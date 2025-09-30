# C# Memory Management, GC, IDisposable, using

## Big picture
- .NET garbage collector reclaims unused managed objects automatically; you focus on object lifetimes.
- Still need to release unmanaged resources (file handles, sockets) via `IDisposable`.
- Minimize allocations in hot paths to reduce GC pressure.

## GC recap
- Managed heap divided into generations (0, 1, 2, LOH). Younger generations collect faster.
- Large objects (> ~85 KB) go to Large Object Heap; prefer pooling to avoid fragmentation.
- `GC.Collect()` is rarely needed; rely on the runtime except during diagnostics.

## IDisposable patterns
```csharp
public class FileLogger : IDisposable
{
    private FileStream? _stream;
    private bool _disposed;

    public FileLogger(string path) => _stream = File.OpenWrite(path);

    public void Log(string message)
    {
        if (_disposed) throw new ObjectDisposedException(nameof(FileLogger));
        using var writer = new StreamWriter(_stream!, leaveOpen: true);
        writer.WriteLine(message);
    }

    public void Dispose()
    {
        if (_disposed) return;
        _stream?.Dispose();
        _disposed = true;
        GC.SuppressFinalize(this);
    }
}
```
- Suppress finalization when disposing manually to skip extra GC work.
- For unmanaged handles, implement a finalizer as a safety net and call `Dispose(false)`.

## `using` and `await using`
- `using var resource = new Resource();` ensures `Dispose()` runs at scope end.
- `await using var connection = await pool.RentAsync();` for async disposables.
- Nest `using` statements or employ `using` declarations to reduce indentation.

## Diagnostics toolkit
- Use `dotnet-counters`, `dotnet-gcdump`, or PerfView to analyze allocations.
- In code, `GC.GetTotalMemory(forceFullCollection: false)` gives snapshot, but avoid in production loops.
- `ArrayPool<T>` and object pooling reduce pressure in tight loops.

## Practice prompts
1. Implement `IDisposable` on a class holding a native handle and add a finalizer.
2. Profile a hot path, identify an allocation source, and redesign to reuse objects.
3. Compare eager disposal (`using`) vs. letting GC reclaim and describe the trade-offs.








## References
- [Garbage collection fundamentals](https://learn.microsoft.com/en-us/dotnet/standard/garbage-collection/fundamentals) - CLR garbage collector primer.
- [Garbage collection and performance](https://learn.microsoft.com/en-us/dotnet/standard/garbage-collection/) - tuning GC and understanding generations.
- [Implementing Dispose](https://learn.microsoft.com/en-us/dotnet/standard/garbage-collection/implementing-dispose) - deterministic cleanup with IDisposable.
- [Large object heap guidance](https://learn.microsoft.com/en-us/dotnet/standard/garbage-collection/large-object-heap) - manage large allocations efficiently.
- [.NET garbage collection deep dive](https://www.youtube.com/watch?v=lohXTO90ScY) - talk from the .NET team on GC internals.
## Key Terms
- **Managed Heap**: Memory area where the CLR allocates objects under GC management.
- **Generation**: Grouping of objects (Gen 0/1/2) used by the GC to optimize collection frequency.
- **Large Object Heap**: Special heap segment for allocations larger than ~85 KB.
- **Garbage Collection**: Automatic process that reclaims memory for objects no longer referenced.
- **Finalizer**: Method (`~Type`) that runs before GC frees an object, usually as a safety net for unmanaged resources.
- **IDisposable**: Interface signaling that a type exposes a deterministic `Dispose` method.
- **GC.SuppressFinalize**: API that tells the runtime a finalizer does not need to run because cleanup already occurred.
- **using Declaration**: C# syntax that disposes a resource when the surrounding scope exits.
- **await using**: Async disposal syntax leveraging `IAsyncDisposable`.
- **Object Pooling**: Technique for reusing objects or arrays to reduce allocations.
- **ArrayPool<T>**: Shared pool of arrays provided by the BCL for allocation-free buffering.
- **dotnet-counters**: Diagnostic tool that monitors GC and runtime metrics in real time.
- **GC Pressure**: Strain on the garbage collector caused by excessive allocations or large objects.

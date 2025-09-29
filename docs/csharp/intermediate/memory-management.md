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

## Word List
- 0
- 1
- 2
- 3
- 85
- a
- add
- allocation
- allocations
- an
- analyze
- and
- arraypool
- as
- async
- at
- automatically
- avoid
- await
- big
- bool
- but
- c
- call
- class
- code
- collect
- collector
- compare
- connection
- counters
- csharp
- declarations
- describe
- diagnostics
- disposables
- disposal
- dispose
- disposed
- disposing
- divided
- dotnet
- during
- eager
- employ
- end
- ensures
- except
- extra
- false
- faster
- file
- filelogger
- filestream
- finalization
- finalizer
- focus
- for
- forcefullcollection
- fragmentation
- garbage
- gc
- gcdump
- generations
- gettotalmemory
- gives
- go
- handle
- handles
- heap
- holding
- hot
- identify
- idisposable
- if
- implement
- in
- indentation
- into
- is
- kb
- large
- leaveopen
- letting
- lifetimes
- log
- loh
- loops
- managed
- management
- manually
- memory
- message
- minimize
- nameof
- native
- need
- needed
- nest
- net
- new
- object
- objectdisposedexception
- objects
- offs
- on
- openwrite
- or
- path
- paths
- patterns
- perfview
- picture
- pool
- pooling
- practice
- prefer
- pressure
- private
- production
- profile
- prompts
- public
- rarely
- recap
- reclaim
- reclaims
- redesign
- reduce
- release
- rely
- rentasync
- resource
- resources
- return
- reuse
- runs
- runtime
- safety
- scope
- skip
- snapshot
- sockets
- source
- statements
- still
- stream
- streamwriter
- string
- suppress
- suppressfinalize
- t
- the
- this
- throw
- tight
- to
- toolkit
- trade
- true
- unmanaged
- unused
- use
- using
- var
- via
- void
- vs
- when
- work
- writeline
- writer
- you
- younger

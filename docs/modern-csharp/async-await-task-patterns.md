# Modern C# Async/Await

## Why Task-Based Asynchrony Matters
- Keep UI responsive while work happens off the main thread.
- Compose independent operations without callback pyramids.
- Handle cancellation, progress, and error handling consistently via `Task` APIs.

## Core Concepts
- `Task` represents ongoing work and carries results or exceptions.
- `async` marks a method that may suspend; it must return `Task`, `Task<T>`, `ValueTask`, or `void` (special cases only).
- `await` yields control to the caller until the awaited task completes, resuming on the captured synchronization context by default.

```csharp
public async Task<string> DownloadTitleAsync(Uri endpoint, HttpClient client, CancellationToken ct)
{
    using var response = await client.GetAsync(endpoint, ct);
    response.EnsureSuccessStatusCode();
    return await response.Content.ReadAsStringAsync(ct);
}
```

## Compose Asynchronous Workflows
- Use `Task.WhenAll` to run independent tasks concurrently.
- Chain continuations with `await` rather than `.ContinueWith` to preserve exceptions and context.
- Expose cancellation tokens on public async APIs; link child tokens with `CancellationTokenSource.CreateLinkedTokenSource`.

```csharp
public async Task<IReadOnlyList<UserDto>> LoadUsersAsync(IEnumerable<int> ids, IUserClient client, CancellationToken ct)
{
    var fetches = ids.Select(id => client.FetchUserAsync(id, ct));
    return await Task.WhenAll(fetches);
}
```

## Error Handling and Diagnostics
- Wrap awaited calls in `try`/`catch` blocks near the caller to preserve stack clarity.
- Observe tasks explicitly (`await` or `TaskScheduler.UnobservedTaskException`) to avoid silent failures.
- Profile with `dotnet-trace`, `EventSource`, or visual tooling (Visual Studio Diagnostic Tools, Rider).

## Unity, `async void`, and UniTask Notes
- In Unity, `async void` is often used for event handlers, but exceptions crash silently; prefer returning `UniTask` or `Task` when possible.
- UniTask provides value-task like structs to reduce allocations on IL2CPP, but mixing with `Task` requires conversion via `ToTask()` or `ToUniTask()`.
- Unity's main thread context is not restored automatically; use `await UniTask.SwitchToMainThread()` when touching scene objects after an `await`.
- Avoid `async void` for gameplay flows; wrap entry points in `async UniTaskVoid` from UniTask or use fire-and-forget helpers that log exceptions.

## Best Practices Checklist
- ✅ Never block on `Task.Result` or `.Wait()` on the main thread; use `await` end-to-end.
- ✅ Prefer `ValueTask`/`UniTask` only for hot paths where measurement shows allocation pressure.
- ✅ Dispose `CancellationTokenSource` instances to release timers.
- ✅ Document threading expectations so callers know when continuations resume on a background thread.

## Further Study
- Stephen Cleary, *Concurrency in C# Cookbook*.
- Unity blog: "Async/Await in Unity" for engine-specific caveats.
- MSDN Docs: `Task`, `ValueTask`, `IAsyncEnumerable` for streaming scenarios.

## Word List
- a
- after
- allocation
- allocations
- an
- and
- apis
- async
- asynchronous
- asynchrony
- automatically
- avoid
- await
- awaited
- background
- based
- best
- block
- blocks
- blog
- but
- by
- c
- callback
- caller
- callers
- calls
- cancellation
- cancellationtoken
- cancellationtokensource
- captured
- carries
- cases
- catch
- caveats
- chain
- checklist
- child
- clarity
- cleary
- client
- completes
- compose
- concepts
- concurrency
- concurrently
- consistently
- content
- context
- continuations
- continuewith
- control
- conversion
- cookbook
- core
- crash
- createlinkedtokensource
- csharp
- ct
- default
- diagnostic
- diagnostics
- dispose
- docs
- document
- dotnet
- downloadtitleasync
- end
- endpoint
- engine
- ensuresuccessstatuscode
- entry
- error
- event
- eventsource
- exceptions
- expectations
- explicitly
- expose
- failures
- fetches
- fetchuserasync
- fire
- flows
- for
- forget
- from
- further
- gameplay
- getasync
- handle
- handlers
- handling
- happens
- helpers
- hot
- httpclient
- iasyncenumerable
- id
- ids
- ienumerable
- il2cpp
- in
- independent
- instances
- int
- ireadonlylist
- is
- it
- iuserclient
- keep
- know
- like
- link
- loadusersasync
- log
- main
- marks
- matters
- may
- measurement
- method
- mixing
- modern
- msdn
- must
- near
- never
- not
- notes
- objects
- observe
- off
- often
- on
- ongoing
- only
- operations
- or
- paths
- points
- possible
- practices
- prefer
- preserve
- pressure
- profile
- progress
- provides
- public
- pyramids
- rather
- readasstringasync
- reduce
- release
- represents
- requires
- response
- responsive
- restored
- result
- results
- resume
- resuming
- return
- returning
- rider
- run
- scenarios
- scene
- select
- shows
- silent
- silently
- so
- special
- specific
- stack
- stephen
- streaming
- string
- structs
- studio
- study
- suspend
- switchtomainthread
- synchronization
- t
- task
- tasks
- taskscheduler
- than
- that
- the
- thread
- threading
- timers
- to
- tokens
- tooling
- tools
- totask
- touching
- tounitask
- trace
- try
- ui
- unitask
- unitaskvoid
- unity
- unity's
- unobservedtaskexception
- until
- uri
- use
- used
- userdto
- using
- value
- valuetask
- var
- via
- visual
- void
- wait
- when
- whenall
- where
- while
- why
- with
- without
- work
- workflows
- wrap
- yields

# C# Delegates, Events, Lambdas, Action/Func

## Core ideas
- Delegates are type-safe function pointers; `Action` and `Func` cover most scenarios.
- Lambdas create inline delegates without verbose method declarations.
- Events wrap delegates to enforce publisher/subscriber semantics and encapsulation.

## Delegate quick syntax
```csharp
public delegate void Notify(string message);

Notify handler = Console.WriteLine;      // method group conversion
handler += msg => Logger.Log(msg);       // lambda + multicast
handler("Ready");
```

## Action / Func guide
- `Action` for `void` return, up to 16 parameters: `Action<int, string>`.
- `Func<TResult>` when returning values: `Func<int, string>` maps `int -> string`.
- `Predicate<T>` is shorthand for `Func<T, bool>`.
- Use `Action`/`Func` over custom delegates unless naming improves clarity.

## Events in practice
```csharp
class Timer
{
    public event EventHandler? Tick;               // EventHandler = (object?, EventArgs)
    protected virtual void OnTick() => Tick?.Invoke(this, EventArgs.Empty);

    public void Start()
    {
        while (true)
        {
            Thread.Sleep(1000);
            OnTick();
        }
    }
}
```
- Only the declaring class can invoke its events; subscribers use `+=`/`-=`.
- Prefer `EventHandler<T>` for custom data payloads.
- Unsubscribe (`-=`) to avoid memory leaks in long-lived publishers.

## Lambda refreshers
- Expression-bodied: `x => x * x`
- Statement-bodied: `x => { var y = x * 2; return y; }`
- Capture variables carefully; closures hold references to variables, not values.

## Practice prompts
1. Create an event-driven `DownloadService` that emits progress updates.
2. Replace `List.ForEach` with LINQ + lambdas for clarity and lazy evaluation.
3. Build a `Retry(Func<bool> action)` helper that retries until success or limit.








## References
- [Delegates programming guide](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/delegates/) - define and invoke delegates.
- [Events programming guide](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/events/) - publisher and subscriber patterns.
- [Lambda expressions reference](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/statements-expressions-operators/lambda-expressions) - syntax and supported scenarios.
- [Implement delegates, events, and lambdas](https://learn.microsoft.com/en-us/training/modules/csharp-implement-delegates-events-lambdas/) - Microsoft Learn module with hands-on labs.
- [Events and delegates in depth](https://www.youtube.com/watch?v=Rd8Kncf5aOo) - detailed video explanation.
## Word List
- 1
- 1000
- 16
- 2
- 3
- a
- action
- an
- and
- are
- avoid
- bodied
- bool
- build
- c
- can
- capture
- carefully
- clarity
- class
- closures
- com
- compared
- console
- conversion
- core
- cover
- create
- csharp
- custom
- data
- declarations
- declaring
- delegate
- delegates
- dotnet
- downloadservice
- driven
- emits
- empty
- en
- encapsulation
- enforce
- evaluation
- event
- eventargs
- eventhandler
- events
- explains
- expression
- for
- foreach
- func
- function
- group
- guide
- handler
- handlers
- helper
- hold
- https
- ideas
- improves
- in
- inline
- int
- invoke
- is
- its
- lambda
- lambdas
- lazy
- leaks
- learn
- limit
- linq
- list
- lived
- log
- logger
- long
- maps
- memory
- message
- method
- microsoft
- most
- msg
- multicast
- naming
- not
- note
- notify
- object
- only
- ontick
- or
- over
- parameters
- patterns
- payloads
- pointers
- practice
- predicate
- prefer
- programming
- progress
- prompts
- protected
- public
- publisher
- publishers
- quick
- ready
- references
- refreshers
- replace
- retries
- retry
- return
- returning
- safe
- scenarios
- semantics
- shorthand
- sleep
- start
- statement
- string
- subscriber
- subscribers
- success
- syntax
- t
- that
- the
- this
- thread
- tick
- timer
- to
- tresult
- true
- type
- unless
- unsubscribe
- until
- up
- updates
- us
- use
- values
- var
- variables
- verbose
- virtual
- void
- when
- while
- with
- without
- wrap
- writeline
- x
- y

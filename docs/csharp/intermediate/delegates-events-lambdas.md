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
- downloadservice
- driven
- emits
- empty
- encapsulation
- enforce
- evaluation
- event
- eventargs
- eventhandler
- events
- expression
- for
- foreach
- func
- function
- group
- guide
- handler
- helper
- hold
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
- most
- msg
- multicast
- naming
- not
- notify
- object
- only
- ontick
- or
- over
- parameters
- payloads
- pointers
- practice
- predicate
- prefer
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

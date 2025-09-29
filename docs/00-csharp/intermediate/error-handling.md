# C# Error Handling: Exceptions, Custom Types, Try/Finally

## Guiding principles
- Throw exceptions for exceptional states; use flow control (return values) for expected outcomes.
- Always preserve the original exception context; wrap only when adding important detail.
- Contain `try` blocks to the minimum statements that may throw.

## Built-in workflow
```csharp
try
{
    Process(order);
}
catch (ValidationException ex)
{
    logger.Warn(ex, "Invalid order");
    return Result.Invalid(ex.Errors);
}
catch (Exception ex)
{
    logger.Error(ex, "Unexpected failure");
    throw; // rethrow preserves stack trace
}
finally
{
    Cleanup();
}
```

## Creating custom exceptions
```csharp
[Serializable]
public class PaymentFailedException : Exception
{
    public string Provider { get; }

    public PaymentFailedException(string provider, string message, Exception? inner = null)
        : base(message, inner) => Provider = provider;

    protected PaymentFailedException(SerializationInfo info, StreamingContext context)
        : base(info, context) => Provider = info.GetString(nameof(Provider))!;

    public override void GetObjectData(SerializationInfo info, StreamingContext context)
    {
        base.GetObjectData(info, context);
        info.AddValue(nameof(Provider), Provider);
    }
}
```
- Inherit from `Exception` or relevant subclass; provide standard constructors.
- Add extra context via properties; keep them immutable.

## Disposal patterns
- Use `try/finally` or `using` to guarantee cleanup.
- `using var stream = File.OpenRead(path);` disposes at scope end (C# 8).
- For async resources, use `await using` with `IAsyncDisposable`.

## Practice prompts
1. Wrap a third-party exception to add a correlation id while preserving the inner exception.
2. Convert a manual `try/finally` resource cleanup into `using` and explain the lifetime.
3. Build a domain-specific exception hierarchy and decide where each one is caught.








## References
- [Exceptions in C#](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/exceptions/) - exception model and terminology.
- [try catch finally reference](https://learn.microsoft.com/en-us/dotnet/csharp/language-reference/keywords/try-catch) - language reference for structured exception handling.
- [Best practices for exceptions](https://learn.microsoft.com/en-us/dotnet/standard/exceptions/best-practices-for-exceptions) - designing a resilient exception strategy.
- [Handle errors and exceptions in C#](https://learn.microsoft.com/en-us/training/modules/csharp-handle-errors-exceptions/) - interactive module on try catch finally.
- [C# 101 exceptions video](https://www.youtube.com/watch?v=y5yDOtXJXKw) - quick video overview from the .NET team.
## Word List
- 1
- 2
- 3
- 8
- a
- add
- adding
- addvalue
- always
- and
- async
- at
- await
- base
- best
- blocks
- build
- built
- c
- catch
- caught
- class
- cleanup
- com
- constructors
- contain
- context
- control
- convert
- correlation
- creating
- csharp
- custom
- decide
- design
- detail
- disposal
- disposes
- domain
- dotnet
- each
- en
- end
- error
- errors
- ex
- exception
- exceptional
- exceptions
- expected
- explain
- extra
- failure
- file
- finally
- flow
- for
- from
- fundamentals
- get
- getobjectdata
- getstring
- guarantee
- guidance
- guiding
- handling
- hierarchy
- https
- iasyncdisposable
- id
- immutable
- important
- in
- info
- inherit
- inner
- into
- invalid
- is
- keep
- learn
- lifetime
- logger
- manual
- may
- message
- microsoft
- minimum
- nameof
- null
- official
- on
- one
- only
- openread
- or
- order
- original
- outcomes
- override
- party
- path
- patterns
- paymentfailedexception
- practice
- practices
- preserve
- preserves
- preserving
- principles
- process
- prompts
- properties
- protected
- provide
- provider
- public
- references
- relevant
- resource
- resources
- result
- rethrow
- return
- scope
- serializable
- serializationinfo
- specific
- stack
- standard
- statements
- states
- stream
- streamingcontext
- string
- subclass
- that
- the
- them
- third
- throw
- tips
- to
- trace
- try
- types
- unexpected
- us
- usage
- use
- using
- validationexception
- values
- var
- via
- void
- warn
- when
- where
- while
- with
- workflow
- wrap

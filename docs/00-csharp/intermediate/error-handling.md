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
## Key Terms
- **Exception**: Runtime signal indicating an unexpected or invalid state.
- **try/catch**: Structured block that isolates risky code and handles specific exceptions.
- **finally**: Block that always executes after try/catch to release resources.
- **Inner Exception**: Original exception preserved when wrapping errors for additional context.
- **Rethrow**: Using `throw;` to propagate the current exception without losing the stack trace.
- **Custom Exception**: Domain-specific exception class deriving from `Exception` with extra metadata.
- **Serialization Constructor**: Protected constructor enabling custom exceptions to be serialized/deserialized.
- **`IDisposable`**: Interface indicating a type owns unmanaged resources and needs deterministic cleanup.
- **using Statement**: Syntax sugar that wraps resource usage in try/finally for disposal.
- **`IAsyncDisposable`**: Async counterpart used with `await using` for asynchronous resource cleanup.
- **Exception Hierarchy**: Structured set of exception types that mirror domain concerns for targeted handling.
- **Correlation ID**: Diagnostic identifier added to exceptions to trace operations across systems.

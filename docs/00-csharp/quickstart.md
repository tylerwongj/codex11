# C# Quickstart Notes

## 1. Language Snapshot
- **Paradigm**: statically typed, OOP-first with functional features (delegates, LINQ).
- **Runtime**: runs on .NET (cross-platform via .NET SDK).
- **Key files**: `.cs` source, `.csproj` project definition, `Program.cs` entry point.

## 2. Core Syntax Cheatsheet
```csharp
// Namespace + class
namespace TodoApp;

public class Program
{
    public static void Main(string[] args)
    {
        Console.WriteLine($"Tasks today: {args.Length}");
    }
}
```

### Built-in Types
| Category | Examples | Notes |
| --- | --- | --- |
| Integral | `int`, `long`, `byte` | default int literals are `int`; suffix `L` for long |
| Floating | `float`, `double`, `decimal` | use `f` or `m` suffix (`3.14f`, `9.99m`) |
| Text | `string`, `char` | strings are immutable |
| Boolean | `bool` | values `true` / `false` |
| Nullable | `int?`, `bool?` | wraps value types to allow null |

### Control Flow
```csharp
if (score >= 10) { level++;
} else if (score > 5) { level += 0.5;
}

for (int i = 0; i < enemies.Count; i++)
{
    enemies[i].Tick();
}

foreach (var enemy in enemies)
{
    enemy.Tick();
}

while (!quest.IsComplete)
{
    quest.Advance();
}
```

## 3. Object-Oriented Essentials
```csharp
public abstract class Character
{
    public string Name { get; }
    protected Character(string name) => Name = name;
    public abstract void Act();
}

public interface IAttack
{
    void Attack(Character target);
}

public class Warrior : Character, IAttack
{
    public Warrior(string name) : base(name) {}

    public override void Act() => Console.WriteLine($"{Name} stands ready.");

    public void Attack(Character target)
        => Console.WriteLine($"{Name} strikes {target.Name}!");
}
```

Class diagram sketch:
```
Character (abstract)
|-- Warrior : Character, IAttack
IAttack (interface)
```

### Records vs Classes
- `record` for immutable, value-like data with built-in equality.
- `class` for entities with identity and mutable state.

## 4. Collections + LINQ
```csharp
var players = new List<string> { "Ava", "Bo", "Cy" };
players.Add("Di");

bool hasBo = players.Contains("Bo");

var scores = new Dictionary<string, int>
{
    ["Ava"] = 12,
    ["Bo"] = 9
};

var topPlayers = scores
    .OrderByDescending(pair => pair.Value)
    .Select(pair => pair.Key)
    .Take(3)
    .ToList();
```

## 5. Error Handling + Pattern Matching
```csharp
try
{
    var content = File.ReadAllText("save.json");
    Console.WriteLine(content);
}
catch (IOException ex)
{
    Console.WriteLine($"Load failed: {ex.Message}");
}

object token = GetToken();

string kind = token switch
{
    int n when n > 0 => "Positive integer",
    string s => $"String of length {s.Length}",
    _ => "Unknown"
};
```

## 6. Async & Tasks
```csharp
public async Task LoadAssetsAsync()
{
    using HttpClient client = new();
    var response = await client.GetAsync("https://example.com/assets");
    string json = await response.Content.ReadAsStringAsync();
    Console.WriteLine(json);
}

await LoadAssetsAsync();
```
Key points:
- Methods that `await` must be marked `async` and return `Task`/`Task<T>` (or `ValueTask`).
- `await` unwraps the result; avoid `.Result` in UI/Unity threads to prevent deadlocks.

## 7. .NET CLI Quick Commands
- `dotnet --list-sdks` — check installed SDKs.
- `dotnet new console -n MyGameTools` — scaffold console app.
- `dotnet run` — build + run in Debug.
- `dotnet test` — run unit tests.
- `dotnet add package Newtonsoft.Json` — add NuGet dependency.

## 8. Micro-Project Roadmap (1–2 Weeks)
**Day 1–2**: Read these notes, set up .NET SDK, run `dotnet new console` and explore `Program.cs`.

**Day 3–4**: Build a text-based quest tracker: parse commands (`start`, `advance`, `status`). Practice loops and switch expressions.

**Day 5–6**: Add classes for `Quest`, `Objective`, explore lists and dictionaries to track state. Add unit tests with xUnit (`dotnet new xunit`).

**Day 7**: Persist data to JSON using `System.Text.Json`. Handle file errors with try/catch.

**Day 8–9**: Introduce async: mock loading quest templates from a local web server; refactor to `async Task` methods.

**Day 10**: Reflect and refactor—apply interfaces, convert `Quest` to an immutable `record`, add LINQ queries to summarize progress.

## 9. Extra Study Pointers
- Official docs: learn.microsoft.com/dotnet/csharp
- Interactive playground: try.dot.net
- Workflow tip: write small C# scripts with `dotnet-script` when testing ideas.








## References
- [Take your first steps with C#](https://learn.microsoft.com/en-us/training/paths/csharp-first-steps/) - hands-on introduction to syntax and tooling.
- [Create a console app with VS Code](https://learn.microsoft.com/en-us/dotnet/core/tutorials/with-visual-studio-code) - step-by-step setup using the dotnet CLI.
- [dotnet new templates catalog](https://learn.microsoft.com/en-us/dotnet/core/tools/dotnet-new) - list of project templates and switches.
- [C# 101 video series](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oW8nviYduHq7bmKode-p8Wy) - short videos from the .NET team.
- [JetBrains Academy C# track](https://www.jetbrains.com/academy/track/dotnet-developer/) - interactive exercises covering language basics.
## Key Terms
- **.NET Runtime**: Execution environment that hosts compiled C# assemblies and provides the base class library.
- **Namespace**: Logical container that groups related types; declared with the `namespace` keyword.
- **Entry Point**: The `Main` method that .NET calls to start a console application.
- **Reference Type**: Objects like classes and strings that live on the managed heap and are passed by reference.
- **Value Type**: Structs and primitives stored inline; may be wrapped in `Nullable<T>` to accept null.
- **Control Flow**: Constructs such as `if`, loops, and `switch` expressions that drive decision logic.
- **Interface**: Contract that defines members a class must implement, enabling polymorphic behavior.
- **Record**: C# type designed for immutable, value-centric models with generated equality.
- **LINQ**: Language Integrated Query API used to transform and filter collections fluently.
- **Pattern Matching**: C# feature that deconstructs or filters values using `switch` expressions and guards.
- **Exception Handling**: Use of `try`/`catch`/`finally` to respond to runtime errors gracefully.
- **Async/Await**: Task-based programming model that keeps code responsive while performing I/O.
- **dotnet CLI**: Command-line interface for scaffolding, building, running, and testing .NET projects.
- **NuGet Package**: Reusable library distributed via `dotnet add package`, often used to extend console tools.
- **JSON Serialization**: Process of converting objects to and from JSON using libraries like `System.Text.Json`.

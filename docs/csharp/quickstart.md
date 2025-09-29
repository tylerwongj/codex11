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

## Word List
- 0
- 1
- 10
- 12
- 14f
- 2
- 3
- 4
- 5
- 6
- 7
- 8
- 9
- 99m
- a
- abstract
- act
- add
- advance
- allow
- an
- and
- app
- apply
- are
- args
- assets
- async
- attack
- ava
- avoid
- await
- base
- based
- be
- bo
- bool
- boolean
- build
- built
- byte
- c
- catch
- category
- char
- character
- cheatsheet
- check
- class
- classes
- cli
- client
- collections
- com
- commands
- console
- contains
- content
- control
- convert
- core
- count
- cross
- cs
- csharp
- csproj
- cy
- data
- day
- deadlocks
- debug
- decimal
- default
- definition
- delegates
- dependency
- di
- diagram
- dictionaries
- dictionary
- docs
- dot
- dotnet
- double
- else
- enemies
- enemy
- entities
- entry
- equality
- error
- errors
- essentials
- ex
- example
- examples
- explore
- expressions
- extra
- f
- failed
- false
- features
- file
- files
- first
- float
- floating
- flow
- for
- foreach
- from
- functional
- get
- getasync
- gettoken
- handle
- handling
- hasbo
- httpclient
- https
- i
- iattack
- ideas
- identity
- if
- immutable
- in
- installed
- int
- integer
- integral
- interactive
- interface
- interfaces
- introduce
- ioexception
- iscomplete
- json
- key
- kind
- l
- language
- learn
- length
- level
- like
- linq
- list
- lists
- literals
- load
- loadassetsasync
- loading
- local
- long
- loops
- m
- main
- marked
- matching
- message
- methods
- micro
- microsoft
- mock
- must
- mutable
- mygametools
- n
- name
- namespace
- net
- new
- newtonsoft
- notes
- nuget
- null
- nullable
- object
- objective
- of
- official
- on
- oop
- or
- orderbydescending
- oriented
- override
- package
- pair
- paradigm
- parse
- pattern
- persist
- platform
- players
- playground
- point
- pointers
- points
- positive
- practice
- prevent
- program
- progress
- project
- protected
- public
- queries
- quest
- quick
- quickstart
- read
- readalltext
- readasstringasync
- ready
- record
- records
- refactor
- reflect
- response
- result
- return
- roadmap
- run
- runs
- runtime
- s
- save
- scaffold
- score
- scores
- script
- scripts
- sdk
- sdks
- select
- server
- set
- sketch
- small
- snapshot
- source
- stands
- start
- state
- static
- statically
- status
- strikes
- string
- strings
- study
- suffix
- summarize
- switch
- syntax
- system
- t
- take
- target
- task
- tasks
- templates
- test
- testing
- tests
- text
- that
- the
- these
- threads
- tick
- tip
- to
- today
- todoapp
- token
- tolist
- topplayers
- track
- tracker
- true
- try
- typed
- types
- ui
- unit
- unity
- unknown
- unwraps
- up
- use
- using
- value
- values
- valuetask
- var
- via
- void
- vs
- warrior
- web
- weeks
- when
- while
- with
- workflow
- wraps
- write
- writeline
- xunit

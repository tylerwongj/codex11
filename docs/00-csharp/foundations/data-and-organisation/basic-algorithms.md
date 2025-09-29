# Basic Algorithms With Built-in APIs

## Searching
- `List<T>.Find`/`FindIndex` grab the first match without a manual loop.
- `FirstOrDefault`, `SingleOrDefault` in LINQ return the element or a default value.
- `BinarySearch` on sorted lists gives O(log n) lookups—remember to sort first.

```csharp
var found = enemies.FirstOrDefault(e => e.HP <= 0);
if (found != null)
{
    HandleDefeat(found);
}
```

## Sorting
- `List<T>.Sort()` sorts in place; pass an `IComparer<T>` or comparison lambda.
- `OrderBy`/`ThenBy` create a sorted copy without mutating the source.
- Use `Array.Sort(keys, items)` to keep parallel arrays in sync.

```csharp
scores.Sort((a, b) => b.Value.CompareTo(a.Value));
var topThree = scores.Take(3).ToList();
```

## Iteration Patterns
- `foreach` is the safest default; it cannot modify the collection but is concise.
- `for` loops offer index access for arrays/lists when you need manual control.
- `Select` + `ToList()` transforms data while encouraging immutability.
- `Aggregate` folds a sequence into a single value; great for totals or string joins.

```csharp
var totalDamage = attacks.Aggregate(0, (sum, hit) => sum + hit.Damage);
```

## When to Drop to Manual Loops
- Profiling shows hot paths with high allocation counts.
- You need early exits that do not fit `First()` or `Any()` cleanly.
- Complex state machines where a `while` loop keeps intent clearer.

Always measure: readability first, micro-optimizations after evidence from profiling tools.








## References
- [LINQ programming guide](https://learn.microsoft.com/en-us/dotnet/csharp/programming-guide/concepts/linq/) - core operators for querying in-memory data.
- [List.Find API reference](https://learn.microsoft.com/en-us/dotnet/api/system.collections.generic.list-1.find) - search helpers on List<T>.
- [Array.Sort documentation](https://learn.microsoft.com/en-us/dotnet/api/system.array.sort) - sorting overloads and comparer usage.
- [Enumerable.Aggregate reference](https://learn.microsoft.com/en-us/dotnet/api/system.linq.enumerable.aggregate) - fold sequences into single values.
- [LINQ crash course](https://www.youtube.com/watch?v=8pTEmbeENF4) - video overview of practical LINQ patterns.
## Word List
- 0
- 3
- a
- access
- after
- aggregate
- algorithm
- algorithms
- allocation
- always
- an
- analysis
- any
- apis
- array
- arrays
- attacks
- b
- basic
- big
- bigocheatsheet
- binarysearch
- built
- but
- c
- cannot
- cheat
- cleanly
- clearer
- collection
- com
- compareto
- comparison
- complex
- complexity
- concise
- constructing
- control
- copy
- counts
- create
- csharp
- damage
- data
- default
- discussed
- do
- drop
- e
- early
- element
- en
- encouraging
- enemies
- evidence
- exits
- find
- findindex
- first
- firstordefault
- fit
- folds
- for
- foreach
- found
- from
- gives
- grab
- great
- handledefeat
- high
- hit
- hot
- hp
- https
- icomparer
- if
- immutability
- implement
- in
- index
- intent
- into
- is
- it
- items
- iteration
- joins
- keep
- keeps
- keys
- lambda
- learn
- linq
- list
- lists
- log
- lookups
- loop
- loops
- machines
- manual
- match
- measure
- micro
- microsoft
- modify
- module
- modules
- mutating
- n
- need
- not
- null
- o
- offer
- on
- optimizations
- or
- orderby
- parallel
- pass
- paths
- patterns
- place
- profiling
- quick
- readability
- reference
- references
- remember
- return
- safest
- scores
- searching
- select
- sequence
- sheet
- shows
- single
- singleordefault
- sort
- sorted
- sorting
- sorts
- source
- state
- string
- sum
- sync
- t
- take
- that
- the
- thenby
- to
- tolist
- tools
- topthree
- totaldamage
- totals
- training
- transforms
- us
- use
- value
- var
- walkthrough
- when
- where
- while
- with
- without
- www
- you

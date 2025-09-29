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

## Word List
- 0
- 3
- a
- access
- after
- aggregate
- algorithms
- allocation
- always
- an
- any
- apis
- array
- arrays
- attacks
- b
- basic
- binarysearch
- built
- but
- cannot
- cleanly
- clearer
- collection
- compareto
- comparison
- complex
- concise
- control
- copy
- counts
- create
- csharp
- damage
- data
- default
- do
- drop
- e
- early
- element
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
- icomparer
- if
- immutability
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
- modify
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
- readability
- remember
- return
- safest
- scores
- searching
- select
- sequence
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
- transforms
- use
- value
- var
- when
- where
- while
- with
- without
- you

# Serialization Basics

## JSON (System.Text.Json)
- Built-in, fast, works well for data transfer and config.
- Opt into camelCase with `JsonSerializerOptions { PropertyNamingPolicy = JsonNamingPolicy.CamelCase }`.
- Use records or DTO classes with get/set properties.

```csharp
var json = JsonSerializer.Serialize(settings, new JsonSerializerOptions
{
    WriteIndented = true
});
var loaded = JsonSerializer.Deserialize<GameSettings>(json);
```

## Unity ScriptableObjects
- Great for authoring data in the editor and sharing across scenes.
- Use for static data (stats, loot tables) rather than per-save mutable state.
- Keep behavior light; ScriptableObjects should mainly hold data and helper methods.

```csharp
[CreateAssetMenu(menuName = "Configs/Weapon")]
public class WeaponConfig : ScriptableObject
{
    public string DisplayName;
    public int Damage;
    public float Cooldown;
}
```

## PlayerPrefs Considerations
- Backed by the registry (Windows) or plist (macOS); best for tiny settings.
- Stores `int`, `float`, `string`; anything else requires manual JSON or binary encoding.
- Call `PlayerPrefs.Save()` after critical writes on desktop builds.
- Do not store secrets—values are easy to edit.

## General Tips
- Version your serialized data: add a `Version` field or migrate on load.
- Handle missing or extra fields gracefully to support forward/backward compatibility.
- Prefer immutable data objects when possible; mutate copies, then overwrite.








## References
- [Serialization in .NET](https://learn.microsoft.com/en-us/dotnet/standard/serialization/) - overview of serialization options.
- [System.Text.Json overview](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/overview) - modern JSON APIs with examples.
- [System.Text.Json common uses](https://learn.microsoft.com/en-us/dotnet/standard/serialization/system-text-json/common-uses) - recipes for everyday serialization tasks.
- [Serialize and deserialize JSON in .NET](https://learn.microsoft.com/en-us/training/modules/serialize-deserialize-json-dotnet/) - interactive module building JSON workflows.
- [Working with JSON in .NET](https://www.youtube.com/watch?v=qlPxmmbgpqQ) - video discussion on serialization strategies.
## Word List
- a
- across
- add
- after
- and
- anything
- apply
- architecture
- are
- authoring
- backed
- backward
- basics
- behavior
- best
- binary
- builds
- built
- by
- call
- camelcase
- class
- classes
- com
- compatibility
- concepts
- config
- configs
- considerations
- cooldown
- copies
- createassetmenu
- critical
- csharp
- damage
- data
- deserialize
- desktop
- displayname
- do
- dotnet
- dto
- easy
- edit
- editor
- else
- en
- encoding
- extra
- fast
- field
- fields
- float
- for
- forward
- gamesettings
- general
- get
- gracefully
- great
- handle
- helper
- hold
- how
- https
- immutable
- in
- inside
- int
- into
- json
- jsonnamingpolicy
- jsonserializer
- jsonserializeroptions
- keep
- learn
- light
- load
- loaded
- loot
- macos
- mainly
- manual
- menuname
- methods
- microsoft
- migrate
- missing
- mutable
- mutate
- net
- new
- not
- objects
- of
- on
- opt
- or
- overview
- overwrite
- per
- playerprefs
- plist
- possible
- prefer
- properties
- propertynamingpolicy
- public
- rather
- records
- references
- registry
- requires
- save
- scenes
- scriptableobject
- scriptableobjects
- secrets
- serialization
- serialize
- serialized
- serializers
- set
- settings
- sharing
- should
- shows
- standard
- state
- static
- stats
- store
- stores
- string
- support
- system
- tables
- text
- than
- the
- then
- these
- tiny
- tips
- to
- transfer
- true
- unity
- us
- use
- values
- var
- version
- weapon
- weaponconfig
- well
- when
- windows
- with
- works
- writeindented
- writes
- your

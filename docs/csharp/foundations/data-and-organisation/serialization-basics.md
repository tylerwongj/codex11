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

## Word List
- a
- across
- add
- after
- and
- anything
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
- compatibility
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
- dto
- easy
- edit
- editor
- else
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
- immutable
- in
- int
- into
- json
- jsonnamingpolicy
- jsonserializer
- jsonserializeroptions
- keep
- light
- load
- loaded
- loot
- macos
- mainly
- manual
- menuname
- methods
- migrate
- missing
- mutable
- mutate
- new
- not
- objects
- on
- opt
- or
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
- set
- settings
- sharing
- should
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
- tiny
- tips
- to
- transfer
- true
- unity
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

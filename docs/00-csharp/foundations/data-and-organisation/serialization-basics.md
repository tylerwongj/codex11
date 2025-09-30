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
## Key Terms
- **Serialization**: Process of converting objects into a format (JSON, binary) for storage or transfer.
- **Deserialization**: Reconstructing objects from serialized data using matching models.
- **DTO**: Data Transfer Object—simple class or record used to serialize structured data.
- **JsonSerializerOptions**: Configuration object controlling casing, formatting, and converters in System.Text.Json.
- **ScriptableObject**: Unity asset type for authoring reusable, inspector-editable data.
- **PlayerPrefs**: Unity key/value store for lightweight settings persisted per user.
- **Version Field**: Marker embedded in serialized payloads to help migrate data between schema changes.
- **Camel Case Policy**: Json naming policy that converts property names to camelCase for compatibility with JavaScript clients.
- **Immutable Data**: Objects whose state cannot change after creation, reducing serialization side-effects.
- **Binary Encoding**: Manual approach for compact storage when JSON is too verbose.
- **Migration**: Logic that upgrades or repairs data when loading older save formats.

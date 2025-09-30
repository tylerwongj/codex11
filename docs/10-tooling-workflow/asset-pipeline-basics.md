# Asset Pipeline Basics (Import Settings, Compression, Platform Overrides)
- **Import settings awareness:** Inspect model, texture, and audio importer tabs. Record default settings and how they influence memory usage, draw calls, and load times.
- **Texture optimization drills:** Compare crunch compression, ASTC, and ETC variations. Profile GPU memory changes across platforms and document the visual trade-offs.
- **Model import discipline:** Standardize scale factors, animation import options (legacy vs. humanoid), and rig configurations. Reimport assets after source FBX updates to avoid stale data.
- **Audio pipeline:** Balance `Load Type` (Decompress on Load, Compressed in Memory, Streaming) and compression formats (Vorbis, ADPCM) for different clip lengths. Validate loop points in the inspector.
- **Platform overrides:** Use `Default`, `Standalone`, `iOS`, and `Android` tabs to tailor settings. Script checks that fail CI when overrides drift from the agreed baseline.
- **Asset validation tools:** Build editor scripts that scan for missing import presets, uncompressed textures, or assets lacking GUID documentation inside `assets/README.md`.

## Import Preset CLI
```bash
unity -batchmode -quit -projectPath . -executeMethod ImportPresetApplier.Apply
```






## References
- [Asset workflow manual](https://docs.unity3d.com/Manual/AssetWorkflow.html) - import settings and reimport triggers.
- [Importing assets manual](https://docs.unity3d.com/Manual/ImportingAssets.html) - supported formats and pipelines.
- [Asset management tutorial](https://learn.unity.com/tutorial/asset-management) - organize and update assets effectively.
- [Optimizing your asset pipeline](https://unity.com/how-to/optimizing-your-asset-pipeline) - article on iteration speed and best practices.
- [Asset pipeline deep dive](https://www.youtube.com/watch?v=b0X0ZkVud9c) - Unite session on pipeline configuration.
## Key Terms
- **Import Preset**: Saved configuration for model, texture, or audio importers that enforces consistent settings across assets.
- **Compression Format**: Encoding option (Crunch, ASTC, Vorbis) that balances memory usage against visual or audio quality.
- **Platform Override**: Importer tab (Standalone, iOS, Android) where platform-specific settings replace project defaults.
- **Load Type**: Audio importer option (Decompress on Load, Compressed in Memory, Streaming) dictating when clips consume RAM vs disk.
- **Reimport**: Process of refreshing assets after source files change to avoid stale data in the project cache.
- **Validation Script**: Editor utility that scans assets for missing presets, oversized textures, or GUID documentation gaps.

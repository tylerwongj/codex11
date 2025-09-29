# Art and Audio Pipeline Essentials

## Timeline
- Week 1: Audit current asset workflows, define naming conventions, and create import presets.
- Week 2: Implement automated checks (texture sizes, missing references) and align with collaborators.
- Week 3: Build audio routing, mixers, and test cues inside a sample scene.
- Ongoing: Schedule weekly syncs to review asset backlog and adjust guidelines.

## Suggested Resources
- Unity Manual sections on import settings, Addressables, and audio mixers.
- 80 Level and Stylized Station workflow articles for art pipeline best practices.
- FMOD or Wwise getting-started tutorials if extending beyond Unity audio.
- GDC talks on art production pipelines and sound design integration.

## Deliverables
- Pipeline handbook outlining naming, folder structure, versioning, and review gates.
- Unity preset library for textures, models, animations, and audio import settings.
- Mixer template with buses, snapshots, and example parameter controls.
- CI scripts or checklists that flag guideline violations before merge.

## Tracking & Reflection
- Maintain an asset intake log with status (requested, in-progress, approved, live).
- Track pipeline-related bugs and resolution time to measure stability.
- Run quarterly pipeline retros with collaborators to surface pain points.
- Archive before/after profiling data to validate pipeline improvements.

## Import Preset Example
```csharp
[CreateAssetMenu(menuName = "Pipeline/TexturePreset")]
public class TextureImportPreset : ScriptableObject
{
    public TextureImporterCompression compression = TextureImporterCompression.Uncompressed;
}
```






## References
- [Unity art pipeline overview](https://docs.unity3d.com/Manual/3D-formats.html) - import formats and workflow tips.
- [Unity audio overview](https://docs.unity3d.com/Manual/Audio.html) - structure of Unity audio systems.
- [Art and asset pipeline tutorial](https://learn.unity.com/tutorial/art-and-asset-pipeline) - course on managing art content.
- [Audio fundamentals tutorial](https://learn.unity.com/tutorial/audio-fundamentals) - hands-on audio setup training.
- [Unity art and audio talks](https://www.youtube.com/playlist?list=PLX2vGYjWbI0R5W0EXUX-uLLq5yRvCN-4c) - Unite sessions on visual and audio pipelines.
## Word List
- 1
- 2
- 3
- 80
- a
- addressables
- adjust
- after
- align
- an
- and
- animations
- approved
- archive
- art
- articles
- asset
- assets
- assetworkflow
- audio
- audiomixer
- audit
- automated
- backlog
- before
- best
- beyond
- bugs
- build
- buses
- checklists
- checks
- ci
- class
- collaborators
- com
- compression
- controls
- conventions
- create
- createassetmenu
- csharp
- cues
- current
- data
- define
- deliverables
- design
- docs
- documentation
- essentials
- example
- extending
- flag
- fmod
- folder
- for
- gates
- gdc
- getting
- guidance
- guideline
- guidelines
- handbook
- html
- https
- if
- implement
- import
- improvements
- in
- inside
- intake
- integration
- level
- library
- live
- log
- maintain
- manual
- measure
- menuname
- merge
- missing
- mixer
- mixers
- models
- naming
- official
- on
- ongoing
- or
- outlining
- pain
- parameter
- pipeline
- pipelines
- points
- practices
- preset
- presets
- production
- profiling
- progress
- public
- quarterly
- references
- reflection
- related
- requested
- resolution
- resources
- retros
- review
- routing
- run
- sample
- scene
- schedule
- scriptableobject
- scripts
- sections
- settings
- sizes
- snapshots
- sound
- stability
- started
- station
- status
- structure
- stylized
- suggested
- surface
- syncs
- talks
- template
- test
- texture
- textureimportercompression
- textureimportpreset
- texturepreset
- textures
- that
- time
- timeline
- to
- track
- tracking
- tutorials
- uncompressed
- unity
- unity3d
- validate
- versioning
- violations
- week
- weekly
- with
- workflow
- workflows
- wwise

# Unity Project Layout, Scenes, Prefabs, and Build Targets
- **Project anatomy:** Understand the role of the `Assets`, `Packages`, `ProjectSettings`, and `Library` folders. Practice navigating them in the editor and in a file explorer.
- **Scenes:** Learn how `.unity` scene files capture object hierarchies. Create a gameplay scene, a UI overlay scene, and experiment with scene-specific lighting settings.
- **Prefabs and prefab variants:** Build reusable GameObjects (e.g., a pickup item). Convert them into prefabs, then create variants to override select properties such as materials or behavior flags.
- **Asset pipelines:** Import common asset types (models, textures, audio). Note how Unity creates meta files and how import settings affect runtime performance.
- **Build targets:** Switch between PC/Mac/Linux and mobile build targets. Record which assets need platform-specific configuration (compression, shader variants, input handling).
- **Hands-on checkpoint:** Organize a demo project with separate folders for art, code, and prefabs. Use a naming convention like `Scenes/Gameplay`, `Prefabs/UI`, and `Scripts/Controllers`.

## Project Tree
```text
Assets/
  Scripts/
  Art/
  Prefabs/
  Scenes/
```






## References
- [Organizing your Unity project](https://learn.unity.com/tutorial/organizing-your-unity-project) - naming conventions and folder structure.
- [Build settings manual](https://docs.unity3d.com/Manual/BuildSettings.html) - configure scenes and build targets.
- [Platform dependencies guide](https://docs.unity3d.com/Manual/PlatformDependencies.html) - settings that vary per platform.
- [Prefab variants manual](https://docs.unity3d.com/Manual/PrefabVariants.html) - share base prefabs across variants.
- [Production-ready project structure](https://unity.com/how-to/set-your-unity-project-up-production) - Unity article on scalable project layouts.
## Key Terms
- **Assets Folder**: Primary location for scenes, scripts, and media that Unity imports into the project.
- **Library Folder**: Unity cache that stores imported artifacts per machine; safe to regenerate but excluded from version control.
- **Prefab Variant**: Prefab derived from a parent prefab that inherits defaults while overriding specific properties.
- **Asset Pipeline**: Import process that converts source files into Unity-ready assets with platform-specific settings.
- **Build Target**: Platform configuration (PC, mobile, console) that controls compression, shaders, and output binaries.

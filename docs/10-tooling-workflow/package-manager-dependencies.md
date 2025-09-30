# Package Manager Usage, Managing Dependencies, Custom Packages
- **Package Manager tour:** Learn how Unity's Package Manager displays embedded, registry, and Git-based packages. Practice adding packages from the Unity Registry and removing unused dependencies.
- **Locking dependencies:** Enable version locking (`manifest.json` with `lock` section) to stabilize reproducible builds. Audit `Packages/packages-lock.json` into source control.
- **Custom package pipeline:** Scaffold a `com.example.tooling` package with its own `package.json`, editor/runtime assemblies, tests, and documentation. Reference it via a local path first, then publish to a scoped registry.
- **Third-party updates:** Create a schedule for reviewing dependency changelogs. Test upgrades in a feature branch and record migration notes under `docs/` before merging.
- **Sandboxing experiments:** Use `Packages/manifest.json` `testables` entries to load experimental packages only in test projects or editor tooling assemblies.
- **Fallback strategy:** Mirror critical packages locally or fork them in case upstream registries fail.

## Manifest Entry
```json
"com.unity.cinemachine": "2.9.7"
```






## References
- [Package Manager UI manual](https://docs.unity3d.com/Manual/upm-ui.html) - manage packages inside the editor.
- [Package dependencies manual](https://docs.unity3d.com/Manual/upm-dependencies.html) - define and resolve dependency graphs.
- [Custom packages manual](https://docs.unity3d.com/Manual/CustomPackages.html) - author and host custom Unity packages.
- [OpenUPM registry](https://openupm.com/) - open-source package registry for Unity.
- [Package manager workflows tutorial](https://learn.unity.com/tutorial/package-manager-workflows) - course on versioning and dependency management.
## Key Terms
- **Unity Package Manager (UPM)**: Tooling that installs, updates, and removes Unity packages from registries, Git, or local folders.
- **`manifest.json`**: Project file listing package dependencies and scoped registries; locking versions here ensures reproducible builds.
- **`packages-lock.json`**: Generated lock file that records exact dependency versions to audit into source control.
- **Custom Package**: Locally authored package with its own `package.json`, assemblies, and tests, often published to a scoped registry.
- **Scoped Registry**: Package registry configuration that routes certain namespaces (e.g., `com.example`) to a private feed.
- **Testables**: Manifest entry enabling experimental or test-only packages for editor extensions without shipping them to production builds.

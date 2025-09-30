# IDE: Visual Studio / Rider Setup, Code Analysis, Unity Integration
- **Environment parity:** Install the Unity Editor integration (Visual Studio Tools for Unity or Rider's Unity plugin). Verify that play mode controls, console mirroring, and shader file support work from the IDE.
- **Solution hygiene:** Regenerate `.sln` and `.csproj` files when packages change. Confirm that assembly definitions map to IDE projects so IntelliSense mirrors runtime boundaries.
- **Debugger fundamentals:** Practice attaching the debugger to a running editor and player build. Use breakpoints, conditional expressions, and watch windows to inspect MonoBehaviour state during gameplay.
- **Code quality tooling:** Enable analyzers (Roslyn, Rider inspections) alongside `dotnet format` or `csharpier` to enforce style. Configure rule severities so critical diagnostics fail builds but guidance-level tips remain informational.
- **Unity-specific productivity:** Explore Rider's Burst inspector, Visual Studio's Event Tracing for profiling, and both IDEs' gutter icons for quick scene navigation. Document hotkeys the team should share.
- **Collaboration tip:** Store IDE settings in version control via `.editorconfig` and shared settings layers so new contributors inherit the same warnings and formatting.

## Editorconfig Sample
```ini
[*.cs]
indent_size = 4
```






## References
- [Scripting tools and IDEs manual](https://docs.unity3d.com/Manual/ScriptingToolsIDEs.html) - official guidance on IDE integration.
- [Visual Studio tools for Unity](https://learn.microsoft.com/en-us/visualstudio/gamedev/unity/get-started/visual-studio-tools-for-unity) - setup guide for Visual Studio integration.
- [JetBrains Rider Unity support](https://www.jetbrains.com/rider/features/unity.html) - IDE features tailored to Unity development.
- [.NET code analysis overview](https://learn.microsoft.com/en-us/dotnet/fundamentals/code-analysis/overview) - enable Roslyn analyzers and inspections.
- [Configure IDEs tutorial](https://learn.unity.com/tutorial/configure-integrated-development-environments) - step-by-step IDE configuration.
## Key Terms
- **IDE Integration**: Setup that links Visual Studio or Rider with Unity for play controls, console mirroring, and asset editing.
- **Solution Hygiene**: Practice of keeping `.sln`/`.csproj` files and assembly definitions in sync so IntelliSense matches runtime assemblies.
- **Debugger Attachment**: Process of connecting the IDE debugger to the Unity editor or player to inspect state via breakpoints and watches.
- **Analyzer**: Roslyn or Rider inspection rule enforcing code style and correctness, often paired with `.editorconfig` severities.
- **`.editorconfig`**: Shared configuration file that standardizes formatting and code analysis rules across team members.
- **Burst Inspector**: IDE tool (Rider) exposing Burst-compiled job information to help profile and optimize performance-critical code.

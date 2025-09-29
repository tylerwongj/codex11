# Custom Inspectors, Editor Scripting, and Tooling Workflows
- **Inspector customization:** Build property drawers and editor windows that reduce repetitive setup. Example: a `ReorderableList` for enemy spawn waves.
- **Editor automation:** Script menu commands for scene validation, linting, or asset migration. Integrate with `AssetPostprocessor` to enforce naming conventions or compression settings.
- **UI Toolkit vs. IMGUI:** Prototype the same tool in both systems to understand retained-mode vs. immediate-mode trade-offs.
- **Testing editor tools:** Add editor integration tests (`UnityEditor.TestTools`) to prevent regressions when Unity upgrades.
- **Versioning:** Package reusable tools into UPM packages (inside `Packages/`) and document install steps in `docs/10-tooling-workflow/`.
- **Exercises:** Create a custom inspector for a data-driven ability system that highlights missing assets and provides quick links to related ScriptableObjects.
- **Reference material:**
  - [Unity Manual: Custom Editors](https://docs.unity3d.com/Manual/editor-CustomEditors.html)
  - [Unity Manual: Extending the Editor](https://docs.unity3d.com/Manual/ExtendingTheEditor.html)
  - [Unity UI Toolkit Documentation](https://docs.unity3d.com/Manual/UIE-getting-started.html)
  - [Unity Test Framework: Editor Tests](https://docs.unity3d.com/Packages/com.unity.test-framework@latest/manual/reference-components-editor-tests.html)
  - [Odin Inspector Blog — Advanced Inspector Workflows](https://odininspector.com/blog)

## Custom Inspector Sample
```csharp
[CustomEditor(typeof(HealthComponent))]
public class HealthComponentEditor : Editor
{
    public override void OnInspectorGUI()
    {
        DrawDefaultInspector();
        if (GUILayout.Button("Debug Heal"))
        {
            ((HealthComponent)target).Heal(10);
        }
    }
}
```






## References
- [Extending the editor manual](https://docs.unity3d.com/Manual/ExtendingTheEditor.html) - entry point for editor scripting.
- [Custom editors manual](https://docs.unity3d.com/Manual/editor-CustomEditors.html) - build bespoke inspector windows.
- [Editor scripting API](https://docs.unity3d.com/ScriptReference/Editor.html) - reference for authoring custom inspectors.
- [Editor scripting tutorial](https://learn.unity.com/tutorial/editor-scripting) - hands-on exercises for editor tooling.
- [Custom inspector tutorial](https://www.youtube.com/watch?v=0uTPkGXAV0Y) - step-by-step custom inspector video.
## Word List
- 10
- a
- ability
- add
- advanced
- and
- asset
- assetpostprocessor
- assets
- automation
- blog
- both
- build
- button
- class
- com
- commands
- components
- compression
- conventions
- create
- csharp
- custom
- customeditor
- customeditors
- customization
- data
- debug
- docs
- document
- documentation
- drawdefaultinspector
- drawers
- driven
- editor
- editors
- enemy
- enforce
- example
- exercises
- extending
- extendingtheeditor
- for
- framework
- getting
- guilayout
- heal
- healthcomponent
- healthcomponenteditor
- highlights
- how
- html
- https
- if
- imgui
- immediate
- in
- inside
- inspector
- inspectors
- install
- integrate
- integration
- into
- latest
- links
- linting
- manual
- material
- menu
- migration
- missing
- mode
- modern
- naming
- odin
- odininspector
- offs
- oninspectorgui
- or
- override
- overview
- package
- packages
- prevent
- property
- prototype
- provides
- public
- quick
- reduce
- reference
- references
- regressions
- related
- reorderablelist
- repetitive
- retained
- reusable
- same
- sample
- scene
- script
- scriptableobjects
- scripting
- settings
- setup
- spawn
- started
- steps
- system
- systems
- target
- test
- testing
- tests
- testtools
- that
- the
- to
- tool
- tooling
- toolkit
- tools
- trade
- typeof
- ui
- uie
- understand
- unity
- unity3d
- unityeditor
- upgrades
- upm
- validation
- versioning
- void
- vs
- waves
- when
- windows
- with
- workflow
- workflows

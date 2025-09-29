# Scene Management (SceneManager, Additive Loading, Persistent Managers)
- **SceneManager API:** Call `SceneManager.LoadScene` and `SceneManager.LoadSceneAsync` to transition scenes. Understand synchronous vs. asynchronous loading trade-offs for UX and hitching.
- **Additive workflows:** Use additive loading to compose levels from smaller chunks. Load a base scene containing global lighting and audio, then add gameplay sections on demand.
- **Persistent managers:** Create a `Bootstrap` scene with systems like audio, input, and save-game managers. Use `DontDestroyOnLoad` judiciously to keep singleton objects alive between scene changes.
- **Scene activation:** Separate loading from activation to pre-load heavy assets. Call `allowSceneActivation = false` during async operations when you want a loading screen.
- **Unloading scenes:** Use `SceneManager.UnloadSceneAsync` to free memory. Confirm that persistent objects do not reference destroyed scene objects to avoid `MissingReferenceException`.
- **Testing checklist:** Script editor tools to launch additive scene sets, and build automated play-mode tests that verify essential managers exist after scene transitions.

## Scene Load Snippet
```csharp
public async UniTask LoadArenaAsync()
{
    await SceneManager.LoadSceneAsync("Arena");
    SceneManager.SetActiveScene(SceneManager.GetSceneByName("Arena"));
}
```






## References
- [Scene management manual](https://docs.unity3d.com/Manual/SceneManagement.html) - conceptual overview of scenes.
- [SceneManager scripting reference](https://docs.unity3d.com/ScriptReference/SceneManagement.SceneManager.html) - API for loading and unloading scenes.
- [Load scenes additively tutorial](https://learn.unity.com/tutorial/load-scenes-additively) - walkthrough for multi-scene workflows.
- [AsyncOperation manual](https://docs.unity3d.com/Manual/AsyncOperation.html) - track progress of asynchronous loads.
- [Scene management video guide](https://www.youtube.com/watch?v=4N3X5dlLyY4) - Brackeys tutorial on loading screens and transitions.
## Word List
- a
- activation
- add
- additive
- after
- alive
- allowsceneactivation
- and
- api
- arena
- assets
- async
- asynchronous
- audio
- automated
- avoid
- await
- base
- best
- between
- bootstrap
- build
- call
- changes
- checklist
- chunks
- com
- compose
- confirm
- containing
- create
- csharp
- demand
- destroyed
- do
- docs
- documentation
- dontdestroyonload
- during
- editing
- editor
- essential
- exist
- false
- for
- free
- from
- game
- gameplay
- getscenebyname
- global
- heavy
- hitching
- html
- https
- input
- judiciously
- keep
- launch
- levels
- lighting
- like
- load
- loadarenaasync
- loading
- loadscene
- loadsceneasync
- management
- managers
- manual
- memory
- missingreferenceexception
- mode
- multi
- multisceneediting
- not
- objects
- offs
- on
- operations
- persistent
- play
- practices
- pre
- public
- reference
- references
- save
- scene
- scenemanagement
- scenemanager
- scenes
- screen
- script
- scripting
- scriptreference
- sections
- separate
- setactivescene
- sets
- singleton
- smaller
- snippet
- synchronous
- systems
- testing
- tests
- that
- then
- to
- tools
- trade
- transition
- transitions
- understand
- unitask
- unity
- unity3d
- unloading
- unloadsceneasync
- use
- ux
- verify
- vs
- want
- when
- with
- workflows
- you

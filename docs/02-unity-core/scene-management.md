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
## Key Terms
- **Scene**: Unity asset containing a hierarchy of GameObjects, lighting, and settings.
- **Additive Load**: Technique that loads multiple scenes simultaneously to compose levels or UI overlays.
- **Persistent Manager**: Bootstrap object kept alive across scenes, often via `DontDestroyOnLoad`, to host shared systems.
- **AsyncOperation**: Unity handle returned by asynchronous loads that exposes progress and activation control.
- **Scene Activation**: Step that makes a loaded scene active, allowing scripts and lighting to take effect.

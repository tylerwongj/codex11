# Addressables, Asset Bundles, and Resource Management
- **Asset labeling:** Learn how Addressables groups, labels, and addressable keys control build content and runtime queries. Practice tagging assets for DLC, platform-specific content, and localized bundles.
- **Loading workflows:** Compare `Addressables.LoadAssetAsync`, `InstantiateAsync`, and preloading via `DownloadDependenciesAsync`. Measure load times with Unity Profiler and note memory spikes.
- **Legacy vs. modern pipelines:** Review when classic AssetBundles or `Resources` are still viable and how to migrate toward Addressables for remote content delivery.
- **Caching strategies:** Configure caching behavior, versioning, and catalog updates. Simulate offline scenarios and confirm graceful fallbacks.
- **Exercises:** Build a content update testbed that swaps character skins at runtime without a full build redeploy. Automate verification by logging bundle sizes and timestamps.
- **Reference material:**
  - [Unity Addressables Manual](https://docs.unity3d.com/Packages/com.unity.addressables@latest/index.html)
  - [Unity Learn: Getting Started with Addressables](https://learn.unity.com/tutorial/getting-started-with-addressables)
  - [Unity Addressables Sample Project](https://github.com/Unity-Technologies/Addressables-Sample)
  - [Unity Blog: Addressables Roadmap Update (2023)](https://blog.unity.com/engine-platform/addressables-roadmap-update-2023)

## Addressables Load Example
```csharp
public async UniTask<GameObject> LoadEnemyAsync(string key)
{
    var handle = Addressables.InstantiateAsync(key);
    await handle.Task;
    return handle.Result;
}
```






## References
- [Addressables manual](https://docs.unity3d.com/Manual/com.unity.addressables.html) - package overview and workflow.
- [Asset bundles introduction](https://docs.unity3d.com/Manual/AssetBundlesIntro.html) - foundations of bundle creation and loading.
- [Addressables getting started tutorial](https://learn.unity.com/tutorial/addressables-getting-started) - step-by-step setup of Addressables.
- [Master Unity Addressables](https://unity.com/how-to/master-unity-addressables) - article on best practices for memory and delivery.
- [Addressables deep dive talk](https://www.youtube.com/watch?v=gvv1VmeT8Yc) - session covering profiles, labels, and hosting.
## Key Terms
- **Addressable**: Asset marked with a key that Addressables can load asynchronously at runtime.
- **Label**: Tag applied to addressable assets to group content for downloads or content packs.
- **AssetBundle**: Legacy container format for packaging assets, often replaced by Addressables.
- **Catalog**: Addressables metadata file that maps keys to asset locations and versions.
- **Content Hosting**: Strategy for storing bundles remotely (CDN, cloud storage) and configuring caching.

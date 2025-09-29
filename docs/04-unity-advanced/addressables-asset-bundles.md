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
## Word List
- 2023
- a
- addressable
- addressables
- and
- are
- asset
- assetbundles
- assets
- async
- at
- automate
- await
- behavior
- blog
- build
- bundle
- bundles
- by
- caching
- catalog
- character
- classic
- com
- compare
- configure
- confirm
- content
- control
- csharp
- delivery
- demonstrating
- dlc
- docs
- documentation
- downloaddependenciesasync
- engine
- example
- exercises
- fallbacks
- for
- full
- gameobject
- getting
- github
- graceful
- groups
- handle
- how
- html
- https
- index
- instantiateasync
- key
- keys
- labeling
- labels
- latest
- learn
- legacy
- load
- loadassetasync
- loadenemyasync
- loading
- localized
- logging
- management
- manual
- material
- measure
- memory
- migrate
- modern
- note
- official
- offline
- or
- package
- packages
- patterns
- pipelines
- platform
- practice
- preloading
- profiler
- project
- public
- queries
- redeploy
- reference
- references
- remote
- resource
- resources
- result
- return
- review
- roadmap
- runtime
- sample
- samples
- scenarios
- simulate
- sizes
- skins
- specific
- spikes
- started
- still
- strategies
- string
- swaps
- tagging
- task
- technologies
- testbed
- that
- times
- timestamps
- to
- toward
- tutorial
- unitask
- unity
- unity3d
- update
- updates
- var
- verification
- versioning
- via
- viable
- vs
- when
- with
- without
- workflows

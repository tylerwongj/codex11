# Continuous Integration, Automated Builds, Crash/Analytics Instrumentation
- **CI pipeline design:** Draft workflows (GitHub Actions, Azure DevOps, Jenkins) that run `make lint`, `make test`, and Unity batch builds on pull requests. Cache library folders and package downloads to keep runtimes fast.
- **Build automation:** Use Unity's command line (`-batchmode -nographics`) with custom build scripts (`BuildPipeline.BuildPlayer`). Script platform-specific output directories and symbol server uploads.
- **Artifact management:** Store player builds, IL2CPP symbols, and addressable catalogs as CI artifacts. Tag builds with commit hashes so QA can reproduce issues quickly.
- **Crash reporting:** Integrate Unity Cloud Diagnostics, Backtrace, or Firebase Crashlytics. Verify that symbols upload automatically so stack traces resolve on dashboards.
- **Analytics instrumentation:** Wrap analytics events in a typed service. Add unit tests that guard against schema drift (missing parameters, renamed events) before shipping releases.
- **Release gates:** Require green CI, crash-free session targets, and analytics health checks before promoting builds from staging to production.

## CI Step Outline
```yaml
- name: Run Lint
  run: make lint
```






## References
- [Command line arguments manual](https://docs.unity3d.com/Manual/CommandLineArguments.html) - options for building projects via CLI.
- [Batch mode manual](https://docs.unity3d.com/Manual/Batchmode.html) - run Unity in headless mode for automation.
- [GameCI getting started](https://game.ci/docs/github/getting-started) - set up Unity builds on GitHub Actions.
- [CI/CD for Unity with Azure Pipelines](https://learn.microsoft.com/en-us/gaming/unity/azure-devops/ci-cd-unity) - tutorial on Azure-based pipelines.
- [Automating Unity builds talk](https://www.youtube.com/watch?v=EVS9st9WME0) - session on CI strategy and tooling.
## Key Terms
- **Continuous Integration (CI)**: Automated workflow that builds, tests, and packages Unity projects on each change.
- **Unity Batchmode**: Command-line flag (`-batchmode -nographics`) that runs Unity headlessly for build automation.
- **Build Artifact**: Packaged output (player build, symbols, addressable catalog) archived by CI for QA and deployment.
- **Crash Reporting Service**: Tool like Unity Cloud Diagnostics or Crashlytics that collects stack traces from player sessions.
- **Analytics Guardrail**: Automated test ensuring event payloads match expected schemas before release.
- **Release Gate**: Policy requiring green CI, crash metrics, or other checks before promoting a build to production.

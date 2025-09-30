# Team Collaboration: Scene/Prefab Merge Strategies, Task Tracking, Code Reviews
- **Source control hygiene:** Standardize Git branching (kebab-case), commit conventions, and LFS usage for large assets. Reinforce locking workflows for binary files when needed.
- **Scene and prefab merges:** Adopt Unity's Smart Merge (YAML merge) and set up `.unity`/`.prefab` reserialization to `Force Text`. Document best practices for subdividing scenes via additive loading and for breaking prefabs into smaller reusable units.
- **Task tracking:** Select a project management tool (Jira, Linear, Notion) and define ticket states. Encourage linking commits and pull requests to tasks for traceability.
- **Code reviews:** Establish checklists covering gameplay correctness, performance, test coverage, and documentation updates. Promote pair programming or mob review sessions for high-risk changes.
- **Cross-discipline workflows:** Schedule regular content syncs between designers, artists, and programmers. Document handoff expectations (e.g., scene validation passes, asset naming) within this collaboration module so expectations stay discoverable.
- **Exercises:** Facilitate a mock merge conflict resolution session on a shared scene and iterate on the documented playbook based on the outcome.
- **Reference material:** Unity Smart Merge documentation; Git best practices; "Collaborating on Scenes" Unite talks.

## Scene Merge Checklist
```text
1. Create a temporary branch
2. Pull teammates' latest scene edits
3. Use Smart Merge on .unity files
4. Resolve lighting or navmesh updates
```






## References
- [Unity version control manual](https://docs.unity.com/version-control/en/manual/overview) - Plastic SCM features and setup.
- [Unity cloud build manual](https://docs.unity3d.com/Manual/UnityCloudBuild.html) - collaborative build automation.
- [Unity DevOps pathway](https://learn.unity.com/pathway/unity-devops) - training on source control and pipelines.
- [Git LFS](https://git-lfs.github.com/) - handle large binary assets in Git repositories.
- [Unity DevOps collaboration talk](https://www.youtube.com/watch?v=71Hj4i7Gr2Y) - panel on workflows and team culture.
## Key Terms
- **Smart Merge**: UnityYAMLMerge configuration that reconciles `.unity` and `.prefab` files so teams can co-edit scenes safely.
- **Force Text Serialization**: Project setting that stores Unity assets as YAML, enabling diffing and merge tooling to work effectively.
- **Git Workflow**: Shared branching and commit conventions that keep history clean and facilitate code reviews.
- **Task Tracker**: Project management system (Jira, Linear, Notion) where tickets capture scope, status, and ownership.
- **Review Checklist**: Agreed criteria—gameplay correctness, performance, tests, documentation—that reviewers verify before merging.
- **Cross-Discipline Sync**: Scheduled touchpoint for designers, artists, and programmers to hand off assets and align on changes.
- **Merge Conflict Drill**: Practice exercise where the team resolves a staged conflict to refine the collaboration playbook.

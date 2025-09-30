# Platform-Specific Considerations

## Timeline
- Pre-Production: Identify target platforms, gather certification checklists, and estimate hardware constraints.
- Mid-Production: Conduct 2-week research spikes per platform to validate build pipelines and device performance.
- Pre-Launch: Execute compliance passes, submission dry runs, and final QA sweeps.
- Post-Launch: Gather telemetry and platform feedback to inform patches.

## Suggested Resources
- Official platform documentation (Apple/Google developer portals, Sony/Microsoft/Nintendo TRC/XR checklists).
- Unity platform-specific manuals (Mobile optimization, Console build guides, XR best practices).
- Oculus, SteamVR, and XR Interaction Toolkit samples for immersive platforms.
- Talks/blogs on console certification, mobile F2P strategies, and XR comfort design.

## Deliverables
- Platform readiness matrix with requirements, owner, status, and target dates.
- Input abstraction layer or wrapper to normalize controls across devices.
- Build pipeline configuration files/scripts for each platform, including CI integration where possible.
- Risk register documenting open compliance gaps, hardware issues, and mitigation plans.

## Tracking & Reflection
- Maintain per-platform dashboards showing certification progress and outstanding blockers.
- Archive submission assets (screenshots, metadata, age ratings) for future updates.
- Record test device inventory and coverage to avoid blind spots.
- Host go/no-go reviews before each submission with action logs afterwards.

## Build Matrix Snippet
```yaml
platforms:
  ios:
    min_version: 16.0
    input: touch
  pc:
    distribution: steam
    input: keyboard_mouse
  vr:
    device: quest2
    fps_target: 72
```






## References
- [Platform development course](https://learn.unity.com/course/platform-development) - Unity Learn course on tailoring builds per platform.
- [Platform-specific manual](https://docs.unity3d.com/Manual/PlatformSpecific.html) - documentation for platform differences.
- [Mobile optimization guide](https://docs.unity3d.com/Manual/MobileOptimizationPracticalGuide.html) - official recommendations for mobile targets.
- [Console certification talk](https://www.youtube.com/watch?v=G9mYVWeN_Gs) - GDC session on console submission insights.
- [Unity XR documentation](https://docs.unity3d.com/XR/Manual/index.html) - VR and AR platform requirements and workflows.
## Key Terms
- **Certification Checklist**: Official platform requirements you must satisfy before submission.
- **Platform Readiness Matrix**: Tracking table showing requirements, owners, status, and target dates.
- **Input Abstraction Layer**: Wrapper that maps platform-specific inputs to engine-agnostic actions.
- **Risk Register**: Document listing compliance gaps, hardware issues, and mitigation plans.
- **Submission Assets**: Screenshots, metadata, age ratings, and other materials required for store submission.
- **Go/No-Go Review**: Formal meeting to assess readiness before submitting or shipping on a platform.

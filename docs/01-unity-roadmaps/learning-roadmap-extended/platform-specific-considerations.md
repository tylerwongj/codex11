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
## Word List
- 0
- 1026973
- 16
- 2
- 2020
- 72
- abstraction
- across
- action
- afterwards
- age
- and
- apple
- archive
- assets
- avoid
- before
- best
- blind
- blockers
- blogs
- build
- certification
- checklists
- ci
- com
- comfort
- compliance
- conduct
- configuration
- considerations
- console
- constraints
- controls
- coverage
- dashboards
- dates
- deliverables
- deployment
- design
- details
- developer
- device
- devices
- discussion
- distribution
- docs
- documentation
- documenting
- dry
- each
- estimate
- execute
- expectations
- f2p
- feedback
- files
- final
- for
- fps
- future
- gaps
- gather
- gdc
- gdcvault
- getting
- go
- google
- guides
- hardware
- host
- html
- https
- identify
- immersive
- including
- inform
- input
- integration
- interaction
- inventory
- ios
- issues
- keyboard
- launch
- layer
- logs
- maintain
- manual
- manuals
- matrix
- metadata
- microsoft
- mid
- min
- mitigation
- mobile
- mouse
- nintendo
- no
- normalize
- oculus
- of
- official
- on
- open
- optimization
- or
- outstanding
- owner
- panel
- passes
- patches
- pc
- per
- performance
- pipeline
- pipelines
- plans
- platform
- platforms
- platformspecific
- play
- portals
- possible
- post
- practices
- pre
- production
- progress
- qa
- quest2
- ratings
- readiness
- record
- references
- reflection
- register
- requirements
- research
- resources
- reviews
- risk
- runs
- samples
- screenshots
- scripts
- showing
- snippet
- sony
- specific
- spikes
- spots
- status
- steam
- steamvr
- strategies
- submission
- suggested
- sweeps
- talks
- target
- telemetry
- test
- timeline
- to
- toolkit
- touch
- tracking
- trc
- unity
- unity3d
- updates
- validate
- version
- vr
- week
- where
- with
- wrapper
- www
- xr
- yaml
- your

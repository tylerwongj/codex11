# Animation Workflows

## Key Concepts
- Animator Controllers define states and transitions; parameters (bool, float, trigger) gate movement.
- Blend trees interpolate between clips based on parameters for smooth locomotion.
- Animation events notify gameplay scripts at specific frames.
- State machine behaviors encapsulate logic tied to animation states.
- Humanoid vs generic rigs require different import settings and retargeting workflows.

## Practice Checklist
- Create an idle-walk-run blend tree controlled by character velocity.
- Use animation layers and masks for upper-body aiming while legs run.
- Trigger attack combos with animation events calling gameplay scripts.
- Profile Animator performance using the Animation window and Timeline profiler module.







## References
- [Animation system overview](https://docs.unity3d.com/Manual/AnimationOverview.html) - conceptual guide to Unity animation.
- [Animator Controller manual](https://docs.unity3d.com/Manual/AnimatorControllers.html) - configure states, transitions, and parameters.
- [Blend Trees manual](https://docs.unity3d.com/Manual/BlendTrees.html) - set up blend trees for smooth transitions.
- [Animator and Timeline tutorial](https://learn.unity.com/tutorial/animator-and-timeline) - connect animation with timeline workflows.
- [Animation rigging deep dive](https://www.youtube.com/watch?v=7fF8xl8r4qM) - session on advanced rigging and workflows.
## Key Terms
- **Animator Controller**: Asset that defines animation states, transitions, and parameters.
- **Blend Tree**: Graph that blends multiple animation clips based on parameter values to produce smooth motion.
- **Animation Event**: Frame-level callback that invokes game logic during an animation clip.
- **State Machine Behaviour**: Script attached to Animator states to run custom logic on enter, update, or exit.
- **Humanoid vs Generic Rig**: Import modes determining whether animations retarget between characters or remain model-specific.

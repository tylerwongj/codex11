# Audio Fundamentals

## Key Concepts
- AudioSources play clips, support spatialization, Doppler effects, and 3D attenuation.
- AudioListeners (usually one per scene) capture audio for the player; position matters in 3D mixes.
- Audio Mixer groups enable volume control, effects, and snapshot transitions.
- Use Audio Mixers for ducking (sidechain) and dynamic music layers.
- AudioClip import settings affect memory usage and streaming behavior.

## Practice Checklist
- Configure spatial audio for footsteps and ambient loops with distance-based attenuation.
- Build an audio mixer with SFX, music, and dialogue groups plus snapshot transitions.
- Implement runtime volume sliders adjusting exposed mixer parameters.
- Trigger adaptive music layers in response to gameplay states (combat, exploration).







## References
- [Audio overview manual](https://docs.unity3d.com/Manual/Audio.html) - structure of Unity audio systems.
- [Audio Mixer manual](https://docs.unity3d.com/Manual/AudioMixer.html) - mixing, routing, and effects.
- [Spatial audio manual](https://docs.unity3d.com/Manual/AudioSpatializer.html) - set up spatialization plugins.
- [Audio fundamentals tutorial](https://learn.unity.com/tutorial/audio-fundamentals) - hands-on exercises for audio setup.
- [Unity audio workflow tips](https://www.youtube.com/watch?v=snz1BIwz1Ys) - talk covering practical audio pipelines.
## Key Terms
- **AudioSource**: Component that plays AudioClips with support for 2D or 3D spatialization.
- **AudioListener**: Scene component that receives audio mixdown—typically attached to the player camera.
- **Audio Mixer**: Routing asset that groups sounds, applies effects, and exposes parameters for runtime control.
- **Snapshot**: Stored mixer state that crossfades volumes/effects for transitions like ducking.
- **Spatialization**: Technique that positions audio in 3D space using attenuation, pan, and HRTF plugins.

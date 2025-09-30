# Input Systems

## Key Concepts
- Legacy Input Manager reads axes and buttons by string name at runtime. It is simple but inflexible.
- The new Input System package uses action maps, control schemes, and devices for better abstraction.
- Input actions can trigger callbacks (performed, canceled) and support rebinding at runtime.
- PlayerInput and InputActionAsset centralize configuration and decouple logic from hardware.

## Practice Checklist
- Configure horizontal and jump actions in both legacy and new systems, then compare code complexity.
- Swap between keyboard/mouse and gamepad profiles using control schemes without changing gameplay code.
- Implement UI navigation bindings and mobile touch controls via the new Input System.
- Profile input latency and device detection across desktop and mobile builds.







## References
- [Input System package docs](https://docs.unity3d.com/Packages/com.unity.inputsystem@latest) - documentation for the new Input System.
- [New Input System course](https://learn.unity.com/course/new-input-system) - guided training on action maps and bindings.
- [Input Manager reference](https://docs.unity3d.com/Manual/class-InputManager.html) - legacy input configuration guide.
- [UI input module manual](https://docs.unity3d.com/Manual/UISystem-Input.html) - connect input to UI components.
- [Input System overview talk](https://www.youtube.com/watch?v=0XxsvK23z7Q) - official presentation on modern input workflows.
## Key Terms
- **Legacy Input Manager**: Older Unity system that reads axes and buttons defined in Project Settings.
- **Input System Package**: Modern event-driven input framework that uses action maps and control schemes.
- **Action Map**: Collection of input actions grouped by gameplay context (e.g., gameplay, UI).
- **Control Scheme**: Device-specific binding set that lets you swap between keyboard, gamepad, or touch.
- **PlayerInput**: Component that wires an input actions asset to scripts and handles device switching.

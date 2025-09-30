# User Interface Architecture

## Key Concepts
- Unity UI (uGUI) uses `Canvas` for rendering; choose Screen Space vs World Space based on use case.
- `RectTransform` anchors define responsive layout; pivots affect scaling and rotation.
- EventSystem mediates UI input; components like `Button` and `Toggle` respond to events.
- UI Toolkit introduces retained-mode UI with USS stylesheets and UXML assets.
- UI Toolkit runtime supports data binding and editor tooling; learn both for future-proofing.

## Practice Checklist
- Prototype HUD elements with Unity UI, paying attention to anchors for multiple aspect ratios.
- Build an in-game menu using UI Toolkit, binding controls to a scriptable state model.
- Implement hover, click, and drag events using event interfaces or UI Toolkit callbacks.
- Profile UI batching and canvas rebuild costs in the Frame Debugger.







## References
- [UI system manual](https://docs.unity3d.com/Manual/UISystem.html) - Unity UI (UGUI) fundamentals.
- [UI Toolkit manual](https://docs.unity3d.com/Manual/UIElements.html) - modern retained-mode UI workflow.
- [UI best practices](https://docs.unity3d.com/Manual/UIBestPractices.html) - tips for performance and layout.
- [UI Toolkit essentials tutorial](https://learn.unity.com/tutorial/ui-toolkit-essentials) - build runtime UI with UI Toolkit.
- [UI Toolkit for runtime talk](https://www.youtube.com/watch?v=Xl1Xm9XGaY0) - presentation on shipping UI Toolkit UI.
## Key Terms
- **Canvas**: Root component that renders Unity UI (uGUI) elements in screen or world space.
- **RectTransform**: Transform subtype with anchors and pivots used for responsive UI layout.
- **EventSystem**: Manager that routes input events to UI components like Button and Toggle.
- **UI Toolkit**: Retained-mode UI framework using UXML markup and USS stylesheets.
- **USS/UXML**: Style and markup files that define layout and styling for UI Toolkit interfaces.

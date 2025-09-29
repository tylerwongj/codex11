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
## Word List
- a
- affect
- an
- anchors
- and
- architecture
- aspect
- assets
- attention
- based
- batching
- binding
- both
- build
- button
- callbacks
- canvas
- case
- checklist
- choose
- classic
- click
- com
- components
- concepts
- controls
- costs
- data
- debugger
- define
- docs
- documentation
- drag
- editor
- elements
- event
- events
- eventsystem
- for
- frame
- future
- game
- hover
- html
- https
- hud
- implement
- in
- input
- interface
- interfaces
- introduces
- key
- layout
- learn
- like
- manual
- mediates
- menu
- mode
- model
- multiple
- on
- or
- paying
- pivots
- practice
- profile
- proofing
- prototype
- ratios
- rebuild
- recttransform
- reference
- references
- rendering
- respond
- responsive
- retained
- rotation
- runtime
- scaling
- screen
- scriptable
- space
- state
- stylesheets
- supports
- system
- the
- to
- toggle
- tooling
- toolkit
- ugui
- ui
- uisystem
- uitoolkit
- unity
- unity3d
- use
- user
- uses
- using
- uss
- uxml
- vs
- with
- world

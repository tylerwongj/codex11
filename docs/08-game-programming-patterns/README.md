# Game Programming Patterns Study Guide

Use these focused modules to explore architectural patterns for gameplay systems. Review the prerequisites, then work through each topic with weekly sprints or study sessions.

- [Entity-Component Principles](entity-component-principles.md)
- [Behavioral Patterns Toolkit](behavioral-patterns-toolkit.md)
- [Messaging Strategies](messaging-strategies.md)
- [Data-Oriented Design and ECS](data-oriented-design-ecs.md)
- [Scene Architecture and Systems Design](scene-architecture-systems-design.md)

Document experiments and reflections as you progress so the insights feed back into your project architecture.

## Practice Checklist
- [ ] Components remain data-driven; behavior is composed through discrete scripts or systems.
- [ ] State machines are testable via unit tests and do not hardcode Unity callbacks.
- [ ] Messaging solution matches team needs (editor tooling, performance, debuggability).
- [ ] ECS systems operate on contiguous data and schedule jobs without race conditions.
- [ ] Scene flow avoids monolithic managers; responsibilities are documented per system.

## Further Reading and Resources
- Robert Nystrom, *Game Programming Patterns* (free online edition).
- Unity Manual: ScriptableObject-based architecture patterns.
- Ryan Hipple, "Game Architecture with ScriptableObjects" (GDC 2017).
- Unity DOTS Samples repository for practical ECS implementations.
- Sander van Rossen, "Data-Oriented Design" talk for fundamentals on cache-friendly layouts.

## Reflection Prompts
- Where does composition break down, and how can data-driven authoring restore flexibility?
- What criteria determine whether you centralize a system or decouple via events/messages?
- How does DOTS change your approach to debugging compared to MonoBehaviour-centric workflows?
- Which architectural decisions need documenting for future contributors, and where should they live?

## Pattern Index
```bash
ls docs/08-game-programming-patterns
```






## References
- [Game Programming Patterns book](https://gameprogrammingpatterns.com/) - free online reference for classic patterns.
- [Design patterns in Unity](https://learn.unity.com/tutorial/design-patterns-in-unity) - Unity Learn course applying GoF patterns.
- [Unity architecture talks](https://www.youtube.com/playlist?list=PLX2vGYjWbI0Rv_0E8xmPKzW0fvkYl9t7P) - collection of Unity architecture sessions.
- [Refactoring.Guru patterns catalog](https://refactoring.guru/design-patterns) - visual explanations of common patterns.
- [Data oriented design book](https://www.dataorienteddesign.com/dodmain/dodmain.html) - Mike Acton on data oriented mindset.
## Word List
- 08
- 2017
- a
- and
- approach
- architectural
- architecture
- architectures
- are
- as
- authoring
- avoids
- back
- based
- bash
- behavior
- behavioral
- book
- break
- cache
- callbacks
- can
- centralize
- centric
- change
- checklist
- com
- compared
- component
- components
- composed
- composition
- conditions
- contiguous
- contributors
- criteria
- data
- debuggability
- debugging
- decisions
- decouple
- decoupled
- design
- determine
- discrete
- do
- docs
- document
- documented
- documenting
- does
- dots
- down
- driven
- each
- ecs
- edition
- editor
- entity
- events
- experiments
- explore
- feed
- flexibility
- flow
- focused
- for
- free
- friendly
- fundamentals
- further
- future
- game
- gameplay
- gameprogrammingpatterns
- gdc
- guide
- hardcode
- hipple
- how
- https
- implementations
- index
- insights
- inspired
- into
- is
- jobs
- kk
- layouts
- live
- ls
- machines
- managers
- manual
- matches
- md
- messages
- messaging
- modules
- monobehaviour
- monolithic
- need
- needs
- not
- nystrom
- on
- online
- operate
- or
- oriented
- pattern
- patterns
- per
- performance
- practical
- practice
- prerequisites
- presentation
- principles
- programming
- progress
- project
- prompts
- race
- raq3ihhe
- reading
- reference
- references
- reflection
- reflections
- remain
- repository
- resources
- responsibilities
- restore
- review
- robert
- rossen
- ryan
- samples
- sander
- scene
- schedule
- scriptableobject
- scriptableobjects
- scripts
- sessions
- should
- so
- solution
- sprints
- state
- strategies
- study
- system
- systems
- talk
- team
- testable
- tests
- that
- the
- then
- these
- they
- through
- to
- tooling
- toolkit
- topic
- unit
- unite
- unity
- use
- v
- van
- via
- watch
- weekly
- what
- where
- whether
- which
- with
- without
- work
- workflows
- www
- you
- your
- youtube

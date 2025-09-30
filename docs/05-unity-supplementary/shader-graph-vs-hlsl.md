# Basic Shader Knowledge: Shader Graph vs. Hand-Written, URP vs. HDRP
- **Rendering pipelines overview:** Compare the Built-in Render Pipeline with Universal (URP) and High Definition (HDRP) pipelines. Track how lighting models, post-processing, and feature availability change per pipeline and document project-specific recommendations alongside these notes.
- **Shader Graph workflow:** Build a simple stylized material using Shader Graph. Explore subgraphs, keywords, and Custom Function nodes. Profile iteration speed improvements when artists do not rely on engineer-built shaders.
- **Hand-written shaders:** Port the Shader Graph material to an HLSL-based shader (`.shader` or `.hlsl`). Explain when hand-authored shaders are necessary (e.g., complex lighting models, dynamic branching, platform-specific optimizations) and note common pitfalls such as variant explosion.
- **URP vs. HDRP selection criteria:** Evaluate rendering requirements (target hardware, realism goals, feature needs like volumetric lighting or ray tracing). Build a table contrasting URP and HDRP for your project and capture migration considerations.
- **Exercises:** Implement the same water or foliage effect in Shader Graph and hand-written HLSL, profile on target devices, and summarize trade-offs.
- **Reference material:** Unity Manual — Render Pipelines; Unity Learn Shader Graph tutorials; Catlike Coding shader series for HLSL deep dives.

## Shader Graph Flow
```text
Texture Sample -> Normal Strength -> PBR Master
```






## References
- [Shader Graph manual](https://docs.unity3d.com/Manual/shader-graph.html) - node-based shader authoring workflow.
- [Writing shaders manual](https://docs.unity3d.com/Manual/SL-ShaderPrograms.html) - HLSL-based programmable pipeline.
- [Shader Graph course](https://learn.unity.com/course/shader-graph) - Unity Learn course covering Shader Graph fundamentals.
- [Choose between Shader Graph and HLSL](https://unity.com/how-to/choose-between-shader-graph-and-hlsl) - article comparing authoring approaches.
- [Shader Graph tips session](https://www.youtube.com/watch?v=Xkgzj540HZ4) - advanced Shader Graph workflows video.
## Key Terms
- **Render Pipeline**: Set of shaders and systems (Built-in, URP, HDRP) that control lighting models, post-processing, and hardware targets.
- **Shader Graph**: Visual authoring environment that lets you assemble shaders via nodes, subgraphs, and keywords without writing HLSL.
- **Hand-Written Shader**: Custom `.shader` or `.hlsl` file that grants full control over lighting equations, branching, and platform tuning.
- **Custom Function Node**: Shader Graph node that injects snippets of HLSL so you can mix visual authoring with bespoke code.
- **Shader Variant**: Compiled permutation created from keywords or multi_compile directives; excessive variants can slow builds and increase memory.
- **Profiling Pass**: Measurement of shader cost on target hardware to compare Shader Graph and HLSL implementations for the same effect.

# Repository Guidelines

## Project Structure & Module Organization
All learning material lives in `docs/`, organized by topic (e.g., `csharp/`, `unity-core/`, `game-programming-patterns/`). Each folder holds focused Markdown files plus a local `README.md` that orients new readers. Roadmaps sit under `docs/unity-roadmaps/` and meta guidance under `docs/meta/`. When adding a new subject, mirror this pattern: a directory named after the topic in kebab-case with overview and deep-dive notes. Place large reference media in `assets/` and cite sources inside an `assets/README.md` entry.

## Build, Test, and Development Commands
This repo is documentation-only, so there is no build pipeline yet. Before opening a pull request, run a Markdown style pass such as `npx markdownlint-cli "docs/**/*.md"` (or your preferred formatter) to catch heading and spacing issues. If you introduce scripts or samples later, document the exact command in the relevant folder’s README.

## Writing Style & Naming Conventions
Use Markdown headings sequentially (`#`, `##`, `###`) and wrap prose near 100 characters. Favor concise, instructional language; lead with definitions or checklists, then add curated resources. Files should be lowercase kebab-case (e.g., `vector-math-fundamentals.md`). Keep examples in fenced code blocks with language hints, and prefer ASCII unless quoting APIs that require symbols. When documenting workflows, include explicit command snippets and paths.

## Content Review & Quality Checks
Cross-link related articles so readers can navigate between topics. For new sections, include a short synopsis, learning outcomes, and at least one actionable exercise or reference. Peer reviewers should verify technical accuracy, spelling, and link health. Record follow-up ideas in the associated directory’s README so they are easy to triage later.

## Commit & Pull Request Guidelines
Craft commits using `type(scope): summary` (e.g., `docs(unity-gameplay): expand physics notes`). Each pull request should explain the motivation, list major sections touched, and attach previews or screenshots when formatting changes are involved. Reference supporting resources or issue IDs, note any outstanding TODOs, and request at least one review before merging.

## Research & Attribution
Quote external sources sparingly and attribute them inline with links. If you copy significant excerpts or diagrams, confirm the license permits reuse, store originals in `assets/`, and include credit details. Add a short rationale for recommended resources so future readers know why they matter.

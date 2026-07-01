---
name: xhs-andy-ai-video
description: Create silent Xiaohongshu-style short videos in HyperFrames from reference images, a topic, and a fixed duration. Use when Codex needs to turn visual references into a 9:16 opinion video, card-based motion graphic, or minimalist social clip without voiceover or TTS.
---

# XHS Andy AI Video

## Overview

Use this skill to convert a few reference images and a topic into a silent HyperFrames short video. Follow the same production path each time: extract the visual system, define the narrative beats, write the design spec, build the HyperFrames project, and render a review/final export.

## Workflow

1. Inspect the provided reference images before making visual decisions.
2. Lock the video constraints early:
   - theme/topic
   - duration
   - aspect ratio, usually `9:16`
   - delivery mode: silent video only
3. Extract the repeatable visual language from references:
   - background treatment
   - card structure
   - typography scale
   - emphasis color
   - motion tone
4. Write a short design spec in `docs/superpowers/specs/`.
5. Write an implementation plan in `docs/superpowers/plans/`.
6. Build one HyperFrames project directory per video.
7. Render at least:
   - one draft/review export
   - one final export
8. Validate with `hyperframes lint`, `validate`, and `inspect` before calling it complete.

## Trigger Examples

Use this skill for requests like:

- "Use these references to make a 9:16 AI opinion short video."
- "Turn these Xiaohongshu-style references into a silent HyperFrames short."
- "Create a 45-second HyperFrames video from these references, with no voiceover."
- "Build a white-background minimalist tech card animation around this topic."

## Project Outputs

For each video task, produce these artifacts:

- a design spec markdown file
- an implementation plan markdown file
- a HyperFrames project folder
- an `index.html` composition entry file
- a `DESIGN.md` file inside the HyperFrames project
- a script file for on-screen copy
- a review render
- a final render

## Naming Rules

- Name the HyperFrames project folder after the topic in concise kebab-case.
- Name the design spec as `YYYY-MM-DD-<topic>-video-design.md`.
- Name the implementation plan as `YYYY-MM-DD-<topic>-video.md`.
- Name the on-screen script file as `script_<topic>.md` or `script_<topic>.txt`.
- Keep render outputs under `renders/` and separate review vs final files clearly.

## Visual Rules

Use the references as the style anchor instead of inventing a fresh aesthetic.

- Prefer white or very light backgrounds when the references are clean editorial cards.
- Keep the structure centered and card-based when the references use isolated content blocks.
- Use one emphasis family only, usually blue or cyan, for keywords and micro-accents.
- Keep typography bold and high-contrast.
- Keep motion intentional and restrained. The visual rhythm should feel sharp, not decorative.
- Do not add voiceover, TTS, karaoke captions, or audio-reactive behavior unless the user explicitly asks for them outside this skill.

## Build Rules

- Prefer one self-contained `index.html` unless the timeline becomes hard to maintain.
- If scenes become dense, split coherent scene groups into sub-compositions.
- Match scene count to runtime. For a `45s` short video, `5-7` scenes is the normal range.
- Build around on-screen text and motion graphics, not spoken pacing.
- Keep copy concise enough to be readable without pausing.

## Validation

Run these commands from the workspace root:

```powershell
cmd /c npx hyperframes lint .\your-project
cmd /c npx hyperframes validate .\your-project
cmd /c npx hyperframes inspect .\your-project --samples 10
cmd /c npx hyperframes render .\your-project --quality draft --fps 30 --output .\your-project\renders\review.mp4
cmd /c npx hyperframes render .\your-project --quality high --fps 30 --output .\your-project\renders\final.mp4
```

On Windows, prefer `cmd /c npx ...` to avoid PowerShell execution-policy issues.

## Common Failures

- If the video feels like slides instead of a short video, the scene rhythm is too flat. Tighten the scene beats and strengthen transitions.
- If text becomes unreadable, reduce copy density before shrinking fonts aggressively.
- If the style drifts away from the references, rewrite `DESIGN.md` first instead of patching colors ad hoc.
- If the timeline becomes hard to reason about, split scenes into sub-compositions instead of adding more overlap in one file.
- If `npx` fails in PowerShell, rerun through `cmd /c npx ...`.

## References

Read [references/workflow.md](./references/workflow.md) before implementation. It contains the concrete deliverable structure, scene design method, and command checklist for this workflow.

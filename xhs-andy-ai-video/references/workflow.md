# Workflow

## Purpose

Turn a set of visual references plus a topic into a silent HyperFrames short video that feels native to Xiaohongshu-style commentary content.

## Inputs

- 1-6 reference images
- one clear topic
- target duration
- target aspect ratio
- optional tone, such as sharp, calm, or editorial

## Standard Flow

1. Read the reference images and describe the recurring visual traits.
2. Convert those traits into a minimal visual identity:
   - canvas color
   - main card style
   - typography hierarchy
   - accent color
   - motion character
3. Convert the topic into `5-7` scene beats.
4. Write a short design spec under `docs/superpowers/specs/`.
5. Write a matching implementation plan under `docs/superpowers/plans/`.
6. Create a HyperFrames project folder named after the topic.
7. Add:
   - `index.html`
   - `DESIGN.md`
   - a text script file for scene copy
   - `renders/`
8. Implement the full video in HyperFrames.
9. Run lint, validate, inspect.
10. Render draft and final outputs.

## Recommended Scene Shape

For a `45s` silent short video:

- scene 1: hook
- scene 2: pain point
- scene 3: key judgment
- scene 4: practical framing
- scene 5: team or system view
- scene 6: closing statement

Keep each scene focused on one idea only.

## Scene Template

Use this structure when drafting scene copy:

```text
Scene 1
- role: hook
- headline: one sharp statement
- support: one short clarifier

Scene 2
- role: pain point
- headline: what people are doing wrong
- support: what that behavior leads to

Scene 3
- role: judgment
- headline: the core argument
- support: one sentence of explanation
```

Repeat the same pattern for the remaining scenes. Keep the hierarchy stable across the full video.

## Copy Rules

- Write for reading speed, not speaking speed.
- Prefer short lines and high-information phrases.
- Highlight only the few words that change the meaning.
- Do not overload one scene with more than one headline and one support block unless the layout clearly supports it.

## Copy Template

Use this as a starting frame:

```text
Headline:
Support:
Highlight words:
Do not say:
```

`Do not say` is useful for removing weak wording, filler, and duplicated phrasing before layout begins.

## Motion Rules

- Build the final layout first, then animate entrances.
- Use transitions between scenes; avoid jump cuts.
- Keep motion crisp and directional.
- Avoid excessive decorative particles, noisy gradients, or unrelated UI chrome.

## Directory Pattern

```text
<project-name>/
  index.html
  DESIGN.md
  script_<topic>.md
  renders/
```

## Deliverable Checklist

- references were read before visual decisions
- duration and ratio were fixed before scene writing
- `DESIGN.md` exists and matches the references
- scene script exists and matches the final layout
- review render exists
- final render exists
- lint ran
- validate ran
- inspect ran or intentional overflow was justified

## Render Commands

```powershell
cmd /c npx hyperframes lint .\project-dir
cmd /c npx hyperframes validate .\project-dir
cmd /c npx hyperframes inspect .\project-dir --samples 10
cmd /c npx hyperframes render .\project-dir --quality draft --fps 30 --output .\project-dir\renders\review.mp4
cmd /c npx hyperframes render .\project-dir --quality high --fps 30 --output .\project-dir\renders\final.mp4
```

## Out of Scope

This skill does not cover:

- TTS
- voiceover timing
- subtitle-to-audio sync
- background music design
- dubbing workflows

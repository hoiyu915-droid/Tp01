# TP01 Prompt Module

version: 1.0.0
status: active
core_workflow: Tp01.md
repository: hoiyu915-droid/Tp01
branch: main
derived_from: TP01 run refinement on 2026-06-30
purpose: Store editable extraction prompts for AnchorA / AnchorB / AnchorC without changing TP01 core workflow.

---

## 0. Module Purpose

This file stores TP01 generation prompts and prompt-governance rules.

Use this file when generating AnchorA / AnchorB / AnchorC after runtime files exist.

Do not put stop-point governance here. Stop points belong to `Tp01.md`.

This module answers:

```text
How should each anchor be prompted so it stays inside its role?
```

Core workflow answers:

```text
When should TP01 read, stop, validate, generate, package, or fail?
```

---

## 1. Global Prompt Rules

These rules apply to all A / B / C prompts unless explicitly overridden.

### Global principles

```text
Extract function, not finished artwork.
Copy structure, not identity.
Copy visual logic, not brand.
Produce reusable anchor material, not a final poster.
Prefer portrait / vertical output unless overridden.
Use current source input, not old packages or canonical baseline content.
```

### Global negative rules

```text
Do not create a finished infographic unless the anchor role explicitly requires it.
Do not create a full story scene unless the anchor role explicitly requires it.
Do not recreate the source photo directly.
Do not crop the source photo and call it an anchor.
Do not add long readable text unless explicitly requested.
Do not add branded identity or copied source text.
Do not silently merge layout, style, and object roles.
Do not copy prompt examples as final anchor content.
```

### Anchor role summary

```text
AnchorA answers: how is the source arranged?
AnchorB answers: how does the source feel visually?
AnchorC answers: what components can be recombined?
```

### Role lock

```text
AnchorA must not become a poster.
AnchorB must not become a moodboard.
AnchorC must not become a scene.
```

---

## 2. AnchorA Prompt

### Role

Spatial skeleton only.

### Core instruction

```text
Generate TP01 AnchorA: layout grammar only.

This anchor must extract spatial skeleton, viewpoint, depth layers, dominant axes, major nodes, negative space, repetition, structural rhythm, and reading/viewing flow from the current source input.

It must answer:
how is the source arranged?
```

### Must capture

```text
- frame ratio
- viewpoint
- primary structure
- depth layers
- dominant axes
- major nodes
- negative space map
- reading flow
- repetition or rhythm
- structural relationships
```

### Must avoid

```text
- no finished poster
- no readable explanatory text
- no numbered caption panels
- no complete object inventory
- no material moodboard
- no full source-photo recreation
- no detailed topic narrative
- no style-guide behavior
- no brand or identity copying
```

### Output behavior

```text
Use simplified lines, blocks, arrows, node markers, construction lines, and spatial placeholders only.

Use pale paper background, low-saturation structure marks, fine linework, and quiet spacing.

It may look like a spatial construction sketch or layout skeleton.
It must not look like a finished explanation graphic.
```

### Short reinforcement

```text
AnchorA must remain a reusable spatial skeleton, not a complete communication graphic.
```

### Strict regeneration prompt for failed A

Use when AnchorA drifts into an annotated infographic, poster, photo recreation, or mixed A/B/C board.

```text
Regenerate TP01 AnchorA only.

Create a portrait spatial skeleton extracted from the current source input.

This is NOT an infographic.
This is NOT a poster.
This is NOT an annotated source-photo board.
This is NOT a material or object sheet.

Use only abstract spatial grammar:
- construction lines
- viewpoint frame
- depth layers
- dominant axes
- node markers
- negative-space blocks
- flow arrows
- simplified structure placeholders

No readable text.
No headings.
No labels.
No numbers.
No captions.
No source photo crop.
No full scene illustration.
No material swatches.
No object inventory.

The output must answer only: how is the source arranged?
```

---

## 3. AnchorB Prompt

### Role

Visual feeling only.

### Core instruction

```text
Generate TP01 AnchorB: style DNA only.

This anchor must extract material language, palette family, lighting mood, line quality, edge behavior, surface texture, contrast profile, and overall visual tone from the current source input.

It must answer:
how does the source feel visually?
```

### Must capture

```text
- material impression
- texture language
- palette family
- light and shadow mood
- line or edge quality
- contrast profile
- surface character
- overall atmosphere
```

### Must avoid

```text
- do not create a moodboard
- do not create a design guide
- do not create an infographic
- do not create sectioned panels with headings
- do not create labels, numbers, captions, or explanatory text
- do not create a layout skeleton
- do not create an object inventory
- do not reconstruct the full room scene
- do not turn into a brand manual
- do not become a style-guide poster
```

### Output behavior

```text
Create abstract visual samples only.

Preferred mental model:
a silent texture laboratory

Preferred content:
- close-up material fragments
- abstract texture studies
- light and shadow swatches
- color swatches
- line and edge samples
- soft atmosphere fragments

No explanatory structure is needed.
The visual samples should quietly communicate the style DNA without text.
```

### Strong control sentence

```text
AnchorB must answer “how does this source feel visually?” not “what objects are in it?” and not “how is the scene arranged?”
```

### Short reinforcement

```text
AnchorB must remain a style DNA anchor, not a moodboard, not a poster, not a scene.
```

### Strict regeneration prompt for failed B

Use when AnchorB drifts into a moodboard, design guide, style manual, sectioned poster, or full scene reconstruction.

```text
Regenerate TP01 AnchorB only.

Create style DNA only from the current source input.

This is NOT a moodboard.
This is NOT a design guide.
This is NOT an infographic.
This is NOT a poster.
This is NOT a brand manual.

Create a portrait sheet with only abstract visual samples:
- material fragments
- surface textures
- color swatches
- warm/cool light samples
- shadow softness
- edge behavior studies
- small atmosphere washes

No headings.
No labels.
No numbers.
No captions.
No Chinese text.
No English text.
No section boxes.
No full room scene.
No object inventory.
No layout skeleton.
No explanatory design system.

Use soft Japanese hand-drawn texture, low saturation, fine linework, watercolor wash, pale paper background, quiet spacing.

The output should feel like a silent texture laboratory, not a finished reference board.
```

---

## 4. AnchorC Prompt

### Role

Reusable object vocabulary only.

### Core instruction

```text
Generate TP01 AnchorC: asset / object vocabulary only.

This anchor must extract reusable objects, connection logic, variants, props, scene elements, and modular components from the current source input.

It must answer:
what components can be recombined?
```

### Must capture

```text
- primary objects
- secondary objects
- connectors or relationships
- reusable components
- gesture or pose vocabulary
- scene elements
- micro details
- modular variants
```

### Must avoid

```text
- no full page composition
- no fixed story scene
- no full hierarchy poster
- no complete conclusion
- no layout-guide behavior
- no style-guide behavior
- no large unified scene reconstruction
- no identity-specific copied objects by default
```

### Output behavior

```text
Create an asset sheet / object vocabulary sheet.
Objects should be separated, modular, and recombinable.

Use isolated components, variants, small connection studies, and reusable fragments.
The sheet may contain tiny context hints, but no large complete scene.
```

### Strong control sentence

```text
No complete scene vignette larger than 20% of the canvas.
Every item must remain reusable and separable.
```

### Short reinforcement

```text
AnchorC must remain an asset vocabulary sheet, not a finished scene.
```

### Strict regeneration prompt for failed C

Use when AnchorC drifts into a scene, concept art, narrative image, poster, or full composition.

```text
Regenerate TP01 AnchorC only.

Create reusable object vocabulary only from the current source input.

This is NOT a finished scene.
This is NOT concept art.
This is NOT a poster.
This is NOT a layout guide.
This is NOT a moodboard.

Create a portrait asset sheet with separated, recombinable components:
- primary object variants
- secondary object variants
- connector studies
- relationship fragments
- small reusable scene elements
- micro details

No complete scene vignette larger than 20% of the canvas.
Every component must be visually separable.
Every item should be reusable in a new composition.

No full story.
No final environment reconstruction.
No fixed composition.
No explanatory long text.
No brand copying.
```

---

## 5. Stricter Regeneration Rules

Use these when an anchor drifts.

### If AnchorA fails

Common drift:

```text
- became infographic
- included long text
- included source-photo realism
- merged B or C content
- became annotated poster
```

Repair rule:

```text
- reduce to skeleton only
- strip all readable text
- strip material emphasis
- strip object listing
- preserve only spatial grammar
```

### If AnchorB fails

Common drift:

```text
- became moodboard
- became design guide
- became poster with headings
- reconstructed full room
- added numbered sections or captions
```

Repair rule:

```text
- remove all headings, labels, captions
- remove section boxes
- remove full scene reconstruction
- retain only abstract samples
- use “silent texture laboratory” framing
```

### If AnchorC fails

Common drift:

```text
- became a scene
- became too compositional
- became too narrative
- merged layout or style explanation
- made one large environment vignette
```

Repair rule:

```text
- separate objects
- reduce vignette size
- keep modular variants
- retain connection logic only
- remove narrative completion
```

---

## 6. Optional Split Mode for AnchorB

Use this only when B keeps drifting.

Rule:

```text
If AnchorB repeatedly turns into a moodboard, split B into B1–B4 instead of refining one big B.
```

### B1 — Material DNA only

```text
Generate TP01 AnchorB1: Material DNA only.

This is NOT a moodboard, NOT a design guide, NOT an infographic, NOT a poster.

Create a portrait sheet with only 8 abstract material samples on pale paper:
- rough twisted natural rope fiber
- frayed rope edge
- matte black metal surface
- black metal edge highlight
- warm wood grain
- soft amber light reflection
- warm shadow wash
- tiny muted accent sample when present in source

No headings.
No labels.
No numbers.
No captions.
No Chinese text.
No English text.
No section boxes.
No full room scene.
No object inventory.
No layout skeleton.
No explanatory design system.

Use soft Japanese hand-drawn texture, low saturation, fine linework, watercolor wash, quiet spacing.

The output should feel like a silent texture laboratory, not a finished reference board.
```

### B2 — Palette / Light DNA only

```text
Generate TP01 AnchorB2: Palette and Lighting DNA only.

Create a portrait visual language sheet showing only the color and light system extracted from the current source image.

Use soft watercolor swatches, light gradients, shadow softness, warm/cool balance, glow samples, and tiny accent color samples.

No full composition.
No material inventory.
No object vocabulary.
No readable labels.
No headings.
No captions.
No photo recreation.
No moodboard layout.
```

### B3 — Line / Edge DNA only

```text
Generate TP01 AnchorB3: Line and Edge DNA only.

Create a portrait reference sheet of abstract line behavior from the current source image.

Show irregular organic lines, soft frayed edges, rigid straight edges, smooth surface lines, soft light edges, and edge contrast studies.

No full scene.
No object sheet.
No color palette board.
No readable text.
No final poster.
No design guide.
```

### B4 — Mood / Atmosphere DNA only

```text
Generate TP01 AnchorB4: Mood and Atmosphere DNA only.

Create a portrait atmospheric reference sheet expressing only the source mood category.

Use abstract mood vignettes, soft washes, blurred light spots, tonal fields, and minimal structural hints.

No full room reconstruction.
No object inventory.
No layout skeleton.
No readable text.
No moodboard headings.
No explanatory panels.
```

---

## 7. Source-Specific Prompt Template

When a new user source image is provided, fill this template before generation.

```md
# TP01 Current Source Prompt Fill

source_refs:
- REF_01:

source_summary:

AnchorA source-specific focus:
- arrangement:
- viewpoint:
- depth:
- axes:
- rhythm:

AnchorB source-specific focus:
- material:
- palette:
- light:
- edge:
- atmosphere:

AnchorC source-specific focus:
- primary objects:
- secondary objects:
- connectors:
- reusable variants:
- micro details:
```

This fill should be derived from current source input, not memory.

---

## 8. Successful 2026-06-30 Extraction Lessons

These are prompt lessons extracted from the 2026-06-30 rope-divider TP01 run.

### AnchorA lesson

```text
A first failed when it became an annotated infographic with the source photo and too much readable explanation.
A passed when regenerated as a spatial construction sketch with nodes, axes, depth, negative space, and flow only.
```

Reusable rule:

```text
AnchorA = spatial skeleton only.
It answers: how is the source arranged?
A must not become a poster.
```

### AnchorB lesson

```text
B repeatedly failed when prompted as moodboard / style DNA sheet / design guide.
Those words triggered a full design-manual layout with headings, captions, panels, and explanation.
B passed when reframed as abstract visual samples / silent texture laboratory.
```

Reusable rule:

```text
AnchorB = visual feeling only.
It answers: how does the source feel visually?
B must not become a moodboard.
Do not create a design guide.
Create only abstract visual samples.
Preferred framing: silent texture laboratory.
```

### AnchorC lesson

```text
C passed when it separated ropes, knots, posts, panels, lights, connectors, and small variants into a reusable asset sheet.
C still needs a vignette-size constraint to avoid drifting into complete scene reconstruction.
```

Reusable rule:

```text
AnchorC = reusable object vocabulary only.
It answers: what components can be recombined?
C must not become a scene.
No complete scene vignette larger than 20% of the canvas.
Every item must remain reusable and separable.
```

---

## 9. Prompt Editing Rule

When future prompt refinement is needed:

```text
Edit this file first.
Do not edit Tp01.md unless stop points, runtime contract, source routing, or package governance changes.
```

This keeps TP01 stable while allowing extraction behavior to improve.

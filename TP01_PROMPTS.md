# TP01 Prompt Module

version: 1.1.0
status: active
core_workflow: Tp01.md
repository: hoiyu915-droid/Tp01
branch: main
derived_from: TP01 run refinement on 2026-06-30 plus staged-generation / compiler / audit upgrade
purpose: Store editable extraction prompts, prompt compiler rules, anti-anchor controls, audit scorecards, parameter ranges, and downstream staged usage rules for AnchorA / AnchorB / AnchorC without changing TP01 core workflow.

---

## 0. Module Purpose

This file stores TP01 generation prompts and prompt-governance rules.

Use this file when generating AnchorA / AnchorB / AnchorC after runtime files exist.

Do not put source-routing or stop-point governance here. Stop points belong to `Tp01.md`.

This module answers:

```text
How should each anchor be prompted, compiled, constrained, audited, and reused so it stays inside its role?
```

Core workflow answers:

```text
When should TP01 read, stop, validate, generate, package, or fail?
```

Important split:

```text
Tp01.md = stable operating protocol
TP01_PROMPTS.md = editable prompt / compiler / audit module
```

When prompt behavior needs refinement, update this file first. Do not rewrite core workflow unless the protocol itself changes.

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
Generate complete files directly; do not output patch-only files.
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

## 2. TP01 Prompt Compiler Contract

The compiler is a deterministic transformation from runtime markdown into a model-ready generation prompt.

It exists because manual runtime-to-prompt translation is a high-variance failure point.

### Compiler input

```text
AnchorA.runtime.md
AnchorB.runtime.md
AnchorC.runtime.md
TP01_PROMPTS.md
current source reference(s)
```

### Compiler output

For each anchor, produce one complete model-ready prompt in this order:

```text
1. TARGET ANCHOR
2. ROLE LOCK
3. SOURCE-DERIVED POSITIVE FEATURES
4. ALLOWED VISUAL LANGUAGE
5. PARAMETER RANGES / TOLERANCES
6. HARD NEGATIVES / ANTI-ANCHOR BLOCK
7. OUTPUT FORMAT
8. FAIL CONDITIONS
```

### Compiler schema

```md
# TP01_COMPILED_PROMPT

target_anchor:
source_refs:
role_lock:
primary_question:
source_derived_positive_features:
allowed_visual_language:
parameter_ranges:
hard_negatives:
output_format:
fail_conditions:
```

### Compiler hard rules

```text
Never compile all A/B/C roles into one anchor prompt.
Never allow AnchorA prompt to include material mood or object inventory.
Never allow AnchorB prompt to include layout skeleton or object catalog.
Never allow AnchorC prompt to include page hierarchy, style guide behavior, or a complete scene.
Always inject the corresponding ANTI_ANCHOR block.
Always include explicit fail conditions.
Always compile from current runtime, not from memory.
```

### Bad compiler behavior

```text
Manual freewriting from runtime.
Adding attractive design language not present in runtime.
Using generic words that trigger drift, such as moodboard, brand manual, design guide, infographic, poster, cinematic scene, concept art.
Combining positive role instructions with weak avoid lists only.
```

### Good compiler behavior

```text
Role first.
Source-derived positives second.
Allowed form third.
Hard negatives fourth.
Fail conditions last.
Short, strict, and role-specific.
```

---

## 3. AnchorA Prompt

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
- reading / viewing flow
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
Use simplified lines, blocks, arrows, node markers, construction lines, perspective scaffolds, and spatial placeholders only.

Use pale paper background, low-saturation structure marks, fine linework, quiet spacing, and abstract construction grammar.

It may look like a spatial construction sketch or layout skeleton.
It must not look like a finished explanation graphic.
```

### ANTI_ANCHOR_A

Inject this hard negative block into every compiled AnchorA prompt.

```text
ANTI_ANCHOR_A:
- no title
- no headings
- no captions
- no labels
- no numbered explanation nodes
- no legend panel
- no explanatory sidebars
- no finished infographic
- no poster layout
- no design guide
- no material swatches
- no color palette row
- no object inventory
- no close-up object studies
- no full source-photo recreation
- no realistic scene rendering
- no brand identity copying
```

### AnchorA parameter ranges

Use only when source evidence supports them.

```yaml
frame_ratio: source-derived; default portrait if source is portrait
viewpoint_tilt: source-derived; allow approximate tolerance, not fixed imitation
major_node_count: 2-6 unless source requires more
primary_axis_count: 2-5
negative_space_ratio: 15-45% depending on source density
depth_layer_count: 3-5 when depth is visible
text_amount: 0 readable words
object_detail_level: low; placeholders only
```

### Strict regeneration prompt for failed A

Use when AnchorA drifts into an annotated infographic, poster, photo recreation, or mixed A/B/C board.

```text
Regenerate TP01 AnchorA only.

Create a portrait spatial skeleton extracted from the current source input.

This is NOT an infographic.
This is NOT a poster.
This is NOT an annotated source-photo board.
This is NOT a material sheet.
This is NOT an object sheet.

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
No legend.
No source photo crop.
No full scene illustration.
No material swatches.
No object inventory.

The output must answer only: how is the source arranged?
```

---

## 4. AnchorB Prompt

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
- abstract material fragments
- surface texture traces
- light and shadow washes
- edge behavior studies
- atmospheric marks
- small color temperature hints

No explanatory structure is needed.
The visual samples should quietly communicate the style DNA without text.
```

### Strong control sentence

```text
AnchorB must answer “how does this source feel visually?” not “what objects are in it?” and not “how is the scene arranged?”
```

### ANTI_ANCHOR_B

Inject this hard negative block into every compiled AnchorB prompt.

```text
ANTI_ANCHOR_B:
- no moodboard
- no grid moodboard
- no design guide
- no brand manual
- no material board
- no color palette row
- no labeled swatches
- no section boxes
- no headings
- no captions
- no numbers
- no readable Chinese text
- no readable English text
- no full room reconstruction
- no object catalog
- no separated object sheet
- no layout skeleton
- no diagram arrows
- no infographic behavior
- no poster behavior
```

### AnchorB parameter ranges

Use only when source evidence supports them.

```yaml
text_amount: 0 readable words
section_box_count: 0
palette_accent_ratio: 0-10% for tiny accent colors
object_recognition_level: low to medium; fragments allowed, catalog forbidden
texture_density: source-derived; usually medium-high for tactile sources
shadow_softness: low / medium / high, selected from source
contrast_profile: source-derived; describe as a range, not a single value
full_scene_area: 0%; no reconstructed room / complete environment
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
This is NOT a material catalog.

Create a portrait sheet with only abstract visual samples:
- material fragments
- surface textures
- warm/cool light samples
- shadow softness
- edge behavior studies
- small atmosphere washes
- muted accent color hints only when present in source

No headings.
No labels.
No numbers.
No captions.
No Chinese text.
No English text.
No section boxes.
No color palette row.
No full room scene.
No object inventory.
No layout skeleton.
No explanatory design system.

Use soft hand-drawn texture, low saturation, fine linework, watercolor wash, pale paper background, quiet spacing.

The output should feel like a silent texture laboratory, not a finished reference board.
```

---

## 5. AnchorC Prompt

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

### ANTI_ANCHOR_C

Inject this hard negative block into every compiled AnchorC prompt.

```text
ANTI_ANCHOR_C:
- no full scene
- no final composition
- no large environment reconstruction
- no story illustration
- no concept art scene
- no poster
- no layout guide
- no style guide
- no moodboard
- no page hierarchy
- no long explanatory text
- no complete room view
- no single unified vignette larger than 20% of canvas
- no fixed conclusion
- no brand copying
```

### AnchorC parameter ranges

Use only when source evidence supports them.

```yaml
component_count: 8-32 depending on source complexity
primary_object_variants: 3-12
secondary_object_variants: 3-12
connector_studies: 2-8 when relationships are visible
micro_detail_count: 3-12
scene_vignette_max_size: <20% canvas
component_separation_margin: visible whitespace between items
text_amount: 0-5 minimal tokens only if essential; prefer 0
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

## 6. Post-Generation Audit Engine

After each anchor image is generated, run this audit before accepting the image.

This is semi-quantitative, not fake precision.

### Audit score convention

```text
0 = absent / failed
1 = weak
2 = acceptable
3 = strong
```

### Hard gate rule

```text
If any hard gate fails, the anchor fails regardless of score.
If hard gates pass, score the soft criteria.
Recommended pass threshold: at least 9 / 12 on soft criteria.
```

### AnchorA audit

Hard gates:

```text
[ ] no readable headings / captions / labels
[ ] no finished poster / infographic behavior
[ ] no source-photo crop or full realistic recreation
[ ] no object inventory or material sheet behavior
[ ] visibly derived from current source spatial structure
```

Soft score:

```yaml
layout_only: 0-3
source_spatial_match: 0-3
abstraction_cleanliness: 0-3
separation_from_BC: 0-3
```

Fail examples:

```text
Annotated explanation board.
Beautiful architectural poster.
Source image redrawn too literally.
Bottom legend / labeled diagram dominates the page.
```

### AnchorB audit

Hard gates:

```text
[ ] no moodboard / grid board / material board
[ ] no headings / captions / labels / readable text
[ ] no full room reconstruction
[ ] no object catalog or asset sheet behavior
[ ] no layout skeleton or diagram behavior
[ ] visibly derived from current source visual feeling
```

Soft score:

```yaml
material_DNA: 0-3
palette_light_DNA: 0-3
atmosphere_DNA: 0-3
separation_from_AC: 0-3
```

Fail examples:

```text
Interior-design moodboard.
Color palette strip with material photos.
Sectioned design guide.
Room scene with atmosphere slapped on top.
```

### AnchorC audit

Hard gates:

```text
[ ] components are visually separated
[ ] no complete scene vignette larger than 20% of canvas
[ ] no final story / environment reconstruction
[ ] no layout guide or style guide behavior
[ ] visibly derived from current source objects / connectors
```

Soft score:

```yaml
asset_separation: 0-3
source_asset_coverage: 0-3
connector_logic: 0-3
component_reusability: 0-3
```

Fail examples:

```text
One large scene with decorative objects.
Concept art.
Narrative poster.
A layout board pretending to be an asset sheet.
```

### Audit output format

```md
# TP01 Anchor Audit

anchor:
hard_gates:
soft_scores:
total_score:
verdict: PASS / PASS_WITH_WARNING / FAIL
failure_reason:
regeneration_instruction:
```

---

## 7. Parameterized Range Policy

Parameterized ranges are used to control consistency without freezing the source into a rigid template.

### Range rules

```text
Ranges must be source-derived.
Ranges must describe tolerated variation, not arbitrary style wishes.
Ranges must not override anchor role separation.
Ranges should be recorded in runtime files and compiled prompts when useful.
```

### Useful range types

```yaml
layout:
  major_node_count:
  axis_count:
  depth_layer_count:
  negative_space_ratio:
  dominant_sweep_angle:

style:
  texture_density:
  shadow_softness:
  contrast_strength:
  palette_accent_ratio:
  edge_fuzziness:

asset:
  component_count:
  primary_variant_count:
  connector_study_count:
  vignette_max_size:
  separation_margin:
```

### Bad range use

```text
Fake precision such as knot fidelity = 87%.
Ranges invented without source evidence.
Ranges used to smuggle style into A or layout into B.
Ranges so tight that generation becomes brittle.
```

---

## 8. Downstream Multi-Pass Generation Mode

This mode is for using a completed TP01 Anchor Package to generate a final image.

It is not the same as TP01 anchor extraction.

### When to use

```text
Use after AnchorA / AnchorB / AnchorC have passed Stop Point 2.
Use when the user asks to generate a finished image, card, poster, scene, or design based on the anchor package.
```

### Rule

```text
Do not feed A/B/C into the final generation as one undifferentiated prompt unless the user explicitly asks for quick mode.
Use staged generation instead.
```

### Pass sequence

```text
Pass 0 — Target brief
Define final output goal, audience, format, and non-negotiables.

Pass 1 — Layout lock
Use AnchorA only.
Generate or describe the final composition skeleton.
No style enrichment.
No object detailing beyond placeholders.

Pass 2 — Style application
Use AnchorB only while preserving Pass 1 layout.
Apply palette, texture, line quality, contrast, and light mood.
Do not move the layout skeleton.
Do not add new major objects.

Pass 3 — Asset injection
Use AnchorC only while preserving Pass 1 layout and Pass 2 style.
Replace placeholders with components, props, connectors, gestures, or object details.
Do not create a new layout.
Do not overwrite style DNA.

Pass 4 — Final audit
Check final image against A/B/C separately.
```

### Downstream audit

```yaml
layout_preservation_from_A: 0-3
style_preservation_from_B: 0-3
asset_use_from_C: 0-3
role_contamination_control: 0-3
```

Hard fail:

```text
Layout changed after Pass 2 or Pass 3.
Style changed when injecting assets.
Assets created a new scene that ignores AnchorA.
Final output collapses into generic pretty image.
```

---

## 9. Stricter Regeneration Rules

Use these when an anchor drifts.

### If AnchorA fails

Common drift:

```text
- became infographic
- included long text
- included source-photo realism
- merged B or C content
- became annotated poster
- included legend panels or explanatory sidebars
```

Repair rule:

```text
- reduce to skeleton only
- strip all readable text
- strip material emphasis
- strip object listing
- preserve only spatial grammar
- inject ANTI_ANCHOR_A again
```

### If AnchorB fails

Common drift:

```text
- became moodboard
- became design guide
- became material board
- became poster with headings
- reconstructed full room
- added numbered sections or captions
- used color palette rows or photo sample grids
```

Repair rule:

```text
- remove all headings, labels, captions
- remove section boxes
- remove grid-board behavior
- remove full scene reconstruction
- retain only abstract samples
- use “silent texture laboratory” framing
- inject ANTI_ANCHOR_B again
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
- inject ANTI_ANCHOR_C again
```

---

## 10. Optional Split Mode for AnchorB

Use this only when B keeps drifting.

Rule:

```text
If AnchorB repeatedly turns into a moodboard, split B into B1-B4 instead of refining one big B.
```

### B1 — Material DNA only

```text
Generate TP01 AnchorB1: Material DNA only.

This is NOT a moodboard, NOT a design guide, NOT an infographic, NOT a poster.

Create a portrait sheet with only abstract material samples on pale paper:
- source-derived tactile texture fragments
- frayed / smooth / matte / glossy surface behavior when present
- edge roughness and surface grain

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
```

### B2 — Palette / Light DNA only

```text
Generate TP01 AnchorB2: Palette and Lighting DNA only.

Create a portrait visual language sheet showing only the color and light system extracted from the current source image.

Use soft watercolor washes, light gradients, shadow softness, warm/cool balance, glow samples, and tiny accent color hints.

No full composition.
No material inventory.
No object vocabulary.
No readable labels.
No headings.
No captions.
No photo recreation.
No moodboard layout.
No color palette row with labels.
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

## 11. Source-Specific Prompt Fill Template

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
- parameter_ranges:

AnchorB source-specific focus:
- material:
- palette:
- light:
- edge:
- atmosphere:
- parameter_ranges:

AnchorC source-specific focus:
- primary_objects:
- secondary_objects:
- connectors:
- reusable_variants:
- micro_details:
- parameter_ranges:
```

This fill must be derived from current source input, not memory.

---

## 12. Source-Specific Compiler Fill Template

After runtime files exist, compile each anchor prompt with this template.

```md
# TP01_COMPILED_PROMPT

target_anchor:
source_refs:
role_lock:
primary_question:
source_derived_positive_features:
allowed_visual_language:
parameter_ranges:
hard_negatives:
output_format:
fail_conditions:
```

Example role lock values:

```text
AnchorA = layout grammar only; answer only how the source is arranged.
AnchorB = style DNA only; answer only how the source feels visually.
AnchorC = asset vocabulary only; answer only what components can be recombined.
```

---

## 13. Successful 2026-06-30 Extraction Lessons

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
B failed when prompted as moodboard / style DNA sheet / design guide.
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

## 14. Prompt Editing Rule

When future prompt refinement is needed:

```text
Edit this file first.
Do not edit Tp01.md unless stop points, runtime contract, source routing, or package governance changes.
```

This keeps TP01 stable while allowing extraction behavior to improve.

Useful external critiques should be absorbed as mechanisms, not blindly accepted as premises.

```text
If a critique identifies a real failure mode, convert it into compiler rules, hard negatives, ranges, audit gates, or downstream usage steps.
If a critique misreads current TP01 behavior, keep the mechanism and discard the wrong premise.
```

# TP01 Failure Salvage Gate

version: 1.0.0
status: active
updated_at: 2026-07-02
scope: TP01 anchor-generation failure recovery

---

## 0. Purpose

This file defines how TP01 should handle generated images that fail their target anchor role but may still be useful.

Core rule:

```text
A failed image is not automatically trash.
A failed image is also not automatically a valid retry base.
First classify its role.
```

The goal is to prevent a common TP01 failure loop:

```text
failed anchor image looks attractive
→ assistant uses it as the next base
→ wrong structure becomes stronger
→ anchor role is contaminated
```

---

## 1. Required Salvage Gate

After every generated anchor image, run the normal TP01 post-generation audit first.

If the image fails, run this additional gate before retrying:

```yaml
failed_but_useful_gate:
  target_role: AnchorA / AnchorB / AnchorC
  verdict_as_target: PASS / PASS_WITH_WARNING / FAIL
  failure_mode:
    - finished_card_drift
    - specimen_card_drift
    - moodboard_drift
    - design_guide_drift
    - material_board_drift
    - scene_drift
    - object_catalog_drift
    - layout_skeleton_drift
    - style_DNA_drift
    - text_or_label_drift
    - source_recreation_drift
  salvageable: yes / no
  salvage_role:
    - negative_diagnostic
    - final_card_draft
    - style_reference_board
    - asset_reference_sheet
    - composition_candidate
    - discard_contaminant
  allowed_next_action:
    - retry_same_role_from_clean_prompt
    - retry_same_role_from_failed_image
    - reclassify_to_downstream_draft
    - store_as_negative_diagnostic
    - discard
```

No retry may proceed until this gate is resolved.

---

## 2. Reuse Rule

A failed image may be reused as a visual base only when it is still inside the same anchor role.

```text
If it fails as AnchorA but is still a layout skeleton, it may be reused for AnchorA repair.
If it fails as AnchorB but is still a texture / atmosphere study, it may be reused for AnchorB repair.
If it fails as AnchorC but is still a separated asset vocabulary sheet, it may be reused for AnchorC repair.
```

A failed image must not be reused as the next anchor base when it has drifted into another role.

```text
finished card        → not a valid AnchorA/B/C base
specimen card        → not a valid AnchorA/B/C base
moodboard            → not a valid AnchorB base
design guide         → not a valid AnchorB base
material board       → not a valid AnchorB base
full scene           → not a valid AnchorC base
object catalog       → not a valid AnchorA/B base
```

---

## 3. Negative Diagnostic Mode

Use this when the failed image reveals the model's drift pattern.

Example:

```yaml
failed_image:
  target_role: AnchorA
  actual_output: specimen card with title, panels, labels, color notes, scale, tags
  verdict_as_target: FAIL
  salvageable: yes
  salvage_role: negative_diagnostic
  allowed_next_action: retry_same_role_from_clean_prompt
```

Diagnostic extraction:

```text
Record what the model tried to add.
Turn those additions into a short avoid list.
Then retry from a clean role-specific prompt, not from the failed image.
```

Do not use the failed image as base in negative diagnostic mode.

---

## 4. Downstream Draft Reclassification

Some failed anchors are useful because they resemble a later final output.

Example:

```yaml
failed_image:
  target_role: AnchorA
  actual_output: finished museum-style specimen card
  verdict_as_target: FAIL
  salvageable: yes
  salvage_role: final_card_draft
  allowed_next_action: reclassify_to_downstream_draft
```

This means:

```text
The image is rejected as an anchor.
The image may be stored as a downstream final-card draft.
It must not feed back into AnchorA/B/C extraction.
```

If the user later requests a final card / poster / specimen card, the image can be used as a composition candidate after A/B/C are completed and audited.

---

## 5. Retry Modes

### RETRY_SAME_ROLE_FROM_CLEAN_PROMPT

Use when the failure drifted into a different role.

```text
Do not use the failed image as visual base.
Remove trigger words that caused drift.
Use a shorter positive target statement.
Use one compact hard-negative line.
```

Examples:

```text
For AnchorA, avoid trigger words such as specimen, card, reference, overview, labels, recognition points.
Use: abstract spatial construction sketch, no text.

For AnchorB, avoid trigger words such as style DNA, moodboard, reference board, palette, swatch, design guide.
Use: silent surface atmosphere study, no text, no grid.

For AnchorC, avoid trigger words such as scene, final composition, poster, layout guide.
Use: separated reusable components, no unified scene.
```

### RETRY_SAME_ROLE_FROM_FAILED_IMAGE

Allowed only when the failed image remains mostly inside the same anchor role.

Required condition:

```yaml
same_role_repair_allowed:
  target_role_match: yes
  no_cross_role_drift: yes
  no_finished_output_drift: yes
  repair_scope_small: yes
```

### RECLASSIFY_TO_DOWNSTREAM_DRAFT

Use when a failed anchor looks useful as a later final image.

```text
Store it separately.
Label it as downstream draft.
Do not count it as AnchorA/B/C.
Do not package it as a required anchor output.
```

### DISCARD_AS_CONTAMINANT

Use when the image is likely to pollute future generations.

```text
Do not use it as base.
Do not include it in the anchor package.
Only describe the failure mode if useful.
```

---

## 6. Known Drift Patterns From 2026-07-02 Run

These examples are now part of TP01 anti-regression behavior.

### AnchorA failure pattern

```yaml
target: AnchorA layout grammar only
failure_output: finished specimen / museum card
bad_features:
  - title
  - headings
  - overview panel
  - recognition points
  - structure map with labels
  - color notes
  - tags
  - reference scale
  - copied source image as main panel
classification:
  verdict_as_target: FAIL
  salvage_role: negative_diagnostic OR final_card_draft
  allowed_next_action: retry_same_role_from_clean_prompt
forbidden_next_action: retry AnchorA using failed image as base
```

Correction:

```text
Remove TP01 / AnchorA / specimen / card / recognition / overview language.
Use only abstract spatial construction sketch language.
No readable text.
No panels.
No card border.
No source-photo frame.
```

### AnchorB failure pattern

```yaml
target: AnchorB style DNA only
failure_output: moodboard / design reference sheet
bad_features:
  - title
  - text labels
  - photo tiles
  - color swatches
  - tool illustrations
  - sectioned grid
  - material-board behavior
classification:
  verdict_as_target: FAIL
  salvage_role: negative_diagnostic OR style_reference_board
  allowed_next_action: retry_same_role_from_clean_prompt
forbidden_next_action: retry AnchorB using failed moodboard as base
```

Correction:

```text
Avoid style DNA / moodboard / reference / board / swatch / palette language.
Use only silent surface atmosphere study language.
No text.
No grid.
No panels.
No color chips.
```

---

## 7. Required Report Add-On

When a generated anchor fails, append this to the normal TP01 audit report:

```md
## Failed-but-useful salvage gate

target_role:
verdict_as_target:
failure_mode:
salvageable:
salvage_role:
allowed_next_action:
forbidden_next_action:
retry_prompt_correction:
```

---

## 8. One-Line Rule

```text
Failed anchors may inform the next retry, but they may not become the next anchor base unless they still belong to the same anchor role.
```

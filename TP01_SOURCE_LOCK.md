# TP01_SOURCE_LOCK

version: 1.0
status: active
created_at: 2026-06-30
purpose: 固定 TP01 的 canonical GitHub 讀取入口，取代以 GDrive 作為 TP01 範本與 seed anchor 來源的預設流程。

---

## 1. Canonical Repository

```text
repository: hoiyu915-droid/Tp01
branch: main
```

TP01 之後以此 GitHub repository 作為 canonical source。

---

## 2. Canonical Raw Links

### TP01 procedure markdown

```text
https://raw.githubusercontent.com/hoiyu915-droid/Tp01/main/Tp01.md
```

### AnchorA

```text
https://raw.githubusercontent.com/hoiyu915-droid/Tp01/main/AnchorA.PNG
```

### AnchorB

```text
https://raw.githubusercontent.com/hoiyu915-droid/Tp01/main/AnchorB.PNG
```

### AnchorC

```text
https://raw.githubusercontent.com/hoiyu915-droid/Tp01/main/AnchorC.PNG
```

---

## 3. Execution Rule

When the user invokes `TP01` / `tp01` without attaching files:

1. Use GitHub connector to read repository metadata, file SHA, and `Tp01.md` content.
2. Use the raw GitHub links above to read image binary / visual content for `AnchorA.PNG`, `AnchorB.PNG`, and `AnchorC.PNG`.
3. Do not use GDrive as the default TP01 template source.
4. Do not use GDrive as the default TP01 seed anchor source.
5. Only use GDrive if the user explicitly asks for Drive upload, Drive audit, or Drive-side verification.

---

## 4. Tool Routing

```text
GitHub connector:
  - Tp01.md
  - SHA
  - repository metadata
  - text/procedure audit

raw.githubusercontent.com:
  - AnchorA.PNG visual content
  - AnchorB.PNG visual content
  - AnchorC.PNG visual content
```

Reason:

```text
GitHub connector is reliable for text, SHA, and metadata.
Raw links are more reliable for image binary / visual anchor reading.
```

---

## 5. Current Canonical Anchors

```text
AnchorA.PNG = layout grammar anchor
AnchorB.PNG = style DNA anchor
AnchorC.PNG = asset / object vocabulary anchor
```

These three files are treated as the active TP01 anchor set unless replaced by a later committed version.

---

## 6. Verification Checklist

Before executing TP01 from this source, confirm:

```text
Tp01.md readable via GitHub connector or raw link
AnchorA.PNG readable via raw link
AnchorB.PNG readable via raw link
AnchorC.PNG readable via raw link
```

If any raw anchor link fails, report the failure explicitly and do not silently fall back to GDrive.

---

## 7. Override Rule

User explicit instruction always wins.

Examples:

```text
"用 GDrive 的 TP01"
"用這次附上的 AnchorA/B/C"
"不要用 GitHub raw"
```

In those cases, follow the user-provided source instead of this source lock.

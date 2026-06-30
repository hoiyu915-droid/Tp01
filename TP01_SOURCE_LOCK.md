# TP01_SOURCE_LOCK

version: 1.1.0
status: active
updated_at: 2026-06-30
purpose: 固定 TP01 的 canonical GitHub 讀取入口，取代以 GDrive 作為 TP01 範本與 seed anchor 來源的預設流程。

---

## 1. Canonical Repository

```text
repository: hoiyu915-droid/Tp01
branch: main
canonical: true
```

TP01 / tp01 沒附檔時，以此 GitHub repository 作為唯一預設 canonical source。

---

## 2. Canonical Read Order

```text
GitHub repo metadata
-> TP01_SOURCE_LOCK.md
-> Tp01.md text / SHA / metadata
-> raw AnchorA.PNG
-> raw AnchorB.PNG
-> raw AnchorC.PNG
```

不可把 GDrive 當作 fallback default。

---

## 3. Canonical Raw Links

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

## 4. Tool Routing

```text
GitHub connector:
  - repository metadata
  - TP01_SOURCE_LOCK.md
  - Tp01.md
  - SHA / metadata
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

## 5. No-GDrive Default Rule

When the user invokes `TP01` / `tp01` without attaching files:

```text
Do not use GDrive as the default TP01 template source.
Do not use GDrive as the default TP01 seed anchor source.
Do not search Drive for Tp01.md.
Do not search Drive for AnchorA/B/C.
Do not silently fall back to Drive if GitHub fails.
```

GDrive is allowed only when the user explicitly requests one of the following:

```text
Drive upload
Drive audit
Drive verification
use GDrive TP01
use Drive anchors
check Drive folder
```

---

## 6. Current Canonical Anchors

```text
AnchorA.PNG = layout grammar anchor
AnchorB.PNG = style DNA anchor
AnchorC.PNG = asset / object vocabulary anchor
```

These three files are treated as the active TP01 anchor set unless replaced by a later committed version in this repository.

---

## 7. Verification Checklist

Before executing TP01 from this source, confirm:

```text
[ ] repository metadata readable
[ ] TP01_SOURCE_LOCK.md readable
[ ] Tp01.md readable via GitHub connector or raw link
[ ] Tp01.md SHA / metadata available
[ ] AnchorA.PNG readable via raw link
[ ] AnchorB.PNG readable via raw link
[ ] AnchorC.PNG readable via raw link
[ ] no GDrive source used unless explicitly requested
```

If any raw anchor link fails, report the failure explicitly and do not silently fall back to GDrive.

---

## 8. Override Rule

User explicit instruction always wins.

Examples:

```text
用 GDrive 的 TP01
用這次附上的 AnchorA/B/C
不要用 GitHub raw
幫我 audit Drive 那份
幫我 upload 到 Drive
```

In those cases, follow the user-provided source instead of this source lock.

---

## 9. Anti-Regression Rule

Any future TP01 edit must preserve this invariant:

```text
TP01 default source = GitHub repo hoiyu915-droid/Tp01
TP01 default procedure = Tp01.md from GitHub
TP01 default anchors = raw AnchorA/B/C from GitHub
GDrive = explicit-only side path
```

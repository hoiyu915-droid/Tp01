# TP01

Canonical TP01 source repository.

Read path:

```text
TP01_SOURCE_LOCK.md
-> Tp01.md
-> TP01_PROMPTS.md
-> AnchorA.PNG
-> AnchorB.PNG
-> AnchorC.PNG
```

## Files

```text
TP01_SOURCE_LOCK.md        source lock
Tp01.md                    executable workflow
TP01_PROMPTS.md            prompt module / compiler / audit rules
TP01_FAILURE_SALVAGE.md    failed-but-useful salvage gate and retry classification
AnchorA.PNG                layout grammar anchor
AnchorB.PNG                style DNA anchor
AnchorC.PNG                asset vocabulary anchor
```

## Runtime check

```text
[ ] read TP01_SOURCE_LOCK.md
[ ] read Tp01.md and metadata
[ ] read TP01_PROMPTS.md and metadata
[ ] read AnchorA.PNG
[ ] read AnchorB.PNG
[ ] read AnchorC.PNG
```

## Failure recovery add-on

When an AnchorA / AnchorB / AnchorC generation fails, do not immediately reuse the failed image as the next base.

Read `TP01_FAILURE_SALVAGE.md` and classify the failed image first:

```text
FAIL_AS_TARGET
-> negative diagnostic / downstream draft / same-role repair / discard contaminant
-> retry only through the allowed next action
```

Core anti-regression rule:

```text
Failed anchors may inform the next retry, but they may not become the next anchor base unless they still belong to the same anchor role.
```

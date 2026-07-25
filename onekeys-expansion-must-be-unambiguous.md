---
name: onekeys-expansion-must-be-unambiguous
description: "adding a key to `print_defaults` in scripts/onekeys-hook.sh: vague expansions (\"What's next?\", \"Status.\") get conflated with neighbouring keys; write the expansion as an imperative naming the action"
metadata: 
  node_type: memory
  type: project
  originSessionId: 3bb7775f-b954-40dd-9549-7fe091c8335e
  modified: 2026-07-25T14:06:03.527Z
---

In onekeys, a default expansion is injected as `additionalContext` with no
other user text to anchor it, so the expansion alone has to determine the
action. Short, vague expansions do not: `n` → "What's next?" was acted on
as either "list pending tasks" or "continue", and `s` → "Status." was acted
on as "list pending tasks" — both were dropped on 2026-07-25 in favour of
`p` → "List pending tasks, no tool use allowed."

**Why:** the one-character prompt carries no intent of its own, so an
expansion that reads as a topic rather than an instruction leaves the
choice of action to inference — and neighbouring keys with overlapping
meanings collapse into whichever reading is most available.

**How to apply:** when adding or reviewing a default key, write the
expansion as an imperative naming the action, plus any constraint that
distinguishes it (e.g. "no tool use allowed"). Reject an expansion whose
plausible readings overlap another key's. Related:
[[release-marketplace-push-blocked]].

---
name: release-marketplace-push-blocked
description: just release pushes to the separate claude-plugins repo; the auto-mode classifier blocks that cross-repo push and the user must run it manually
metadata: 
  node_type: memory
  type: project
  originSessionId: b3abef1d-4986-42b7-87ed-5e7a0d9d0c7a
---

`just release` (from the vendored `plugin-dev/release.just`) bumps and pushes TWO repos: the plugin itself, and the separate `ddaanet/claude-plugins` marketplace repo at `$MARKETPLACE_DIR` (`/Users/david/code/claude-plugins`).

The Claude Code auto-mode classifier blocks `git push` to `claude-plugins` because it is a repo other than the one Claude is invoked in — even with explicit user confirmation via AskUserQuestion. Local commits to it are allowed; only the push is blocked.

**Why:** the classifier treats pushing to a different repo's default branch as out-of-scope regardless of verbal approval.

**How to apply:** when running a release or editing the marketplace, do the local commit yourself, then hand the user the exact push command to run in-session with the `!` prefix (e.g. `! git -C /Users/david/code/claude-plugins push`). Don't retry the blocked push. Related: [[sandbox-protected-paths]].

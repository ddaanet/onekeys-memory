---
name: sandbox-phantom-dotfiles
description: "Sandboxed git status in this repo shows phantom untracked home dotfiles (.bashrc, .zshrc, .gitconfig, .idea, .vscode, .mcp.json…) that don't really exist; trust unsandboxed git status"
metadata: 
  node_type: memory
  type: project
  originSessionId: 60632fa9-e3bb-4ae1-b906-ea0f0f727a6b
---

In /Users/david/code/onekeys, a **sandboxed** `git status` lists many untracked dotfiles at the repo root — `.bashrc`, `.bash_profile`, `.profile`, `.zprofile`, `.zshrc`, `.gitconfig`, `.gitmodules`, `.ripgreprc`, `.mcp.json`, `.idea`, `.vscode`, `.claude/agents`, `.claude/commands`, `.claude/skills`. Run **unsandboxed** (`dangerouslyDisableSandbox: true`) and they vanish — only real changes show.

**Why:** The sandbox surfaces home-directory files at the repo root (HOME/filesystem overlay); they are not actual untracked files in the working tree.

**How to apply:** Don't add these to git or `.gitignore`, and don't treat them as work to clean up. For true working-tree state, trust unsandboxed `git status`. Related: [[sandbox-protected-paths]].

<p align="center">
  <img src="logo.png" alt="playgentic" width="160" />
</p>

<h1 align="center">playgentic</h1>

<p align="center">
  <b>Agent-first test automation for Playwright.</b><br />
  Agents that explore your app, write tests the way your team would, and audit their own work.
</p>

---

## What we build

| Project | What it is |
| --- | --- |
| [**playgentic-agents**](https://github.com/Playgentic/playgentic-agents) | One plugin for **Claude Code**, **GitHub Copilot** and **Codex** that writes and heals Playwright tests in any repo, plain Playwright or playwright-bdd, greenfield or brownfield. |
| [**playgentic**](https://github.com/Playgentic/playgentic) · [npm](https://www.npmjs.com/package/playgentic) | Scaffolds an opinionated Playwright-BDD suite: docstringed steps, page objects, a generated suite wiki, lint gates and CI. It wires up the agents in the same command. |

The two work separately or together. The plugin learns any suite's conventions. The scaffold gives it a suite with conventions worth learning.

## Quick start

New suite, agents included:

```bash
npx playgentic init my-suite --agents claude,copilot,codex   # any subset, or "all"
```

Existing repo, agents only:

```
/plugin marketplace add https://github.com/playgentic/playgentic-agents       # Claude Code, then: /plugin install playgentic@playgentic
copilot plugin marketplace add https://github.com/playgentic/playgentic-agents       # GitHub Copilot, then: copilot plugin install playgentic@playgentic
codex plugin marketplace add https://github.com/playgentic/playgentic-agents         # Codex, then: codex plugin add playgentic@playgentic
```

Then ask your agent to run **`author-tests`**:

```
author-tests --gen cover applying and removing coupons at checkout
author-tests --heal the login scenario fails after the redesign
```

## How it works

1. **Branch.** Every run gets its own feature branch, and a worktree if the work is parallel.
2. **Learn.** It reads your suite, your `CONVENTIONS.md`, and your per-agent extensions.
3. **Plan.** It agrees numbered acceptance criteria with you before building anything.
4. **Explore → build.** An explorer reads the live app. Builders write and run tests in your style.
5. **Audit.** A read-only auditor checks that each test really verifies its criterion, not just that it passes.
6. **Hand off.** It commits test files only, and never pushes without asking.

Your team's rules live in your repo (`.playgentic/wiki/`), not in the plugin, so updates never overwrite them.

## Principles

- **Your conventions win.** The agents follow your code style and testing expectations over their own defaults.
- **Honest coverage.** No `.skip`, no weakened assertions, no config tweaks to get green, unless you explicitly allow it.
- **Finding a bug is a success.** Agents report real app defects instead of bending tests until they pass.
- **Minimal by design.** Markdown skills and agents, zero-dependency tooling, nothing to sync.

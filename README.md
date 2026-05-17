# mturac/tools

Open-source tools for AI-augmented engineering — Claude Code plugins, MCP servers, security scanners, schedulers, and dev-productivity utilities.
Each project is its own repo with its own LICENSE, README, tests, and release tags.

[![PyPI argus-audit](https://img.shields.io/pypi/v/argus-audit?label=pypi%20argus-audit)](https://pypi.org/project/argus-audit/)
[![License: MIT](https://img.shields.io/badge/license-MIT-yellow.svg)](LICENSE)
[![Claude Code Marketplace](https://img.shields.io/badge/Claude%20Code-marketplace-blue?logo=anthropic)](https://github.com/mturac/claude-plugin-marketplace)

## Listed in

- [`awesome-agents` (kyrolabs) — PR #483](https://github.com/kyrolabs/awesome-agents/pull/483)
- [`awesome-claude-code-toolkit` (rohitg00) — PR #412](https://github.com/rohitg00/awesome-claude-code-toolkit/pull/412)
- [`Awesome-AI-Agents` (Jenqyang) — PR #241](https://github.com/Jenqyang/Awesome-AI-Agents/pull/241)
- Auto-discovered by `claudemarketplaces.com`, `claude-plugins.dev`, and `Chat2AnyLLM/awesome-claude-plugins`
- Pending manual submissions: [anthropics/claude-plugins-official](https://clau.de/plugin-directory-submission) and [mcpservers.org/submit](https://mcpservers.org/submit) (web forms)

## Claude Code plugins (pluginpool)

Ten small, focused plugins solving real day-to-day developer-productivity problems. Python 3 stdlib only at runtime; hermetic tests.

| Plugin | What it does | Repo |
|---|---|---|
| `argus-audit` | White-hat security audit + pentest orchestrator. Scope-gated authz vault, intel layer (NVD/KEV/EPSS), 5 scanners (static / secrets / supply-chain / TLS / HTTP). 174 tests. | [mturac/pluginpool-argus-audit](https://github.com/mturac/pluginpool-argus-audit) |
| `commit-narrator` | Conventional commit message generator from staged git diff. | [mturac/pluginpool-commit-narrator](https://github.com/mturac/pluginpool-commit-narrator) |
| `pr-storyteller` | PR title + body + test plan from commits/diff vs base branch. | [mturac/pluginpool-pr-storyteller](https://github.com/mturac/pluginpool-pr-storyteller) |
| `test-gap` | Surface changed git diff lines that aren't covered by tests. Cobertura / LCOV / `coverage.py`. | [mturac/pluginpool-test-gap](https://github.com/mturac/pluginpool-test-gap) |
| `deps-doctor` | Dependency vuln/outdated/license audit across npm / pip / cargo / go. Monorepo-aware. | [mturac/pluginpool-deps-doctor](https://github.com/mturac/pluginpool-deps-doctor) |
| `standup-gen` | Daily standup notes from git activity across one or many repos. | [mturac/pluginpool-standup-gen](https://github.com/mturac/pluginpool-standup-gen) |
| `todo-harvest` | TODO/FIXME/HACK scan with git blame author + age in days. Batched per-file blame. | [mturac/pluginpool-todo-harvest](https://github.com/mturac/pluginpool-todo-harvest) |
| `env-lint` | `.env` vs `.env.example` key parity. Inline-comment safe, `--strict` mode. | [mturac/pluginpool-env-lint](https://github.com/mturac/pluginpool-env-lint) |
| `secret-guard` | Pre-commit secret scanner: regex + entropy, with SHA-redacted output. | [mturac/pluginpool-secret-guard](https://github.com/mturac/pluginpool-secret-guard) |
| `flaky-detector` | Run a test command N times, report per-test flakiness % with pytest -q imputation. | [mturac/pluginpool-flaky-detector](https://github.com/mturac/pluginpool-flaky-detector) |
| `changelog-forge` | Group conventional commits since last tag into a CHANGELOG section + semver bump suggestion. | [mturac/pluginpool-changelog-forge](https://github.com/mturac/pluginpool-changelog-forge) |

## AI-agent infrastructure

| Project | What it does | Repo |
|---|---|---|
| 🪑 **claude-roundtable** | Multi-agent governance for Claude Code. Council deliberates, votes, dispatches, and enforces quality gates. | [mturac/claude-roundtable](https://github.com/mturac/claude-roundtable) |
| ⏱️ **leyla-scheduler** | Durable, session-aware task scheduler in Rust. Jobs survive disconnects. | [mturac/leyla-scheduler](https://github.com/mturac/leyla-scheduler) |
| 🔎 **skill-hunter** | Pre-execution layer that makes agents check for existing skills before building from scratch. | [mturac/skill-hunter](https://github.com/mturac/skill-hunter) |
| 🛡️ **promptguard** | Audits prompts as behavioral contracts. Pre-write guard for agents that ship code. | [mturac/promptguard](https://github.com/mturac/promptguard) |
| 🧠 **recall-mcp** | Shared brain for AI agents. SQLite-backed persistent memory over MCP. Hybrid FTS5 + vector search. | [mturac/recall-mcp](https://github.com/mturac/recall-mcp) |
| 👵 **moooom-claude** | 10 cultures of moms nagging your Claude Code to drink water and sit up straight. | [moooom-claude/moooom-claude](https://github.com/moooom-claude/moooom-claude) |

## Install everything as a Claude Code marketplace

The pluginpool plugins + argus-audit + moooom-claude + skill-hunter expose a `.claude-plugin/plugin.json` manifest and can be added in one step via the marketplace:

```bash
# Add the marketplace to Claude Code
/plugin marketplace add mturac/claude-plugin-marketplace

# Browse and install plugins
/plugin install argus-audit
/plugin install commit-narrator
/plugin install moooom-claude
# …
```

See [mturac/claude-plugin-marketplace](https://github.com/mturac/claude-plugin-marketplace) for the manifest catalog.

## Design principles

1. **Tests are not optional.** Every project ships a test suite that runs offline with no network.
2. **Standard library first.** Python-stdlib-only where possible. External dependencies require justification.
3. **Plugins are independent repos.** Each can be open-sourced, vendored, or installed individually.
4. **Reviewed before release.** Every v0.1.0 tag landed after at least one round of `MiMo` / gemini code review with the findings explicitly addressed.

## License

All projects are MIT licensed unless their own `LICENSE` file says otherwise. Each repo carries its own copy.

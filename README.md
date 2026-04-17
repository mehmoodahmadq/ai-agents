# ai-agents

**Production-ready AI agent definitions for every dev workflow.**

Each file in this repo *is* the agent — a complete, self-contained system prompt you drop into your project and use immediately. No runtime, no framework, no setup. Just markdown.

---

## Why this exists

Most "AI agents" repositories are catalogs: they list use cases, describe what an agent *could* do, and link off to demos. This one is different.

- **Every file is a working agent.** Copy it, use it.
- **Opinionated, not exhaustive.** Each agent takes a clear stance on the right way to do things in its domain. No "you could also consider..." hedging.
- **Security-aware by default.** Every language agent has a dedicated Security section covering injection, crypto, secrets, deserialization, and supply chain — not an afterthought.
- **Current tooling only.** No legacy patterns, no dated advice. Python uses `uv` and Ruff. TypeScript uses Zod and `satisfies`. Swift uses Swift Concurrency. Kotlin uses coroutines and Compose.
- **Tool-agnostic.** Written for Claude Code's sub-agent system, but the body of every file is a plain system prompt — drop it into ChatGPT, Cursor, Windsurf, or any API call.

---

## Quick start

### With Claude Code

```bash
# From the root of your project
mkdir -p .claude/agents
cp /path/to/ai-agents/agents/typescript.md .claude/agents/
```

Then invoke in Claude Code:

```
/typescript refactor this service to use Zod validation
```

Claude Code auto-routes to the right agent based on the `description` field in the frontmatter.

### With any other AI tool

Everything below the `---` frontmatter block is a plain system prompt. Copy it into ChatGPT's "custom GPT" instructions, Cursor rules, Windsurf workflows, or an API call's `system` parameter.

```python
import anthropic

with open("agents/python.md") as f:
    content = f.read()
    system_prompt = content.split("---", 2)[2].strip()

client = anthropic.Anthropic()
client.messages.create(
    model="claude-opus-4-7",
    system=system_prompt,
    messages=[...],
)
```

---

## Available agents

| Agent | Focus | Highlights |
|-------|-------|------------|
| [typescript](agents/typescript.md) | Type-safe TypeScript | Strict mode, Zod, discriminated unions, `satisfies`, no `any` |
| [javascript](agents/javascript.md) | Modern JavaScript | ES2020+, async/await, Web APIs, zero-dep mindset |
| [python](agents/python.md) | Idiomatic Python | Type hints, Pydantic, asyncio, Ruff, mypy strict |
| [go](agents/go.md) | Production Go | Explicit errors, small interfaces, errgroup, context propagation |
| [rust](agents/rust.md) | Systems Rust | Ownership, `thiserror`/`anyhow`, Tokio, zero-cost abstractions |
| [java](agents/java.md) | Modern Java 21 | Records, sealed classes, Spring Boot, constructor injection |
| [csharp](agents/csharp.md) | C# 12 / .NET 8 | Nullable safety, ASP.NET Core, EF Core, async end-to-end |
| [ruby](agents/ruby.md) | Idiomatic Ruby / Rails | Service objects, thin controllers, RSpec, security-first Rails |
| [swift](agents/swift.md) | Modern Swift | SwiftUI, Swift Concurrency, `Actor`, value semantics |
| [kotlin](agents/kotlin.md) | Modern Kotlin | Coroutines, Flow, Compose, MVVM, null safety |

---

## Agent file format

Every agent follows the same structure:

```markdown
---
name: <slug>
description: <one-line description — used by Claude Code for auto-routing>
---

You are an expert <role>...

## Core Principles
## <Domain sections — Type System, Error Handling, Concurrency, etc.>
## Security
## Tooling
## What to Avoid
```

The `description` field matters: it's what Claude Code reads to decide which sub-agent to invoke for a given task. Keep it specific and action-oriented.

---

## Quality bar

Every agent in this repo must be:

- **Opinionated** — one clear stance, not a survey of options.
- **Actionable** — code examples, not vague prose.
- **Current** — reflects the ecosystem *today*, not five years ago.
- **Self-contained** — usable without reading any other file.
- **Security-aware** — a dedicated Security section is mandatory, not optional.
- **Honest about trade-offs** — explains *why* a decision was made.

If a PR adds an agent that doesn't meet all six, it doesn't merge.

---

## Roadmap

Currently flat under `agents/`. Once the collection grows past ~20 agents, it will be reorganized by domain:

```
agents/
  languages/     typescript, python, go, rust, ...
  frontend/      react, vue, svelte, a11y, css
  backend/       express, fastapi, django, database-design
  devops/        docker, kubernetes, terraform, ci-cd
  security/      threat-modeling, owasp-review, secure-code-review
  data/          sql, pipelines, ml-workflows
  mobile/        react-native (swift and kotlin move here)
```

Naming: `<stack-or-tool>.md` — lowercase, hyphenated, no version numbers in filenames.

---

## Contributing

PRs welcome. Before opening one:

1. Read an existing agent to match the structure and tone.
2. Make sure your agent meets every point in the [Quality bar](#quality-bar).
3. Include a working code example in every major section.
4. Add a dedicated `## Security` section — no exceptions.

---

## License

MIT

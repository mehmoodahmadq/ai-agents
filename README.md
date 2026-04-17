# ai-agents

Production-ready AI agent definitions for every dev workflow.

Each agent is a drop-in system prompt — opinionated, battle-tested, and ready to use with Claude Code or any AI tool that accepts a system prompt.

## What's in here

Unlike collections that list use cases or link to demos, every file in this repo **is** the agent. Copy it, drop it in, and start working.

## Usage

### Claude Code

Copy any agent file into your project's `.claude/agents/` directory:

```bash
cp agents/typescript.md .claude/agents/typescript.md
```

Then invoke it in Claude Code:

```
/typescript refactor this service to use proper error handling
```

### Other AI Tools

Each agent file contains a system prompt that works with any model or tool that accepts a system prompt (ChatGPT, Cursor, Windsurf, API calls, etc.). Use the content below the frontmatter `---` block.

## Agents

| Agent | Description |
|-------|-------------|
| [typescript](agents/typescript.md) | Type-safe TypeScript — strict mode, Zod, modern patterns |
| [javascript](agents/javascript.md) | Modern JS — ES2020+, async/await, no unnecessary deps |
| [python](agents/python.md) | Idiomatic Python — type hints, Pydantic, Ruff, asyncio |
| [go](agents/go.md) | Idiomatic Go — explicit errors, interfaces, structured concurrency |
| [rust](agents/rust.md) | Systems Rust — ownership, Result, zero-cost abstractions, Tokio |
| [java](agents/java.md) | Modern Java 21 — records, Spring Boot, clean architecture |
| [csharp](agents/csharp.md) | Modern C# 12 / .NET 8 — nullable safety, ASP.NET Core, async |
| [ruby](agents/ruby.md) | Idiomatic Ruby — Rails conventions, service objects, RSpec |
| [swift](agents/swift.md) | Modern Swift — SwiftUI, Swift Concurrency, value semantics |
| [kotlin](agents/kotlin.md) | Modern Kotlin — coroutines, Flow, Jetpack Compose, MVVM |

## Contributing

Each agent should be:

- **Opinionated** — take a clear stance on the right way to do things
- **Actionable** — concrete examples, not vague advice
- **Current** — reflect modern tooling and patterns
- **Self-contained** — no external dependencies or references needed to use it

## License

MIT

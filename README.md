# AI Rules for .NET

My personal guidelines for [Claude Code](https://claude.com/claude-code) when working on .NET projects.
The goal: code that looks like an experienced developer wrote it by hand. Direct, readable, few types, no enterprise ceremony.

## What's inside

| File | Purpose |
| --- | --- |
| [`.claude/rules/coding-guideline.md`](.claude/rules/coding-guideline.md) | C# style, solution layout, controllers, data access, testing, naming |
| [`.claude/rules/development-guideline.md`](.claude/rules/development-guideline.md) | Process rule: confirm before changing the behavior of an existing feature |

## The main ideas

- **Write less code.** Smallest change that solves the request. No unrequested features, options or abstractions.
- **Few types.** No interface for a single implementation, no Factory/Manager/Helper classes, no MediatR/AutoMapper/FluentValidation.
- **Fixed solution layout.** `Shared`, `Core`, `Integrations`, `Web`, `Tests`. No extra Domain/Application/Infrastructure projects.
- **Thin controllers.** One service call per action. Errors handled in one place.
- **Read-only repositories.** One per aggregate root. Writes happen in services through `DbContext`.
- **Testable by design.** Business rules in pure static methods, repositories tested against a real database, `TimeProvider` for time.
- **Surgical changes.** Every changed line traces to the request. Report unrelated problems instead of fixing them.
- **Ask before changing existing features.** Their UI, flow, API contract, data or defaults.

## Usage

Copy the `.claude` folder into the root of your repository:

```
your-repo/
├── .claude/
│   └── rules/
│       ├── coding-guideline.md
│       └── development-guideline.md
└── ...
```

Claude Code loads the files in `.claude/rules/` automatically as project instructions.

To use them for every project, copy the files to `~/.claude/rules/` instead.

## Customizing

These rules reflect my preferences, so adjust them to your own:

- Replace `AppName` and the project/folder layout in the **Solution layout** and **Structure** sections.
- Remove sections you disagree with (for example the repository pattern under **Data access**).
- The development guideline refers to `docs/status.md` and `docs/history.md`. Create those files or change the rule.

## License

Use freely. Add a `LICENSE` file if you want to state terms explicitly.

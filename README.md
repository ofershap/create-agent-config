<h1 align="center">npx create-agent-config</h1>

<p align="center">
  <strong>Your AI coding agent starts every session blind. Fix that in 30 seconds.</strong>
</p>

<p align="center">
  Scaffold agent context files for Cursor, Claude Code, Copilot, Windsurf, Cline, and AGENTS.md.<br>
  Detects your stack. Pulls community rules from <a href="https://cursor.directory">cursor.directory</a>. You review before anything is written.
</p>

<p align="center">
  <a href="https://www.npmjs.com/package/create-agent-config"><img src="https://img.shields.io/npm/v/create-agent-config.svg" alt="npm version" /></a>
  <a href="https://www.npmjs.com/package/create-agent-config"><img src="https://img.shields.io/npm/dm/create-agent-config.svg" alt="npm downloads" /></a>
  <a href="https://github.com/ofershap/create-agent-config/actions/workflows/ci.yml"><img src="https://github.com/ofershap/create-agent-config/actions/workflows/ci.yml/badge.svg" alt="CI" /></a>
  <a href="https://www.typescriptlang.org/"><img src="https://img.shields.io/badge/TypeScript-strict-blue" alt="TypeScript" /></a>
  <a href="https://opensource.org/licenses/MIT"><img src="https://img.shields.io/badge/License-MIT-yellow.svg" alt="License: MIT" /></a>
</p>

---

<p align="center">
  <img src="assets/demo.gif" alt="Demo" />
</p>

## Quick start

```bash
npx create-agent-config
```

That's it. It scans your project, asks which formats you want, and writes the files.

`npm create agent-config` does the same thing (npm aliases `create` to `npx create-`).

```bash
# target a different directory
npx create-agent-config ./my-project

# skip network, use built-in templates only
npx create-agent-config --offline
```

## What exactly happens

1. **Scans** your project directory (package.json, tsconfig, lockfiles, config files)
2. **Detects** languages, frameworks, test runners, build tools, package manager
3. **Fetches** matching community rules from [cursor.directory](https://cursor.directory)'s open source repository (optional, skippable with `--offline`)
4. **Shows you** every file it plans to create and where
5. **Asks for confirmation** before writing anything
6. **Writes** the files you approved. Existing files are never overwritten.

Nothing is executed, uploaded, or sent to any API. The only network call is a GET request to raw.githubusercontent.com to fetch community rules. Pass `--offline` to skip it entirely.

## What gets created and where

You choose which files to generate. Here's every possible output:

| File                              | Location                   | Used by                                   |
| --------------------------------- | -------------------------- | ----------------------------------------- |
| `AGENTS.md`                       | project root               | Codex, Devin, Jules, SWE-agent, 40+ tools |
| `CLAUDE.md`                       | project root               | Claude Code                               |
| `.cursor/rules/project.mdc`       | `.cursor/rules/` directory | Cursor IDE (modern .mdc format)           |
| `.github/copilot-instructions.md` | `.github/` directory       | GitHub Copilot                            |
| `.windsurfrules`                  | project root               | Windsurf / Codeium                        |
| `.clinerules`                     | project root               | Cline                                     |

Each file contains your detected stack info (languages, frameworks, commands, conventions) plus community best practices if you opted in.

## What gets detected

| Category         | Examples                                                                                                                              |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| Languages        | TypeScript, JavaScript, Python, Rust, Go                                                                                              |
| Frameworks       | Next.js, React, Vue, Nuxt, Angular, Svelte, SvelteKit, Astro, Remix, NestJS, Express, Fastify, Hono, Electron, Django, Flask, FastAPI |
| Test runners     | Vitest, Jest, Mocha, Playwright, Cypress, pytest                                                                                      |
| Build tools      | tsup, esbuild, rollup, Vite, Webpack                                                                                                  |
| Package managers | npm, pnpm, yarn, bun                                                                                                                  |
| Monorepo         | Turborepo, Nx, Lerna, workspaces                                                                                                      |

Detection reads config files and package.json. Nothing is executed.

## Community rules

When online, the tool fetches framework-specific best practices from [cursor.directory](https://cursor.directory)'s [open source repository](https://github.com/pontusab/cursor.directory) on GitHub. These are community-curated rules maintained by 160+ contributors covering React, Next.js, TypeScript, Python, Vue, Angular, Svelte, NestJS, and many more.

You're asked whether to include them. If you decline or the fetch fails, the tool falls back to built-in defaults.

## Example output

Running against a Next.js + TypeScript project generates an `AGENTS.md` like this:

```markdown
# my-app

## Project

Languages: TypeScript
Frameworks: Next.js, React
Testing: Vitest
Package manager: pnpm

## Commands

- Dev server: `pnpm dev`
- Build: `pnpm build`
- Test: `pnpm test`
- Lint: `pnpm lint`

## Conventions

- Use TypeScript strict mode
- Prefer `const` over `let`, avoid `any`
- Use explicit return types on exported functions
- Functional components only, no class components
- Use hooks for state and side effects

## Best Practices

[community rules from cursor.directory for Next.js + React]

## Rules

- Do not modify generated files in `dist/` or `build/`
- Run tests before committing
- Keep commits small and focused
```

The `.cursor/rules/project.mdc` version includes YAML frontmatter with `alwaysApply: true`.

## Contributing

Contributions welcome. See [CONTRIBUTING.md](CONTRIBUTING.md).

## Author

[![Made by ofershap](https://gitshow.dev/api/card/ofershap)](https://gitshow.dev/ofershap)

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://linkedin.com/in/ofershap)
[![GitHub](https://img.shields.io/badge/GitHub-Follow-181717?style=flat&logo=github&logoColor=white)](https://github.com/ofershap)

---

<p align="center">
  Demo animation made with <a href="https://github.com/ofershap/remotion-readme-kit">remotion-readme-kit</a>
</p>

## License

[MIT](LICENSE) &copy; [Ofer Shapira](https://github.com/ofershap)

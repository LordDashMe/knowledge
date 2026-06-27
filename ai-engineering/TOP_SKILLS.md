# Top Skills

A curated list of go-to Claude Code plugins, skills, and tools — the ones worth
installing first to level up day-to-day AI engineering work. Each entry includes
its install command and a quick description of what it does and when to reach for
it.

## Quick Install

```bash
/plugin install skill-creator@claude-plugins-official
/plugin install superpowers@claude-plugins-official
npx get-shit-done-cc --claude --global
/plugin marketplace add mksglu/context-mode
/plugin install context-mode@context-mode
/plugin marketplace add thedotmack/claude-mem
/plugin install claude-mem
/plugin install frontend-design@claude-plugins-official
```

## The List

### 1. skill-creator

> `/plugin install skill-creator@claude-plugins-official`

A toolkit for building, testing, and refining Claude Code skills across a
structured development lifecycle. It offers four modes — **Create** (develop a new
skill from concept), **Eval** (test a skill against prompts), **Improve** (suggest
data-driven enhancements), and **Benchmark** (measure performance with
statistical/variance analysis) — backed by specialized agents that run, grade,
A/B-compare, and analyze skills. Reach for it when authoring skills and you want
to iterate rigorously and measure quality rather than guess.

### 2. superpowers

> `/plugin install superpowers@claude-plugins-official`

An agentic skills framework that gives Claude Code a complete, opinionated
software-development methodology built from composable skills. It adds structured
phases — Socratic brainstorming/design, detailed planning broken into small tasks,
test-driven (red-green-refactor) implementation, subagent-driven execution,
systematic debugging, and two-stage code review — that auto-trigger based on what
you ask. Use it to get more disciplined, higher-quality, verifiable results from
the agent instead of ad-hoc one-shot code. _(Created by Jesse Vincent / "obra"
and the community; accepted into the official Anthropic marketplace in Jan 2026.)_

### 3. get-shit-done-cc (GSD)

> `npx get-shit-done-cc --claude --global`

A spec-driven development and context-engineering system for Claude Code. It adds
a set of `/gsd:*` slash commands and a structured planning workflow that generates
project files like `PROJECT.md`, `REQUIREMENTS.md`, `ROADMAP.md`, `PLAN.md`, and
`STATE.md`. Its purpose is to combat "context rot" on long sessions by
orchestrating specialized research/planning/execution agents and breaking work
into atomic, verifiable tasks. _(The `--claude` flag targets the Claude Code
runtime; `--global` installs user-wide rather than per-project. Note: no longer
actively maintained, but still available on npm.)_

### 4. context-mode

> `/plugin marketplace add mksglu/context-mode`
> `/plugin install context-mode@context-mode`

A plugin that tackles context-window bloat by sandboxing large tool outputs
(claiming up to ~98% reduction — e.g. a 56 KB Playwright snapshot down to ~299
bytes) so raw data stays out of the conversation. It adds MCP tools for
code-driven analysis, a SQLite FTS5 knowledge base for searching docs without
loading full files, and SQLite-backed session tracking of edits, git ops, and
tasks so work survives conversation compaction. Useful for keeping sessions
efficient and continuous on large codebases or long-running tasks.

### 5. claude-mem

> `/plugin marketplace add thedotmack/claude-mem`
> `/plugin install claude-mem`

A persistent memory system for Claude Code. It captures what the agent does during
a session, compresses it with AI, and stores it in a searchable SQLite database,
then injects relevant context back into future sessions. Useful for long-running
projects so you don't have to re-explain prior work, decisions, or debugging
history each time you start a new session.

### 6. frontend-design

> `/plugin install frontend-design@claude-plugins-official`

A UI/UX design plugin from Anthropic's official marketplace that generates
distinctive, production-grade frontend code (React, Vue, Svelte). It pushes Claude
to commit to a deliberate aesthetic direction (brutalist, maximalist,
retro-futuristic, minimalist, etc.) with bold typography, color, and animation
choices. Useful for building polished interfaces that avoid generic "AI slop"
defaults like system fonts and predictable purple gradients.

# Agent Skills

A collection of distilled reference skills for AI coding agents. Each skill is a dense, structured knowledge base designed to be loaded on-demand — not read cover-to-cover.

## What's a Skill?

A skill is a self-contained reference that an AI agent can load when it needs domain knowledge. Each skill has:

- **`SKILL.md`** — Entry point: describes the skill, when to use it, and how chapters are organized
- **`chapters/`** — Individual topic files, loaded selectively based on the task at hand

Skills are optimized for token efficiency: dense bullets, no fluff, every line earns its place.

## Skills

| Skill | Source | Description |
|-------|--------|-------------|
| [software-engineering](./software-engineering/) | van Vliet, *Software Engineering* (2007) | 15 chapters of timeless SE principles — architecture, design, testing, maintenance, quality |

## The Book-to-Skill Pipeline

Many skills here are distilled from textbooks using a repeatable process:

1. **Convert** — PDF → markdown (via [pdf-to-markdown](https://github.com/Whamp/pdf-to-markdown))
2. **Split** — Markdown → individual chapters
3. **Distill** — Each chapter condensed by sub-agents into dense reference material
4. **Review** — Critical pass: what's timeless vs. what's dated?
5. **Refine** — Sub-agents trim, reframe, and tighten based on review
6. **Package** — Assemble as a skill with SKILL.md + chapter files

The goal isn't summarization — it's extraction of **timeless principles** that remain applicable regardless of who (or what) is writing the code.

## Usage

These skills are designed for [OpenClaw](https://github.com/openclaw/openclaw) agents but work with any system that can load markdown reference files. Copy a skill directory into your agent's skill path and reference it in your agent config.

## Contributing

Have a textbook that would make a good skill? The pipeline above is fully reproducible. PRs welcome.

## License

MIT

# AGENTS.md

Conventions for AI coding agents working in **about-me**. This file is the
canonical entry point under the [AGENTS.md](https://agents.md) standard, and it
is the first thing a Fredrin Worker reads.

It is a stub — the first ticket on the board fills it in.

## Project

A static, dark, one-page About Me site for Harsh Kasana (Forward Deployed Engineer). Plain HTML and CSS — no framework, no build step, no database, no analytics. Sections in order: intro, what-i-do, projects, contact.

Files: `index.html` (content), `style.css` (all styling).

## Commands

- **Preview:** open `index.html` directly in a browser, or serve it: `python3 -m http.server 8000` then visit http://localhost:8000.
- **Build:** none. **Tests:** none; verify with the project skill `.claude/skills/verify-about-me/SKILL.md`.

## Conventions

- Keep it dependency-free: no JS frameworks, no external fonts/icons/CDNs, no `<script>` unless truly needed. System font stack only.
- Colors live as CSS variables in `:root` of `style.css`; use the single mint accent (`--accent`) for links/highlights.
- Each section is a `<section id="intro|what-i-do|projects|contact">`; keep ids stable (the verification skill's feature map relies on them).
- ReacDEFI and JobOps intentionally have no links; only Hashtro links out.
- Must work when opened via `file://` — use relative asset paths only.

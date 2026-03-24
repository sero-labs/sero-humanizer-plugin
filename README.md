# @sero-ai/plugin-humanizer

Humanizer app for Sero — transform text with creative writing styles and remove
AI-generated patterns. Includes a comprehensive Pi skill based on Wikipedia's
"Signs of AI writing" guide.

## Sero Plugin Install

Install in **Sero → Admin → Plugins** with:

```text
git:https://github.com/monobyte/sero-humanizer-plugin.git
```

Sero clones the source repo, installs its dependencies locally, builds the UI,
and then hot-loads the plugin into the sidebar.

## Pi CLI Usage

Install as a Pi package:

```bash
pi install git:https://github.com/monobyte/sero-humanizer-plugin.git
```

The agent gains a `humanize` tool and a `/humanize` command, plus the
**humanizer skill** — a detailed writing-editor prompt that detects and fixes
AI writing patterns including inflated symbolism, promotional language, vague
attributions, em-dash overuse, rule of three, AI vocabulary, and more.

## Features

- **AI Pattern Detection** — identifies common AI writing tells
- **Style Transformation** — rewrites text to sound natural and human-written
- **History Tracking** — saves transformation history for review
- **Pi Skill** — comprehensive skill definition (`skills/humanizer/SKILL.md`)
  that teaches the agent to apply Wikipedia's AI-cleanup guidelines
- **Web UI** — visual editor with side-by-side original/transformed panes,
  style presets, and history panel

## Sero Usage

When loaded in Sero, the web UI mounts in the main app area. Paste or type
text, choose a writing style, and the agent transforms it using the humanizer
skill. Transformation history is persisted and visible in both the UI and via
the agent tool.

## State File

```
~/.sero-ui/
└── apps/
    └── humanizer/
        └── state.json
```

```json
{
  "history": [
    {
      "id": "abc123",
      "original": "The text delves into...",
      "humanized": "The text examines...",
      "style": "casual",
      "timestamp": "2026-01-01T00:00:00.000Z"
    }
  ]
}
```

## Skill

The plugin ships a Pi skill at `skills/humanizer/SKILL.md` (v2.2.0) that
covers:

- Inflated symbolism & promotion detection
- Superficial `-ing` analyses
- Vague attributions and weasel words
- Em-dash and semicolon overuse
- Rule-of-three and list padding
- AI vocabulary replacement (delve, tapestry, landscape, etc.)
- Negative parallelisms and excessive conjunctive phrases

The skill is auto-registered via `pi.skills: ["./skills"]` in `package.json`.

## Development

```bash
npm install
npm run dev         # Vite dev server (port 5192)
npm run build       # Production build → dist/ui/
npm run typecheck   # TypeScript check
```

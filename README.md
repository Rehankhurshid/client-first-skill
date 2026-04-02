# Client-First Skill

A skill for [Claude Code](https://claude.ai/claude-code) and Codex that gives the assistant deep knowledge of the **Finsweet Client-First** methodology for Webflow development.

When installed, the assistant automatically applies Client-First conventions when helping you build Webflow sites — class naming, page structure, spacing, typography, folders, variables, interactions, and accessibility.

## What's Covered

| Area | Details |
|------|---------|
| **Class Types** | Utility (no `_`), Custom (`_`), Global, Combo (`is-`) |
| **Naming Convention** | General-to-specific, human-readable, no abbreviations |
| **Core Structure** | `page-wrapper` > `main-wrapper` > `section_` > `padding-global` > `container-` |
| **Folders** | Underscore = folder, nested folders, `_component` keyword |
| **Typography** | HTML tag defaults, `text-size-`, `heading-style-`, `text-weight-` |
| **Spacing** | Spacer blocks, spacing wrappers, direction + size, CSS grid |
| **Sizes & Rem** | All rem, 1rem = 16px, clean values only |
| **Variables** | Color only — primitive + semantic tokens |
| **Buttons** | Base + `is-` combo pattern |
| **Utility Classes** | hide, max-width, icons, z-index, layer, overflow, aspect-ratio |
| **Deep Stacking** | Max 2 preferred, 4 absolute max |
| **Layout** | Custom classes for flex/grid (no utility layout system) |
| **Interactions** | `Element [Action State]` naming |
| **Semantic HTML** | Proper tags on every element |
| **Accessibility** | rem units, semantic tags, heading hierarchy, ARIA |

## Install

### Claude Code

```bash
claude skill add Rehankhurshid/client-first-skill
```

### Codex

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo Rehankhurshid/client-first-skill \
  --path . \
  --name client-first \
  --method git
```

Restart Codex after installing so it picks up the new skill.

## Source

Based on the official [Client-First documentation](https://finsweet.com/client-first/docs) by Finsweet.

## License

MIT

# Lightweight Infographic

Turn a product or workflow into a clear, illustrated explanation for a GitHub README, a presentation, or an onboarding guide.

![Codex Skill](https://img.shields.io/badge/Codex-Skill-18202A)
![Formats](https://img.shields.io/badge/Output-PNG%20%2F%20SVG-5086B1)

**English** | [简体中文](README.zh-CN.md) | [日本語](README.ja.md)

## What this is

A reusable Codex skill for lightweight infographics: short labels, small illustrations that explain the content, soft colors, and clear connections. It helps readers understand how something works without reading a dense technical diagram.

Use it for:

- **GitHub repositories:** a simple “How it works” image showing inputs, key steps, and outcomes.
- **PPT presentations:** a compact architecture overview or product workflow that fits on one slide.
- **Product documentation:** onboarding, feature explanations, and quick-start illustrations.

The visual language stays consistent; the layout, icons, number of steps, and relationships adapt to the subject. It is not a full architecture specification or a fixed poster template.

## Skill

| Entry | Purpose |
|---|---|
| [`lightweight-infographic`](skills/lightweight-infographic/SKILL.md) | Plan, draw, export, and check a lightweight explanatory infographic |
| [`agents/openai.yaml`](skills/lightweight-infographic/agents/openai.yaml) | Codex display metadata and default invocation prompt |

The skill instructions are in Chinese. It supports diagrams in the language requested by the user; these three READMEs are localized guides, not three separate skills.

## Example prompts

```text
Use $lightweight-infographic to explain how this repository works.
Read the README and relevant code, keep the main flow easy to follow,
and deliver a PNG plus an editable SVG for the README.
```

```text
Use $lightweight-infographic to turn this system description into a
simple architecture overview for a 16:9 PPT slide. Show the user,
service, and data store relationships. Deliver an image I can insert.
```

```text
Use $lightweight-infographic to create English, Chinese, and Japanese
versions of this onboarding flow. Adjust line breaks for each language.
Include a QR code pointing to the URL I provide and verify the exported code.
```

## Features

- Content-led structure: often 3–5 steps for a sequence, or layers and branches when the subject needs them.
- Small interface illustrations explain actions; typography and restrained color establish hierarchy.
- Actual sources determine facts and arrows; visual references determine style only.
- PNG for display, genuine editable SVG when requested; native editable PPTX requires suitable presentation tooling.
- QR codes are optional, generated from real URLs, and decoded from the final export before being reported as verified.
- Rendering checks cover readability, overflow, connections, multilingual layout, and requested editability.

## Visual reference

[See an earlier “How it works” infographic](https://github.com/tsetsugekka/codex-market-skills/blob/main/assets/how-it-works.en.svg) that informed this style. Reuse its clarity and lightness, not its project-specific labels, icons, or QR destination.

## Recommended layout

```text
README.md
README.zh-CN.md
README.ja.md
skills/
  lightweight-infographic/
    SKILL.md
    agents/openai.yaml
```

The installable skill contains only instructions and UI metadata. No API key or fixed rendering service is required; actual exports depend on the tools available in the current environment.

## Installation and usage

Copy the skill into your global Codex skills directory. If a skill with the same name already exists, compare it before replacing it.

```sh
git clone https://github.com/tsetsugekka/lightweight-infographic-skill.git
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
cp -R lightweight-infographic-skill/skills/lightweight-infographic "${CODEX_HOME:-$HOME/.codex}/skills/"
```

Start a new Codex task so it can discover the installed skill, then invoke `$lightweight-infographic` with the content to explain. Provide a target size, language, or format when you have a preference. For native editable PPTX, explicitly request it and use an environment with presentation tooling.

## Security rules

Only publish approved content. Keep credentials, private paths, and personal metadata out of exported files. Creating a diagram does not itself authorize publishing a repository, replacing documentation, or deleting earlier artwork.

## Limitations

This is an instruction package, not a standalone renderer. It does not guarantee a product's behavior, a working QR code without a decode check, or editable slide objects from a flattened image. The agent must report any checks it could not perform.

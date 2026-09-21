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

## Example gallery

Two real project examples show how the same visual language adapts to different subjects. Click an image to view the original.

### SignalScout TV · Product workflow

From collecting live-stream sources to organizing channels, checking connections, and playback: small interface illustrations make each step concrete. The original diagram is in Chinese.

[![SignalScout TV workflow: source collection, channel organization, browser checks, and playback](https://raw.githubusercontent.com/tsetsugekka/signalscout-tv/main/public/architecture.png)](https://github.com/tsetsugekka/signalscout-tv/blob/main/public/architecture.png)

[Explore SignalScout TV →](https://github.com/tsetsugekka/signalscout-tv)

### Codex Market Skills · Research workflow

A question becomes a research result through skill selection and evidence checks. Supporting methods sit below the main flow so the overview stays easy to scan.

[![Codex Market Skills workflow: ask a question, match skills, check evidence, and deliver results](https://raw.githubusercontent.com/tsetsugekka/codex-market-skills/main/assets/how-it-works.en.svg)](https://github.com/tsetsugekka/codex-market-skills/blob/main/assets/how-it-works.en.svg)

[Explore Codex Market Skills →](https://github.com/tsetsugekka/codex-market-skills)

These earlier examples informed the skill's visual language. New diagrams adapt the structure, illustrations, and labels to their own content.

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

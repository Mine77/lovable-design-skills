<div align="center">

# Lovable Design Skills

**A portable, Lovable-inspired design taste layer for AI coding agents.**

Turn generic AI-generated UIs into distinctive, production-grade frontend design.

[![Install with Skills](https://img.shields.io/badge/install-npx%20skills%20add-blue)](#quick-start)
[![Skill](https://img.shields.io/badge/agent--skill-lovable--design--system-111827)](skills/lovable-design-system/SKILL.md)
[![Language](https://img.shields.io/badge/content-English%20%2B%20中文-green)](#中文说明)

</div>

## Why this exists

Most AI-built frontend work converges to the same look: Inter, purple gradients, centered hero, three cards, generic SaaS polish.

`lovable-design-system` gives your coding agent a stronger design brief before it writes UI code:

- bold aesthetic direction instead of safe defaults
- curated palettes, typography pairs, and layout archetypes
- a repeatable decision flow for choosing visual direction
- a `styleguide.md` contract that keeps taste stable across future work
- implementation rules for semantic design tokens, Tailwind/CSS variables, and visual QA

It is useful for landing pages, marketing sites, portfolios, dashboards, product pages, and any UI where “make it look good” is not enough.

> [!NOTE]
> This is an unofficial skill inspired by Lovable-style frontend generation workflows. It is not affiliated with, endorsed by, or maintained by Lovable.

## Showcase

The examples below are real HTML pages included in this repository and captured with Playwright. They demonstrate the range of visual directions this skill can guide an agent toward.

| Noir & Gold / Editorial | Neon Mint / Product Bento |
| --- | --- |
| ![Noir & Gold editorial layout](assets/readme/noir-gold-editorial.png) | ![Neon Mint product bento layout](assets/readme/neon-mint-product.png) |
| Paper & Ink / Portfolio Gallery | Terracotta & Sage / Split Screen |
| ![Paper & Ink portfolio gallery layout](assets/readme/paper-ink-portfolio.png) | ![Terracotta & Sage wellness split-screen layout](assets/readme/terracotta-sage-wellness.png) |
| Brutalist Pop / Event Schedule | Ocean Deep / Enterprise Dashboard |
| ![Brutalist Pop event schedule layout](assets/readme/brutalist-pop-event.png) | ![Ocean Deep enterprise dashboard layout](assets/readme/ocean-deep-enterprise.png) |

## What the skill provides

- **Design philosophy** — opinionated rules for avoiding generic AI aesthetics
- **26 palette presets** — named color systems with domain hints
- **15 typography pairs** — display/body font combinations with distinct vibes
- **15 layout archetypes** — composition patterns beyond the default centered hero
- **Interaction flows** — when to ask users for visual direction and when to build directly
- **Redesign workflow** — generate and compare multiple rendered design directions
- **Style persistence** — save selected visual choices into `styleguide.md`
- **Implementation constraints** — semantic tokens, Tailwind/CSS variables, contrast, SEO defaults

## Quick start

### Install the skill

```sh
npx skills add Mine77/lovable-design-skills
```

### Ask your agent to use it

```text
Use the lovable-design-system skill to redesign this landing page.
```

or:

```text
Use the lovable-design-system skill. Pick a bold visual direction and rebuild this dashboard so it does not look like a generic AI SaaS page.
```

## Repository structure

```text
skills/lovable-design-system/SKILL.md       # main agent skill
skills/lovable-design-system/references/   # palettes, fonts, layouts, flows
showcase/                                  # standalone HTML examples
assets/readme/                             # screenshots for the README
```

## Good prompts to try

```text
Use lovable-design-system to create three distinct visual directions for this product homepage before coding.
```

```text
Use lovable-design-system to redesign this portfolio with a strong editorial visual identity. Persist the direction into styleguide.md.
```

```text
Use lovable-design-system to improve this dashboard UI. Avoid generic AI aesthetics and use semantic design tokens only.
```

## Who should use this

- builders using AI coding agents for frontend work
- designers who want more consistent taste from coding agents
- teams building landing pages, product sites, dashboards, or portfolios
- anyone tired of the same purple-gradient AI UI template

## 中文说明

这个仓库把 Lovable 风格前端生成背后的设计指导整理成一个可复用的 Agent Skill。它封装了提示词层面的设计哲学、精选的配色 / 字体 / 布局预设、帮助 Agent 避免通用 AI 味道的交互流程，以及把用户审美选择固化到本地 `styleguide.md` 的工作方式。

### 它能做什么

`lovable-design-system` 会在编码 Agent 编写界面代码之前，为它提供更强的设计简报：

- 设计品味：大胆、非模板化的前端设计理念
- 视觉预设：26 套配色、15 组字体搭配、15 种布局原型
- 决策流程：判断何时询问视觉偏好、何时直接开始构建
- 重设计流程：生成并应用多个设计方向
- 风格固化：将用户选定的审美方向写入本地 `styleguide.md`
- 实现约束：基于 Tailwind / CSS 变量的设计令牌建议，以及基础 SEO 默认规则

### 安装

```sh
npx skills add Mine77/lovable-design-skills
```

### 使用

```text
使用 lovable-design-system 技能重设计这个落地页。
```

## Contributing

Ideas, examples, new layout archetypes, and better design-direction workflows are welcome. If you build a great UI with this skill, consider sharing a screenshot or opening a PR.

## Acknowledgements

This project organizes Lovable-inspired design prompting patterns into a framework-agnostic reference system that can be used by different coding agents.

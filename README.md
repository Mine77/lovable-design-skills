<div align="center">

# Lovable 设计系统技能

**一个可移植的、受 Lovable 启发的 Agent 前端设计品味层。**

</div>

这个仓库把 Lovable 风格前端生成背后的设计指导整理成一个可复用的 Agent Skill。它封装了提示词层面的设计哲学、精选的配色 / 字体 / 布局预设、帮助 Agent 避免通用 AI 味道的交互流程，以及把用户审美选择固化到本地 `styleguide.md` 的工作方式。

> [!NOTE]
> 这是一个非官方技能，不隶属于 Lovable，也未获得 Lovable 的认可或维护。

## Showcase

下面 6 张图来自仓库里的真实 HTML 页面，并通过 Playwright 截图生成。它们不是 AI 生成的 mockup，而是这个 Skill 可以指导 Agent 落地的不同 layout 和视觉方向示例。

| Noir & Gold / 编辑杂志 | Neon Mint / 产品 Bento |
| --- | --- |
| ![Noir & Gold 编辑杂志布局](assets/readme/noir-gold-editorial.png) | ![Neon Mint 产品 Bento 布局](assets/readme/neon-mint-product.png) |
| Paper & Ink / 作品集 Gallery | Terracotta & Sage / Split Screen |
| ![Paper & Ink 作品集 Gallery 布局](assets/readme/paper-ink-portfolio.png) | ![Terracotta & Sage 健康品牌 Split Screen 布局](assets/readme/terracotta-sage-wellness.png) |
| Brutalist Pop / 活动 Schedule | Ocean Deep / Enterprise Dashboard |
| ![Brutalist Pop 活动 Schedule 布局](assets/readme/brutalist-pop-event.png) | ![Ocean Deep Enterprise Dashboard 布局](assets/readme/ocean-deep-enterprise.png) |

## 它能做什么

`lovable-design-system` 会在编码 Agent 编写界面代码之前，为它提供更强的设计简报：

| 能力 | 技能提供的内容 |
| --- | --- |
| 设计品味 | 面向大胆、非模板化前端设计的清晰理念 |
| 视觉预设 | 26 套配色、15 组字体搭配、15 种布局原型 |
| 决策流程 | 判断何时询问视觉偏好、何时直接开始构建的规则 |
| 图片预览 | 在支持图片生成的环境中，为视觉选项生成 UI mockup 预览 |
| 重设计流程 | 生成并应用设计方向的结构化流程 |
| 风格固化 | 将用户选定的审美方向写入本地 `styleguide.md`，后续直接复用 |
| 实现约束 | 基于 Tailwind / CSS 变量的设计令牌建议，以及基础 SEO 默认规则 |

当你在构建或优化落地页、营销网站、作品集、产品界面、仪表盘，以及其他对视觉质量有要求的前端体验时，可以使用它。

## 快速开始

使用 Skills CLI 从本仓库安装技能：

```sh
npx skills add https://github.com/Mine77/lovable-design-skills --skill lovable-design-system
```

也可以在仓库发布前，从本地路径验证或安装：

```sh
npx skills add . --skill lovable-design-system
```

如果你想安装到 Codex 的全局技能目录，可以指定 Agent：

```sh
npx skills add https://github.com/Mine77/lovable-design-skills --skill lovable-design-system -a codex -g
```

然后在设计界面时让 Agent 使用这个 Skill：

```text
使用 lovable-design-system 技能重设计这个落地页。
```

## 目录内容

```text
assets/
└── readme/
    ├── brutalist-pop-event.png
    ├── neon-mint-product.png
    ├── noir-gold-editorial.png
    ├── ocean-deep-enterprise.png
    ├── paper-ink-portfolio.png
    └── terracotta-sage-wellness.png
showcase/
├── brutalist-pop-event.html
├── neon-mint-product.html
├── noir-gold-editorial.html
├── ocean-deep-enterprise.html
├── paper-ink-portfolio.html
└── terracotta-sage-wellness.html
skills/
└── lovable-design-system/
    ├── SKILL.md
    └── references/
        ├── ask-questions-flow.md
        ├── design-directions-flow.md
        ├── font-pairs.md
        ├── layout-archetypes.md
        ├── palette-presets.md
        └── styleguide-persistence.md
```

### `SKILL.md`

Agent 的入口文件。它定义了核心设计理念、需要避免的通用默认风格、实现规则、SEO 默认规则，以及完整的决策循环。

### `references/palette-presets.md`

精选的 26 套四色配色库，按情绪和使用场景分组：深色精致、轻盈明亮、自然 earthy、冷静舒缓、高能活力、浪漫、季节感、实验性和权威感等。

### `references/font-pairs.md`

15 组 Google Fonts 字体搭配，组合方式是有辨识度的标题字体加易读的正文字体。每组都包含适合的产品或页面类型说明。

### `references/layout-archetypes.md`

15 种布局结构，从主视觉网格、Bento 网格，到仪表盘、杂志、信息流、画廊和破格网格等。

### `references/ask-questions-flow.md`

当用户没有提供明确设计方向时，向用户询问视觉偏好的精确流程。它会让 Agent 聚焦在三个具体选择上：配色、字体和布局。

### `references/design-directions-flow.md`

用于改进现有界面的重设计工作流。它先锁定用户的审美偏好，再生成三个不同的可视化方向，最后进入实现。

### `references/styleguide-persistence.md`

用于把用户选中的配色、字体、布局、动效强度和组件处理方式写入项目根目录的 `styleguide.md`。如果项目已经存在这个文件，后续 UI 工作会优先读取它。

## Agent 如何使用它

这个技能遵循一个简单循环：

1. 判断用户请求是否涉及视觉设计，以及设计方向是否已经明确。
2. 如果项目根目录已有 `styleguide.md`，优先读取并沿用。
3. 如果用户已经给出方向，就按该方向构建。
4. 如果方向缺失，就询问配色、字体和布局三个视觉选择。
5. 如果运行环境支持图片生成，就按候选视觉方向生成预览图，帮助用户选择。
6. 将选中的预设转换成具体的创意简报，并尽量写入本地 `styleguide.md`。
7. 使用语义化设计令牌，而不是一次性的原始颜色类。
8. 进行视觉质量检查，拒绝通用 AI 风格的输出。

目标是让生成结果少一点「默认 SaaS 模板」味道，多一点明确的艺术指导：更有力量的字体、更清晰的构图、更大胆的色彩，以及真正贴合产品气质的界面。

## 适合场景

- 前端设计系统
- 落地页和营销网站
- 作品集和编辑型页面
- 产品仪表盘和 SaaS 界面
- UI 重设计、视觉打磨和设计方向探索
- 需要在多个项目中复用审美标准的 Agent

## 不包含什么

- 特定项目的设计令牌、组件或品牌规范
- 面向某个具体框架的运行时脚手架
- 专有素材、图片、Logo 或字体
- 对人类设计判断的替代

## 设计原则

- 坚持一个明确且大胆的审美方向。
- 避免紫色渐变、居中英雄区卡片、未改造的 shadcn 默认样式等通用 AI 默认风格。
- 使用语义化令牌管理颜色、渐变、阴影和主题值。
- 将有表现力的标题字体与易读的正文字体搭配。
- 有意识地做布局决策，而不是依赖习惯。
- 只有在视觉偏好会明显改善结果时，才向用户提问。
- 选定视觉方向后，用 `styleguide.md` 固化下来，减少后续漂移。

## 致谢

本项目基于受 Lovable 启发的设计提示词模式整理而成，并进一步组织为一个与具体框架无关的 Agent 参考系统。

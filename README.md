<div align="center">

# Lovable 设计系统技能

**一个可移植的、受 Lovable 启发的 Agent 前端设计品味层。**

让 AI coding agent 写前端时，少一点模板味，多一点真正的设计方向。

[English README](README.en.md)

[![Install with Skills](https://img.shields.io/badge/install-npx%20skills%20add-blue)](#快速开始)
[![Skill](https://img.shields.io/badge/agent--skill-lovable--design--system-111827)](skills/lovable-design-system/SKILL.md)

</div>

## 为什么做这个

很多 AI 生成的前端界面最后都会长得很像：Inter 字体、紫色渐变、居中 hero、三张功能卡片、标准 SaaS 风格。

`lovable-design-system` 的目标，是在 Agent 写 UI 代码之前，先给它一个更强的设计简报：

- 用明确、大胆的审美方向替代安全但普通的默认值
- 提供可复用的配色、字体和布局预设
- 给 Agent 一套判断“什么时候该问用户视觉偏好、什么时候直接开工”的流程
- 把选定的审美方向沉淀到 `styleguide.md`，后续持续复用
- 用语义化设计令牌、Tailwind / CSS 变量和视觉 QA 约束实现质量

它适合用在落地页、营销网站、作品集、产品页、仪表盘，以及任何不能只满足于“能看”的前端界面。

> [!NOTE]
> 这是一个受 Lovable 风格前端生成工作流启发的非官方技能，不隶属于 Lovable，也未获得 Lovable 的认可或维护。

## Showcase

下面 6 张图来自仓库里的真实 HTML 页面，并通过 Playwright 截图生成。它们不是 AI 生成的 mockup，而是这个 Skill 可以指导 Agent 落地的不同视觉方向示例。

| Noir & Gold / 编辑杂志 | Neon Mint / 产品 Bento |
| --- | --- |
| ![Noir & Gold 编辑杂志布局](assets/readme/noir-gold-editorial.png) | ![Neon Mint 产品 Bento 布局](assets/readme/neon-mint-product.png) |
| Paper & Ink / 作品集 Gallery | Terracotta & Sage / Split Screen |
| ![Paper & Ink 作品集 Gallery 布局](assets/readme/paper-ink-portfolio.png) | ![Terracotta & Sage 健康品牌 Split Screen 布局](assets/readme/terracotta-sage-wellness.png) |
| Brutalist Pop / 活动 Schedule | Ocean Deep / Enterprise Dashboard |
| ![Brutalist Pop 活动 Schedule 布局](assets/readme/brutalist-pop-event.png) | ![Ocean Deep Enterprise Dashboard 布局](assets/readme/ocean-deep-enterprise.png) |

## 它能做什么

`lovable-design-system` 会在编码 Agent 编写界面代码之前，为它提供更强的设计简报：

- **设计哲学**：避免通用 AI 审美的明确规则
- **26 套配色预设**：带命名、色值和适用场景提示
- **15 组字体搭配**：标题字体 + 正文字体组合，以及对应气质
- **15 种布局原型**：跳出默认居中 hero 和三卡片结构
- **交互流程**：判断何时询问用户视觉偏好，何时直接开始构建
- **重设计流程**：生成并比较多个设计方向
- **风格固化**：把用户选择写入 `styleguide.md`
- **实现约束**：语义化 token、Tailwind / CSS 变量、对比度、基础 SEO 默认规则

## 快速开始

### 安装技能

```sh
npx skills add Mine77/lovable-design-skills
```

### 使用技能

安装后，在设计界面时让 Agent 使用这个 Skill：

```text
使用 lovable-design-system 技能重设计这个落地页。
```

也可以这样写：

```text
使用 lovable-design-system 技能。选择一个大胆的视觉方向，重做这个 dashboard，让它不要看起来像普通 AI SaaS 页面。
```

## 仓库结构

```text
skills/lovable-design-system/SKILL.md       # 主 Agent Skill
skills/lovable-design-system/references/   # 配色、字体、布局和流程参考
showcase/                                  # 独立 HTML 示例页面
assets/readme/                             # README 截图素材
```

## 可以直接试的 Prompt

```text
使用 lovable-design-system，为这个产品首页先生成三个不同的视觉方向，再开始写代码。
```

```text
使用 lovable-design-system，用更强的编辑杂志风格重设计这个作品集，并把方向保存到 styleguide.md。
```

```text
使用 lovable-design-system 优化这个 dashboard UI。避免通用 AI 审美，只使用语义化设计 token。
```

## 适合谁用

- 用 AI coding agent 写前端的 builder
- 想让 Agent 生成更稳定审美结果的设计师
- 正在做落地页、产品网站、仪表盘、作品集的团队
- 受够了紫色渐变 AI SaaS 模板的人

## 贡献

欢迎提交新的视觉示例、layout archetype、配色组合、字体组合，或者更好的设计方向工作流。如果你用这个 Skill 做出了不错的界面，也欢迎分享截图或开 PR。

## 致谢

本项目基于受 Lovable 启发的设计提示词模式整理而成，并进一步组织为一个与具体框架无关的 Agent 参考系统。

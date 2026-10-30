---
name: de-ai-ui
description: >-
  UI 设计去 AI 味 / De-AI-ify UI. Use when building, reviewing, or polishing any
  web/app UI, landing page, dashboard, component, or design-system tokens with an
  AI agent ("vibe coding"), or when the user says a UI looks AI-generated, cheap,
  廉价, 有 AI 味, slop, generic, or asks to make it more refined / 精致 / 有质感 /
  高级. Gives checkable rules (nested radius r = R − p, superellipse corners,
  0.5px hairlines, ≤4 font sizes ≥12px, Radix Colors, grayscale chrome with color
  reserved for content, CJK font-family stacks), an AI-slop self-audit checklist,
  a before/while/after workflow, and copy-paste prompts. Rules are summarized
  from public posts by Chinese-speaking designers (sources cited in references/sources.md).
---

# UI 设计去 AI 味（De-AI UI）

> vibe 出来的界面一眼廉价，往往输在细节上。—— [@bruc3van](https://x.com/bruc3van/status/2115963644811116732)

本 Skill 把 8 位中文设计师在 X 上公开分享的"AI 界面哪里露馅、该怎么跟 AI 说"整理成**可执行、可检查**的规则。每条规则后面的 `[作者]` 标注出处，详细原文摘要与链接见 [`references/sources.md`](references/sources.md)。标注 `[通用实践]` 的是为了把规则串起来而补充的常识，不代表任何来源作者的观点。

## 何时使用 / When to use

- 用 AI 新建或修改任何界面：落地页、后台、仪表盘、设置页、组件库、设计 token。
- 用户说"看起来像 AI 做的 / 廉价 / 没质感 / 有 AI 味 / slop"，或要求"精致一点、高级一点"。
- 交付 UI 前的自查（review pass）。

## 核心原则 / Core principles

1. **做减法优先于做加法。** AI 最常见的失败不是"少了什么"，而是"多了什么"：多余的说明文字、分割线、图标、标签、阴影、颜色、动效。对每个元素问一句"它真的有存在的必要吗？" [ZaynHao] [dingyi] [yanliudreamer]
2. **界面退后，内容出彩。** 界面本身只用黑白灰，把颜色留给照片和内容。[ianneo_ai]
3. **一致性靠系统，不靠手感。** 颜色用成套 token（Radix Colors），间距/圆角走 4px 网格，字号控制在少数几档，组件复用现有库和设计系统。[ZaynHao] [Kubai087] [yanliudreamer]
4. **细节要"几何正确"。** 嵌套圆角同心、光学对齐、边框粗细统一。[Kubai087] [ZaynHao] [dingyi]
5. **先定义，再动手；先全貌，再逐块改。** 先写清给谁用、解决什么问题、要什么感觉；出完整一版后列问题、排优先级、每轮只改一处。[Xian0063]
6. **不同模式要单独设计，而不是自动转换。** 苹果给 Preview 图标的 Clear 模式单独加了图层，因为直接把默认模式图片转换过去"会显得很脏"。深色/夜间/透明模式同理。[remixdesigner] [ianneo_ai]

## 可检查的硬规则 / Checkable rules

### 圆角与边框（详见 [`references/radius-and-borders.md`](references/radius-and-borders.md)）

- [ ] **嵌套圆角：内圆角 = 外圆角 − 间距（r = R − p）**，内外共用一个圆心；从外往里推：dialog/card → panel、input、button → chip、tag。例：dialog 32、padding 16 → 内部 16；16 的 panel 里 padding 8 的 chip → 8。[Kubai087]
- [ ] 同一层级的盒子用同一个圆角；最小不低于 4px；pill 与圆形保持全圆。[Kubai087]
- [ ] padding、gap、radius 都落在 **4px 网格**上；有 radius token 就改 token，不要硬编码。[Kubai087]
- [ ] **连续圆角（超椭圆）** 作为渐进增强：保留 `border-radius`，再用 `@supports (corner-shape: superellipse(1.25))` 加 `corner-shape`；pill/圆形设 `corner-shape: round`。Chrome/Edge 139+ 生效，Safari/Firefox 自动回退普通圆角。[Kubai087]
- [ ] 线条与边框用 **0.5px**，并且全站粗细统一（"该用 0.5px 的地方用了 1px" 是 slop 特征）。[ZaynHao] [dingyi] —— 注意：ZaynHao 自己说明这是偏个人经验的提示，没有专门考虑低分屏/老设备，需要兼容时请做回退（见参考文件）。
- [ ] 不要随意加圆角和阴影；**禁止卡片左边缘的彩色竖线**。确需圆角/阴影时，数值要符合功能场景。[ZaynHao] [dingyi]
- [ ] 不要叠加过多细节：分割线、多层阴影、半透明叠色、带边框的容器、卡片套卡片。[dingyi] [Xian0063]

### 颜色（详见 [`references/color.md`](references/color.md)）

- [ ] **界面 chrome（按钮、卡片、输入框）默认只用黑白灰**，颜色留给照片、插画、数据等内容。[ianneo_ai]
- [ ] 所有颜色换成 **Radix UI Colors**，并按其 12 级色阶的用途定义来使用。[ZaynHao]（各级对应背景 / 组件 / 边框 / 实色 / 文字，见 Radix 官方文档 `[通用实践]`）
- [ ] 为产品挑 **3–5 个**有辨识度的颜色定基调（可从喜欢的网站/应用里取色，例如他的应用背景 `#f6f4f0`）。[ZaynHao]
- [ ] 不要：紫色/紫蓝渐变、渐变按钮、彩色图标、一张卡片一个颜色、单独染色的某一个字。[dingyi] [Xian0063] [ianneo_ai]

### 字体与排版（详见 [`references/typography-cjk.md`](references/typography-cjk.md)）

- [ ] **字号不超过 4 种，最好 3 种；最小 12px。** 层级不够时用字重、颜色、间距来区分，而不是加字号。[ZaynHao] [dingyi]
- [ ] hero 区标题不要大得离谱；不要全大写小标题、标题上方的小眉标（eyebrow）、章节编号、代码式面包屑。[dingyi] [Xian0063]
- [ ] 避开被用烂的三款字体：**Instrument Serif、Space Grotesk、Bricolage Grotesque**；不要滥用等宽字体和斜体。[dingyi]
- [ ] **中文 font-family：先西后中，兼顾主流系统，最后 `sans-serif` 兜底**；中文字体写英文名；带空格的名字加双引号。现成写法见参考文件。[ricouii]
- [ ] 不要默认全部居中排版。[Xian0063]

### 文案与内容（详见 [`references/copy-and-content.md`](references/copy-and-content.md)）

- [ ] **不要用中点 "·" 当分隔符**，有就移除。[ZaynHao] [dingyi]
- [ ] 不要加冗余的解释性描述文字；正文不塞 Emoji，标题上不顶 emoji 图标。[ZaynHao] [dingyi] [Xian0063]
- [ ] 文案贴合目标人群：易懂但不过度口语化，长短匹配功能场景，**不随意造词**。[ZaynHao] [dingyi]
- [ ] 不编造数据与社会证明（如"10,000+ 满意客户"），不在结尾硬塞订阅框。[Xian0063 转述 Hallmark 的检查项]
- [ ] 图表别做得"超详细"；到处都是标签（tag/badge）也是 slop 特征。[dingyi]

### 动效与交互（详见 [`references/motion-and-interaction.md`](references/motion-and-interaction.md)）

- [ ] 尽量减少过渡动画；必须加时，基础设定 **ease-out、约 250ms**。滚动动效不要多，过渡要收敛。[ZaynHao] [dingyi]
- [ ] 进场用 ease-out 而不是 ease-in；下拉菜单从触发按钮的位置长出、从 0.96 缩放开始而不是 0；按钮按下缩到 0.97；toast 叠成一摞不挤内容；长名字截断、大数字缩写。[Xian0063 转述 Emil Kowalski Skills]
- [ ] 减少需要用户停下来判断的交互；必须有时，放在用户本来就打算做选择的地方，并重新排信息优先级。[ZaynHao]
- [ ] **下拉菜单按钮的下拉小图标**要专门修——dingyi 认为这是清单里"最严重"、几乎没人修的细节。[dingyi]

### 组件、资源与图标（详见 [`references/libraries-and-skills.md`](references/libraries-and-skills.md)、[`references/icons-and-detail.md`](references/icons-and-detail.md)）

- [ ] 优先复用项目已有组件库 / 设计系统和 token，不重复造轮子；参考成熟产品已验证的 UX 模式。[yanliudreamer] [Kubai087]
- [ ] 一整套界面里的图标来自**同一个风格体系**，线条粗细、圆角、比例、视觉重量一致（例如 Remix Icon）。[yanliudreamer] [Kubai087]
- [ ] 深色 / 夜间 / Clear 等模式的素材单独处理，不要直接滤镜转换。[remixdesigner] [ianneo_ai]

## 工作流 / Workflow

**1. 动手前（Before coding）**
- 写清楚：给谁用、解决什么问题、要给人什么感觉。说不清就先向用户提问，这一步不出设计。[Xian0063]
- 读项目现有的组件库、design tokens（颜色 / 圆角 / 间距 / 字号）；有就基于它改，没有就先建一套最小 token（见 [`examples/tokens.css`](examples/tokens.css)）。
- 定视觉规则：3–5 个品牌色 + Radix 灰阶、≤4 档字号、4px 网格、圆角层级、0.5px 边框、中文字体栈。[ZaynHao] [Kubai087] [ricouii]

**2. 编码中（While coding）**
- 每加一个元素先问"能不能不要"：说明文字、分割线、图标、badge、阴影、颜色。[yanliudreamer] [ZaynHao]
- 先出完整页面全貌，而不是局部修补。[Xian0063] [yanliudreamer]
- 复杂视觉方向可一次出 3–4 个方案对比，避免"原型引力"（已经在代码里投入太多就只沿着现方案优化）。[yanliudreamer]

**3. 自查（Review pass）**
- 逐条过 [`references/slop-checklist.md`](references/slop-checklist.md)，记录命中项。
- 按重要程度排序，**每轮只改一处**，确认后再改下一处。[Xian0063]
- 改圆角时按 Kubai087 的要求输出 `element: old -> new` 变更清单。
- 在至少 3 种宽度下截图检查（Taste Skill 的自查方式，[Xian0063] 转述），并检查深色模式。
- 给反馈时用"目标"而不是"像素"：在截图上标问题、说想要的效果，具体数值让 AI 算。[Xian0063]

## 可直接复制给 AI 的提示词 / Copy-paste prompts

完整版（含 Kubai087 的英文原版 prompt、ZaynHao 的 10 条提示词）见 [`references/prompts.md`](references/prompts.md)。最常用的一段合并版：

```text
请按"去 AI 味"规则重做这个界面，只改我指定的页面/组件；项目已有 token 或组件库时改 token、复用组件，不要硬编码：
1. 界面 chrome 只用黑白灰，颜色留给照片和内容；所有颜色换成 Radix UI Colors 并按其 12 级用途使用。不要紫色渐变、渐变按钮、彩色图标、卡片左侧彩色竖线。
2. 字号最多 4 种（最好 3 种），最小 12px；层级不够用字重、颜色、间距解决。不要全大写小标题、标题上方小眉标、超大 hero 字。
3. 嵌套圆角满足 内圆角 = 外圆角 − 间距，同层同圆角，最小 4px，pill/圆形保持全圆；padding/gap/radius 都在 4px 网格上。用 @supports 给 corner-shape: superellipse(1.25) 做渐进增强。
4. 线条和边框统一 0.5px；去掉多余的分割线、多层阴影、半透明叠色、带边框的容器和卡片套卡片。
5. 去掉中点 "·" 分隔符、冗余解释文字、正文 Emoji；文案贴合目标用户，不口语化、不造词。
6. 动效尽量少，必须时用 ease-out 约 250ms。
7. 中文字体栈先西后中、最后 sans-serif 兜底。
完成后列出你改了什么（element: old -> new），以及哪些 slop 特征已消除。
```

单句版（来自 [ianneo_ai]）：`界面只用黑白灰，颜色留给照片和内容。`

## 参考文件 / References

| 文件 | 内容 |
| --- | --- |
| [`references/sources.md`](references/sources.md) | 8 位设计师 + @bruc3van 原帖链接与要点摘要 |
| [`references/slop-checklist.md`](references/slop-checklist.md) | AI slop 自查清单（可逐项打勾） |
| [`references/radius-and-borders.md`](references/radius-and-borders.md) | 圆角公式、超椭圆、0.5px 边框与回退 |
| [`references/color.md`](references/color.md) | 黑白灰 + Radix Colors 用法 |
| [`references/typography-cjk.md`](references/typography-cjk.md) | 字号层级、slop 字体、中文 font-family |
| [`references/copy-and-content.md`](references/copy-and-content.md) | 文案与内容规则 |
| [`references/motion-and-interaction.md`](references/motion-and-interaction.md) | 动效参数与交互细节（含级联菜单、拖拽排序、拟物按钮） |
| [`references/icons-and-detail.md`](references/icons-and-detail.md) | 图标一致性、多模式素材 |
| [`references/libraries-and-skills.md`](references/libraries-and-skills.md) | 推荐资源库与 5 个 AI 设计 Skill |
| [`references/prompts.md`](references/prompts.md) | 全部可复制 Prompt |
| [`examples/`](examples/) | before/after CSS 与最小 token |

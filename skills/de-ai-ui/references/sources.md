# 来源 / Sources

本 Skill 的规则全部整理自以下公开帖子。摘要是转述，不是逐字引用（标了引号的除外）；如有出入以原帖为准。所有日期为北京时间（UTC+8）。

## 起点：@bruc3van（Bruce Van）

- 帖子：<https://x.com/bruc3van/status/2115963644811116732>（2026-10-30）
- 要点：vibe 出来的界面一眼廉价，往往输在细节上（例如嵌套圆角，内圆角应该等于外圆角减去间距）；推荐 8 位中文设计师，并概括每人一条代表帖。
- 说明：原帖里的 8 个 t.co 短链只展开到 `x.com/<用户名>/status`（缺少帖子 ID），因此下面每条帖子是按作者 + 原帖描述的内容在 X 上检索定位的。

---

## 1. @Kubai087 枯白啃设计 — 递进式圆角 + 超椭圆

- 帖子：<https://x.com/Kubai087/status/2115469767650021796>（2026-10-28，《999 个小技巧，让你 Vibe 的产品更有质感》第 004 条）
- 要点：
  - 等距内缩：内圆角 = 外圆角 − 间距，内外共用一个圆心。
  - 连续圆角 / 超椭圆：普通圆角接直边处有一道"折痕"；`border-radius: 32px; corner-shape: superellipse(1.25)`；Chrome / Edge 139+ 支持，Safari、Firefox 退回普通圆角。
  - 附英文 Prompt：从外往里推圆角、同层同圆角、最小 4、pill 与圆保持全圆、4px 网格、`@supports` 渐进增强、最后列出 `element: old -> new`。
- 同系列其他条目（本 Skill 在动效/交互参考中引用）：
  - 001 拟物按钮：<https://x.com/Kubai087/status/2114378773655326873>
  - 002 级联菜单安全区域 + 延时：<https://x.com/Kubai087/status/2114729985143677258>
  - 003 Dither 与 ASCII 效果：<https://x.com/Kubai087/status/2115091203465290087>（未收录细节，属于特效而非"去 AI 味"）
  - 005 拖拽排序：<https://x.com/Kubai087/status/2115823717024735708>
- 其他相关帖：
  - 改造 AI 生成图标、"降低非必要的体积表现"：<https://x.com/Kubai087/status/2115674219602452656>
  - 关于连续圆角与嵌套公式取舍的回复：<https://x.com/Kubai087/status/2115640858091598244>

## 2. @ZaynHao — 10 条优化界面 UI 的提示词

- 帖子：<https://x.com/ZaynHao/status/2113456751915982917>（2026-10-23，附使用前/后对比图）
- 要点（10 条）：不用中点 "·" 分隔；不加冗余解释文字；文案贴合人群、不口语化、不造词；颜色全部换成 Radix UI Colors 并按其规范使用；光学对齐 + 嵌套处同心圆角；线条/边框用 0.5px；少动画，必须时 ease-out、250ms 起步；字号不超过 4 种、最好 3 种、最小 12px，不够用字重/颜色/间距；减少需要用户判断的交互、放在用户本来就要做选择的地方并重排优先级；不随意用圆角、阴影，尤其不要卡片左边缘的彩色线条。
- 作者在回复中补充：这套"比较个人化"，0.5px 没有专门考虑低分屏 / 老旧设备（[回复1](https://x.com/ZaynHao/status/2113463139677446499)、[回复2](https://x.com/ZaynHao/status/2113463292614332685)）。
- 相关帖：<https://x.com/ZaynHao/status/2111685618925474098>（2026-10-18）——Radix Colors 的 12 个等级按使用场景分组；为应用选 3–5 个独特颜色（如背景 `f6f4f0`）；视觉对齐、同一页面不超过 3 个文字大小、注意间距、0.5px；消除"·"和解释性冗余文本。

## 3. @ianneo_ai 伊恩 — 只用黑白灰，把颜色留给内容

- 帖子：<https://x.com/ianneo_ai/status/2115277214149451968>（2026-10-28）
- 要点：AI 界面显得廉价，很多时候是颜色给多了。他点评的案例里按钮、卡片、输入框全是白和灰，颜色都在照片里；而 AI 常给渐变按钮、彩色图标、一张卡片一个颜色，"每个都想抢眼，最后就显得廉价"。案例里界面会随内容（东京夜晚）一起变暗、地图也变黑底，"不是硬切个深色模式"。给 AI 的一句话："界面只用黑白灰，颜色留给照片和内容"。
- 该帖引用了他前一天的帖子 <https://x.com/ianneo_ai/status/2115069769665884588>（案例本体，以视频/图片为主）。

## 4. @dingyi — AI slop 典型特征清单

- 帖子：<https://x.com/dingyi/status/2115790005423734818>（2026-10-29，附一张下拉按钮截图）
- 要点：完整 19 条清单见 [`slop-checklist.md`](slop-checklist.md)。包括三大 slop 字体（Instrument Serif、Space Grotesk、Bricolage Grotesque）、紫色渐变、全大写小标题、0.5px 处用了 1px、字号超过 4 种且最小低于 12px、卡片左边缘彩色竖线、下拉菜单按钮的下拉小图标等。作者称最后一条"最恶心最严重"，几乎没人修。
- 作者回复：衬线字体很多，想特别出众只能买付费的（[回复](https://x.com/dingyi/status/2115823920247152648)）。

## 5. @Xian0063 弦 — 8 条设计审美原则 + 5 个 AI 设计 Skill

- X 长文：<https://x.com/Xian0063/status/2114306504778256445>（2026-10-25，《画过10,000+张 UI 高保真，我的设计审美心得（1）：8 条原则 + 5 个常用 AI 设计 Skill》）
- 要点：AI 页面常见特征——紫蓝渐变、居中排版、卡片套卡片、每个标题上面顶一个 emoji 图标。5 个 Skill：UI UX Pro Max、Taste Skill、Impeccable、Emil Kowalski Skills、Hallmark（安装命令与适用场景见 [`libraries-and-skills.md`](libraries-and-skills.md)）。8 条原则：从好作品和日常找需求；先定义再动手；拆解好设计不照搬；用目标给反馈；先出全貌再逐块改（每轮只改一处）；统一视觉规则；先上线再优化；用反馈分配精力。
- 作者注明：文中演示是按各 Skill 官方 README 复刻的，用来说明能力，不是 Skill 的真实运行结果。
- 续篇（未收录）：<https://x.com/Xian0063/status/2115385391373324775>

## 6. @yanliudreamer 妍妍 — 10 个 UI 组件 / 工具资源

- X 长文：<https://x.com/yanliudreamer/status/2113188741452103685>（2026-10-22，《审美提升(下)👉硅谷设计师都在用的10个UI组件工具库！》）
- 要点：Coolors（配色）、Fontshare（字体）、The Noun Project（图标）、Blush（插画）、React Bits（动效组件）、Spline（3D）、Unsplash（图片）、CTA Gallery（按钮文案/CTA）、Frontify（品牌规范）、The Shape of AI（AI 交互模式）。强调图标线条粗细、圆角、比例、视觉重量要统一，整套界面用同一风格体系。
- 相关帖：<https://x.com/yanliudreamer/status/2115228047594971475>（2026-10-28，转述一篇英文"如何用 AI 设计"文章）——从全局出发而非局部修补；做减法（AI Agent 总喜欢添加多余的文案、分割线和图标）；在设计工具里一次比较 3–4 个方案，避免"原型引力"；用组件和设计系统保持一致；借鉴成熟 UX。

## 7. @ricouii — 中文网站 font-family 写法

- 帖子：<https://x.com/ricouii/status/2113462025556996412>（2026-10-23）
- 要点："先西后中、兼顾主流操作系统、最后以通用无衬线字体（sans-serif）兜底"；完整 `--font-sans` / `--font-mono` 写法与三条避坑（先西后中、写英文名、带空格加引号），见 [`typography-cjk.md`](typography-cjk.md)。

## 8. @remixdesigner — 苹果 Preview 图标的 Clear 模式图层

- 帖子：<https://x.com/remixdesigner/status/2100082157184229741>（2026-09-16，附两张图）
- 要点：新版 Preview 图标给 Clear 模式单独加了图层（"Preview Image Clear" 与 "Preview Image Clear Texture"，在默认模式下不透明度为 0 隐藏）；对比图显示把默认模式图片直接转换成 Clear 模式"有点脏"，单独处理图层"很干净"。作者是开源图标库 Remix Icon 的作者。
- 本 Skill 由此引申的规则（引申属于本仓库，不是作者原话）：不同外观模式的素材要单独设计，不要靠滤镜/自动转换。

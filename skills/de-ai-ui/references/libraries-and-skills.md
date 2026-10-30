# 资源库与 AI 设计 Skill / Libraries, resources & skills

## 1. 10 个 UI 组件 / 工具资源 — yanliudreamer

来源：<https://x.com/yanliudreamer/status/2113188741452103685>

> 说明：@bruc3van 把这篇概括为"10 个常用的 UI 组件和工具库"。实际上大部分是设计资源站点（配色、字体、图标、图片等），能直接在代码里用的组件库主要是 React Bits。下表忠实反映原文。

| # | 资源 | 类别 | 原文推荐理由 / 用法（转述） | vibe 时怎么用 `[通用实践]` |
| --- | --- | --- | --- | --- |
| 1 | [Coolors](https://coolors.co/) | 配色 | 锁定主色生成辅助色；分析冷暖、明度、饱和度 | 先定 3–5 色，再映射到 Radix 色阶 |
| 2 | [Fontshare](https://www.fontshare.com/) | 字体 | 免费高质量字体；同段文字试 3～5 种字体对比 | 替代被用烂的 slop 字体 |
| 3 | [The Noun Project](https://thenounproject.com/) | 图标 | 图标线条粗细、圆角、比例、视觉重量要统一；用同一风格体系 | 全站只用一个图标风格 |
| 4 | [Blush](https://blush.design/) | 插画 | 可组合人物、姿势、场景、颜色；用于 Onboarding、Empty State、Success State | 空状态别只放一个灰图标 + 长段说明 |
| 5 | [React Bits](https://reactbits.dev/) | 动效组件 | 文字动画、Hover、背景特效、交互反馈；可研究其代码实现 | 让 AI 直接引用组件，而不是手写花哨动画 |
| 6 | [Spline](https://spline.design/) | 3D | 理解空间、光影、材质；3D 不应抢走全部注意力 | 只在 hero 等少数位置使用 |
| 7 | [Unsplash](https://unsplash.com/) | 图片 | 选图本身是审美能力；注意主体位置、光线、色调与 UI 文字的关系 | 配合"界面黑白灰、颜色留给照片" |
| 8 | [CTA Gallery](https://www.cta.gallery/) | 按钮/CTA | 文案描述操作还是收益；主次层级；出现时机 | 改按钮文案和主次按钮 |
| 9 | [Frontify](https://www.frontify.com/en) | 品牌规范 | 系统化品牌管理；为自己建 Mini Design System | 先写 token 再写页面 |
| 10 | [The Shape of AI](https://www.shapeof.ai/) | AI 交互模式 | AI UX Patterns：引导、调整结果、建立信任、保持控制 | 做 AI 产品时参考 |

同作者相关帖（<https://x.com/yanliudreamer/status/2115228047594971475>）：用组件和设计系统保持一致性，不要每个地方都重新造轮子；参考同类产品已被验证的交互模式。

`[通用实践]` 代码层面的建议（不是来源作者推荐，只是常见选择）：优先用项目已有的组件库；没有时可选 shadcn/ui、Radix Primitives 等无样式 / 低样式基础组件，再套本 Skill 的 token，比让 AI 从零手写组件更不容易出 slop。

## 2. 5 个常用 AI 设计 Skill — Xian0063

来源：<https://x.com/Xian0063/status/2114306504778256445>（以下命令为原文所列，安装前请到各项目主页核对最新用法）

| Skill | 擅长 | 安装 / 用法（原文） | 适合 |
| --- | --- | --- | --- |
| UI UX Pro Max | 一句话需求自动配整套设计系统（行业规则、风格、配色、字体、落地页结构） | `npm install -g ui-ux-pro-max-cli` → `uipro init --ai claude` | 不知道用什么风格，要稳妥专业 |
| Taste Skill | 先定方向再做原创感；给 3 个方向挑；用真图；按 3 种宽度截图自查，最多返工 3 轮 | `npx skills add https://github.com/Leonxlnx/taste-skill --skill "design-taste-frontend"` | 官网、品牌页、作品集（一次 30–45 分钟，需 Node 22+ 与 Chrome） |
| Impeccable | 24 个设计命令 + 62 条不靠大模型的 AI 味检测规则；先 `init` 写 PRODUCT.md | `npx impeccable install` → `/impeccable init`、`/impeccable audit landing`、`/impeccable polish settings` | 已有项目逐块打磨（不替你定方向） |
| Emil Kowalski Skills | 15 个小 Skill，管动效与细节（作者曾在 Vercel、Linear，Sonner 作者） | `npx skills@latest add emilkowalski/skills` | 叠加在其他 Skill 上补动效细节 |
| Hallmark | 48 种主题材质；sloplint 三级检查（Floor / Reflex / Finish），不过不能上线 | `npx skills add nutlope/hallmark -g` → `/hallmark audit ./index.html` | 落地页、预约页、商店页、有风险的改版 |

怎么选（原文）：不知道风格 → UI UX Pro Max；想要原创感 → Taste Skill；已有项目逐块打磨 → Impeccable + Emil；改版旧站怕改坏 → Hallmark。

本 Skill（de-ai-ui）的定位：轻量、可读、规则透明的中文规则集，可以和上面任何一个一起用——例如先用它们出稿，再用本 Skill 的 [`slop-checklist.md`](slop-checklist.md) 做最后一遍自查。

## 3. Radix Colors — ZaynHao

<https://www.radix-ui.com/colors>，用法见 [`color.md`](color.md)。

## 4. Remix Icon — remixdesigner

<https://remixicon.com/>，开源图标库，作者即 @remixdesigner。Kubai087 的空状态示例里使用了它（<https://x.com/Kubai087/status/2113849121299894727>）。

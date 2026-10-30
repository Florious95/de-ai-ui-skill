# 可复制的提示词 / Copy-paste prompts

以下 prompt 均来自原作者公开帖（个别为了排版做了换行），出处见每段标题。最后一段是本仓库的合并版。

## 1. Kubai087 — 统一圆角 + 连续圆角（原文英文）

来源：<https://x.com/Kubai087/status/2115469767650021796>

```text
Make the corner radii in this UI consistent, then switch them to continuous corners. Work on the screen or components I name; ask me if I have not named them. If the project has radius tokens, change those instead of hard-coding values.

Inner radius = outer radius - padding (r = R - p)
Go from the outside in: dialog or card -> panels, inputs, buttons -> chips and tags. A box p inside a container with radius R gets R - p, so both corners share one center. Example: dialog 32, padding 16 -> panels and buttons 16; a chip 8 inside a 16 panel -> 8.
Boxes on the same level share one radius. Never go below 4.

Pills and circles stay fully round.
Keep every padding, gap and radius on a 4px grid.

Continuous corners
Keep border-radius and add the curve as progressive enhancement: @supports (corner-shape: superellipse(1.25)) { :where(*) { corner-shape: superellipse(1.25); } } Set corner-shape: round on pills and circles.

Chrome and Edge 139+ render it; Safari and Firefox skip the block and show the plain border-radius.
When done, list every radius you changed as "element: old -> new".
```

（原帖中 `@ supports` 带空格是为了避免被 X 识别为 @ 提及，这里还原为 `@supports`。）

Kubai087 同系列还有级联菜单（002）、拖拽排序（005）、拟物按钮（001）的完整英文 prompt，篇幅很长，请直接到原帖复制，要点见 [`motion-and-interaction.md`](motion-and-interaction.md)。

## 2. ZaynHao — 10 条优化界面 UI 的提示词

来源：<https://x.com/ZaynHao/status/2113456751915982917>（作者说明其中一些带有个人经验）

```text
1. 不要使用中点 "·" 作为文案的分隔符。如果有，移除它。
2. 不要在界面添加冗余的解释性描述文本，这会弄脏 UI 界面，还会浪费用户的注意力。
3. review 界面文案，尽量使其描述符合当前界面面向的人群，容易理解但不要过于口语化，长短适合其功能场景，不要冗余和随意造词。
4. 将页面所有使用的颜色，都换成 Radix UI Colors 的颜色。同时，使用那套颜色的使用规范来优化颜色使用。
5. 优化界面元素与 UI 的对齐效果，尽量做到光学对齐；有嵌套的地方，尽量做到同心圆圆角处理。
6. 如果你需要使用线条或者边框，请使用 0.5px 边框。
7. 尽量减少页面中的元素动画过渡效果，如果一定要添加，则考虑通常 ease-out，250ms 是个不错的基础设定。
8. 界面的文字大小不要超过 4 种，最好三种。最小可用文字尺寸是 12px。如果不够用，可以考虑使用字重、字体颜色、间距设计来调整页面的关系结构。
9. 尽量减少页面出现需要用户判断才能进行的交互；必须发生时，放在用户本来就打算做选择的地方。同时，重新思考页面中包含的功能和元素，判断信息优先级，使用更有秩序的做法进行组织。
10. 尽量不要随意在页面中使用圆角，阴影，尤其是一个卡片的左边缘带颜色的线条。如果非要使用圆角和阴影，请注意其值的设定，符合其功能场景。
```

（原文第 3 条"面相"、第 7 条"7则"为笔误，这里改为"面向"、"则"。）

## 3. ianneo_ai — 一句话

来源：<https://x.com/ianneo_ai/status/2115277214149451968>

```text
界面只用黑白灰，颜色留给照片和内容。
```

## 4. ricouii — 中文字体栈

来源：<https://x.com/ricouii/status/2113462025556996412>

```text
中文页面的 font-family 按"先西后中、兼顾主流操作系统、最后 sans-serif 兜底"来写；中文字体用英文名，带空格的字体名加双引号。使用：
--font-sans: -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Helvetica, Arial, "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei UI", "Microsoft YaHei", "Noto Sans CJK SC", "Noto Sans SC", "Source Han Sans CN", sans-serif;
--font-mono: "JetBrains Mono", "SF Mono", ui-monospace, Menlo, Consolas, "Liberation Mono", "Courier New", monospace;
正文用 var(--font-sans)，代码用 var(--font-mono)。
```

## 5. dingyi — 拿清单让 AI 自查

来源：<https://x.com/dingyi/status/2115790005423734818>（清单本体见 [`slop-checklist.md`](slop-checklist.md)；下面的指令是本仓库写的）

```text
按下面的 AI slop 特征清单逐条审查当前页面，列出命中的条目、位置和修改方案，先不要改代码：
到处都是标签和斜体字；Instrument Serif / Space Grotesk / Bricolage Grotesque；滥用等宽字体；分割线、多层阴影、半透明叠色、带边框的容器过多；图表过于详细；文案口语化或自造词；代码面包屑、章节编号、标题上方小眉标；紫色渐变；全大写小标题；中圆点分隔符；正文 Emoji 与无用文字；hero 字体过大；冗余解释文字；嵌套未做同心圆角；边框粗细不统一（该 0.5px 的用了 1px）；滚动动效过多、过渡生硬；字号超过 4 种或小于 12px；卡片左边缘彩色竖线；下拉菜单按钮的下拉小图标没处理好。
```

## 6. Xian0063 — 先定义、再出全貌、每轮只改一处（工作流指令）

来源：<https://x.com/Xian0063/status/2114306504778256445>（原则来自原文，下面的措辞是本仓库写的）

```text
先不要写代码。请先问我：这个页面给谁用、解决什么问题、要给人什么感觉。
确认后出一版完整页面。然后列出问题清单并按重要程度排序；之后每轮只改一处，等我确认再改下一处。
我给反馈时会在截图上标出问题并描述想要的效果，具体数值由你来定。
```

## 7. 本仓库合并版（推荐默认使用）

见 [`../SKILL.md`](../SKILL.md#可直接复制给-ai-的提示词--copy-paste-prompts)。

# 动效与交互 / Motion & interaction

## 1. 基础：少即是多 — ZaynHao / dingyi

- 尽量减少页面中的元素动画过渡效果；如果一定要添加，**通常 ease-out，250ms 是不错的基础设定**。（ZaynHao 第 7 条）
- 页面滚动时动效过多、过渡不收敛很生硬，是 slop 特征。（dingyi）
- 尽量减少需要用户判断才能进行的交互；必须发生时，放在用户本来就打算做选择的地方。同时重新思考页面功能与元素的信息优先级，用更有秩序的方式组织。（ZaynHao 第 9 条）

```css
:root {
  --ease-out: cubic-bezier(0.2, 0.8, 0.2, 1); /* [通用实践] 任一平滑 ease-out 均可 */
  --dur: 250ms;
}
.menu { transition: opacity var(--dur) var(--ease-out), transform var(--dur) var(--ease-out); }
@media (prefers-reduced-motion: reduce) {
  * { transition-duration: 0.01ms !important; animation-duration: 0.01ms !important; }
}
```

## 2. 细节手感 — Emil Kowalski Skills（Xian0063 转述）

来源：<https://x.com/Xian0063/status/2114306504778256445>（Xian0063 文中说明演示为按 README 复刻）

- 进场动画用 **ease-out**，不用 ease-in：一开始就有反应，感觉更快。
- 下拉菜单**从按钮的位置长出来**，从 **0.96** 开始缩放，而不是从 0。
- 按钮按下缩到 **0.97**，有手感。
- 提示（toast）叠成一摞，不把内容挤下去。
- 长名字截断，大数字缩写，不把卡片撑破。

```css
.dropdown { transform-origin: var(--trigger-origin, top left); }
.dropdown[data-state="closed"] { opacity: 0; transform: scale(0.96); }
.dropdown[data-state="open"]   { opacity: 1; transform: scale(1); transition: 200ms var(--ease-out); }
.button:active { transform: scale(0.97); }
.name { overflow: hidden; text-overflow: ellipsis; white-space: nowrap; }
```

## 3. 级联菜单：安全三角区 + 三个延时 — Kubai087（002）

来源：<https://x.com/Kubai087/status/2114729985143677258>（原帖附完整英文 Prompt，可直接复制）

- 问题：鼠标从父菜单斜着移向子菜单时会擦过下面几行，普通菜单一碰就切换，子菜单"跑丢"。
- 安全区：以鼠标上一刻位置为顶点，连到子菜单靠近一侧的上下两个角，围成三角形；鼠标在三角形里就忽略路过的行。离开三角形、或停留超过 **1.2 秒**才切换。
- 延时：悬停 **220ms** 后才打开子菜单；离开菜单 **360ms** 后才关闭；（Prompt 中）拖拽物经过文件夹行 420ms 后打开；安全区内每 80ms 复查一次。
- 行高亮由组件状态驱动，不用 CSS `:hover`，否则安全区内经过的行仍会亮起。
- 键盘：方向键移动、Right/Enter 打开、Left 返回、Escape 全部关闭并把焦点还给触发按钮；使用 `menu` / `menuitem` 角色与 `aria-expanded`。

## 4. 拖拽排序：由近及远的"推挤" — Kubai087（005）

来源：<https://x.com/Kubai087/status/2115823717024735708>

- 光标：可拖拽时为手指，拖动中为抓手。
- 落点用一条插入线提示（约为文字颜色的 15%），出现时从中间展开，并滑向新的落点。
- 插入线两侧元素向外避让，离得越近让得越多、动得越早：**位移 = 10px × 0.7ⁿ，延迟 = 24ms × n**（n 为与插入线相隔的层数，紧挨着的为 0；卡片约 8px）；用几乎不回弹、约 0.25s 稳定的弹簧。
- 用 transform 而不是改布局；支持键盘重排；`prefers-reduced-motion` 时只保留插入线。
- 每种动作用自己的曲线，而不是"到处都是同一个 ease-out"。

## 5. 有点击手感的拟物按钮 — Kubai087（001）

来源：<https://x.com/Kubai087/status/2114378773655326873>

- 已有组件库 / 设计系统时，不新增组件，通过它自己的 variant 与 token 重新设计 Button，保留 API 和可访问性。
- 风格：冷静精确，只用中性灰，不用品牌色；光源正上方；不要 Web 2.0 高光、发光、大模糊。
- 五层材质：渐变面（顶部比底部亮 6–8%）、比面底色深一级的 1px 边、顶部 inset 高光、底部 inset 暗线、两层投影（紧贴的接触阴影 + 柔和抬升）。
- 按下：`translateY(1px)`、渐变翻转、外投影收拢、高光变内阴影；静止与按下的 inset 层数相同（用透明层补齐），阴影才能过渡而不是跳变。
- 时长：transform 120ms、阴影 140ms、颜色 160ms。
- 尺寸：14px 字号对应高 40px、左右 padding 18px、圆角 10px、字重 600；所有长度按 `u = 字号 / 14` 缩放。

> 注意：拟物按钮是一种有意识的风格选择，和"界面只用黑白灰"并不冲突（它本身就只用中性灰），但不要和本 Skill 的"克制阴影"原则混用成多层花哨阴影。

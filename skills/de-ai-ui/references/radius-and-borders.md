# 圆角与边框 / Radius & borders

## 1. 递进式圆角（等距内缩）— Kubai087

来源：<https://x.com/Kubai087/status/2115469767650021796>

**公式：内圆角 = 外圆角 − 间距（r = R − p），内外共用一个圆心。**

- 从外往里推：dialog / card → panels、inputs、buttons → chips、tags。
- 一个盒子在圆角为 R 的容器里、间距为 p，它的圆角就是 R − p。
  - 例：dialog 32、padding 16 → panel 与 button 16。
  - 例：16 的 panel 里间距 8 的 chip → 8。
- 同一层级的盒子共用一个圆角。最小不低于 4。
- Pill 与圆形保持全圆。
- 所有 padding、gap、radius 都在 4px 网格上。
- 项目有 radius token 时改 token，不要硬编码。
- 改完列出每一个改动：`element: old -> new`。


## 2. 连续圆角 / 超椭圆 — Kubai087

普通圆角接直边的地方有一道"折痕"，连续圆角过渡更顺（类比 iOS）。

```css
.card {
  border-radius: 32px;            /* 所有浏览器的基线 */
}

/* 渐进增强：只在支持的浏览器生效（Chrome / Edge 139+）
   Safari、Firefox 会跳过整个块，显示普通 border-radius */
@supports (corner-shape: superellipse(1.25)) {
  :where(*) { corner-shape: superellipse(1.25); }
  .pill, .avatar, .badge-dot { corner-shape: round; } /* pill 与圆形保持正圆 */
}
```

**连续圆角与嵌套公式的取舍**：推友 @ninthbit_ai 在讨论中指出，超椭圆会让圆角"变得更方"（纯圆会变方，需要加曲率补偿），而且用连续圆角做嵌套时，没法在数学上严格满足 R(inner) = R(outer) − padding。Kubai087 的回应是：他**倾向于只在关键元素上加连续圆角**，这样可以不用太严格遵守等距内缩的数值（<https://x.com/Kubai087/status/2115640858091598244>）。

实践建议：
- 默认先保证普通圆角的嵌套公式正确；
- 连续圆角优先用在视觉焦点（主卡片、对话框、App 图标式的大块面），而不是全局 `:where(*)` 一刀切——全局开启是 Kubai087 Prompt 的写法，如果嵌套很深、看起来别扭，就收窄到关键元素；
- pill / 圆形一律 `corner-shape: round`。

## 3. 同心圆角 + 光学对齐 — ZaynHao

来源：<https://x.com/ZaynHao/status/2113456751915982917>（第 5 条）

- 有嵌套的地方尽量做到同心圆圆角（与第 1 节公式一致）。
- 元素与 UI 的对齐尽量做到**光学对齐**，而不只是数值对齐。`[通用实践]` 典型场景：图标 + 文字按钮里图标视觉重心偏移、三角形播放图标需要右移、圆形元素需要比方形稍大才显得等大。

## 4. 0.5px 边框 — ZaynHao / dingyi

- ZaynHao 第 6 条：如果需要使用线条或者边框，请使用 0.5px 边框。
- dingyi：线条和边框粗细不统一、该用 0.5px 的地方用了 1px，是 slop 特征。
- **注意**：ZaynHao 在回复里说这是"比较个人化的提示"，没考虑低分屏 / 老旧设备（<https://x.com/ZaynHao/status/2113463139677446499>）。

`[通用实践]` 在 1x 屏上 0.5px 可能被四舍五入成 1px 或不显示。需要兼容时用 token 做回退：

```css
:root { --hairline: 1px; }
@media (min-resolution: 2dppx) {
  :root { --hairline: 0.5px; }
}
.card { border: var(--hairline) solid var(--gray-a6); }
/* 也可以用 box-shadow: 0 0 0 0.5px ... 代替 border，避免影响布局尺寸 */
```

关键是**全站统一一个 hairline token**，而不是某处 1px、某处 0.5px。

## 5. 圆角和阴影要克制 — ZaynHao / dingyi / Xian0063

- 不要随意在页面中使用圆角、阴影，尤其不要**卡片左边缘带颜色的线条**；非用不可时数值要符合功能场景。（ZaynHao 第 10 条）
- 不要细节过多：分割线、多层阴影、半透明叠色、带边框的容器。（dingyi）
- 不要卡片套卡片。（Xian0063）

## 6. 拟物按钮里的"内圆角"细节 — Kubai087（001）

来源：<https://x.com/Kubai087/status/2114378773655326873>

把所有 inset 阴影放在按钮自身的 `box-shadow` 里（排在外投影之前），不要放到伪元素覆盖层上：元素上的 inset 阴影会跟随内圆角（外圆角 − 边框），各状态下角都能对齐。完整按钮规格见 [`motion-and-interaction.md`](motion-and-interaction.md)。

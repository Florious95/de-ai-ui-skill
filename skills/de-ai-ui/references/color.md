# 颜色 / Color

## 1. 界面只用黑白灰，颜色留给内容 — ianneo_ai

来源：<https://x.com/ianneo_ai/status/2115277214149451968>

- AI 界面有廉价感，很多时候是**颜色给多了**。
- 好的案例里，按钮、卡片、输入框全是白的灰的；颜色都在照片里（夜景、樱花、霓虹），界面自己不抢。
- AI 常见做法：渐变按钮、彩色图标、一张卡片一个颜色——"每个都想抢眼，最后就显得廉价"。
- 加分细节：界面跟着内容变化——白天行程是亮的，点进东京的晚上整个屏幕变暗、地图也变黑底，"不是硬切个深色模式"。
- 一句话 Prompt：**"界面只用黑白灰，颜色留给照片和内容。"**

执行要点 `[通用实践]`：
- 中性灰负责 90% 的 chrome（背景、表面、边框、次要文字）。
- 一个强调色只用于主操作 / 当前状态 / 关键数据；语义色（成功/警告/错误）只在有语义时出现。
- 内容（照片、插画、图表数据）可以有颜色，界面框架不和它抢。

## 2. 用 Radix Colors — ZaynHao

来源：<https://x.com/ZaynHao/status/2113456751915982917>（第 4 条）、<https://x.com/ZaynHao/status/2111685618925474098>

- 把页面所有颜色都换成 **Radix UI Colors**，并使用那套颜色的使用规范来优化颜色使用。
- 好处："无脑按照规则来用，怎么搭配都不会出错"。它提供 **12 个颜色等级**，这些数字按使用场景分组，每个数字都有使用场景定义。
- 为应用选择 **3–5 个独特的颜色**定下基础色调；一个思路是从你喜欢的网站或应用里识别颜色（他的应用背景色是 `#f6f4f0`）。

`[通用实践]` Radix 官方文档对 12 级的约定（摘要，以 <https://www.radix-ui.com/colors/docs/palette-composition/understanding-the-scale> 为准）：

| 级别 | 用途 |
| --- | --- |
| 1–2 | 应用背景、次级背景 |
| 3–5 | 组件背景：默认 / hover / pressed |
| 6–8 | 边框：弱边框与分隔线 / 组件边框与 focus ring / hover 时的组件边框 |
| 9–10 | 实色背景（如主按钮）/ 其 hover |
| 11–12 | 低对比文字 / 高对比文字 |

```bash
npm i @radix-ui/colors
```

```css
@import "@radix-ui/colors/gray.css";
@import "@radix-ui/colors/gray-alpha.css";
@import "@radix-ui/colors/gray-dark.css";
/* 只挑 1 个强调色，例如 */
@import "@radix-ui/colors/blue.css";
@import "@radix-ui/colors/blue-dark.css";
```

## 3. 要避免的颜色用法

- 紫色渐变（dingyi）、紫蓝渐变（Xian0063）
- 渐变按钮、彩色图标、一张卡片一个颜色（ianneo_ai）
- 卡片左边缘的彩色竖线（ZaynHao、dingyi）
- 单独染色的一个字（Xian0063 转述 Hallmark）
- 半透明叠色堆叠（dingyi）

## 4. 配色探索 — yanliudreamer

需要从零探索配色时可用 [Coolors](https://coolors.co/)：锁定品牌主色再生成辅助色；分析每组配色的冷暖、明度对比、饱和度，以及它为什么看起来舒服。（<https://x.com/yanliudreamer/status/2113188741452103685>）

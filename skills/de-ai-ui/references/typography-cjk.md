# 字体与排版（含中文）/ Typography & CJK

## 1. 字号层级 — ZaynHao / dingyi

- 界面文字大小**不超过 4 种，最好 3 种**；最小可用文字尺寸 **12px**。不够用时用**字重、字体颜色、间距**来调整关系结构。（ZaynHao 第 8 条，<https://x.com/ZaynHao/status/2113456751915982917>）
- 他在另一帖里更严格：同一页面不超过 3 个文字大小。（<https://x.com/ZaynHao/status/2111685618925474098>）
- 字号超过 4 种、最小还低于 12px 是 slop 特征；hero 区字体大得离谱也是。（dingyi）

`[通用实践]` 一个够用的 3–4 档示例：

```css
:root {
  --text-sm: 12px;   /* 辅助信息、标签 */
  --text-md: 14px;   /* 正文、控件 */
  --text-lg: 16px;   /* 小标题 / 强调正文（可选第 4 档） */
  --text-xl: 24px;   /* 页面标题；落地页 hero 也别夸张到离谱 */
}
/* 层级优先靠字重和颜色：同为 14px，标题 600 + gray-12，说明 400 + gray-11 */
```

## 2. 要避开的字体与排版习惯 — dingyi / Xian0063

- 三大 slop 字体：**Instrument Serif**（莫奈风格）、**Space Grotesk**、**Bricolage Grotesque**。
- 滥用等宽字体；到处斜体。
- 全大写的小标题；标题上方的小眉标（eyebrow）；章节编号；代码面包屑。
- 全部居中排版（Xian0063）。
- 想要特别出众的衬线字体，dingyi 的回复是"只能买付费的"——也就是别指望默认那几款免费字体出彩。

挑字体时可以到 [Fontshare](https://www.fontshare.com/) 比较：拿同一段文字试 3～5 种字体，关注字重、字宽、字间距和不同字号下的表现。（yanliudreamer）

## 3. 中文网站 font-family — ricouii

来源：<https://x.com/ricouii/status/2113462025556996412>

最佳实践：**"先西后中、兼顾主流操作系统、最后以通用无衬线字体（sans-serif）兜底"。**

原帖写法（整理成可直接粘贴的 CSS，内容不变）：

```css
:root {
  --font-sans:
    /* 西文 */
    -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto,
    "Helvetica Neue", Helvetica, Arial,
    /* 中文 */
    "PingFang SC", "Hiragino Sans GB", "Microsoft YaHei UI", "Microsoft YaHei",
    "Noto Sans CJK SC", "Noto Sans SC", "Source Han Sans CN",
    sans-serif;

  --font-mono: "JetBrains Mono", "SF Mono", ui-monospace, Menlo, Consolas,
    "Liberation Mono", "Courier New", monospace;
}

body { font-family: var(--font-sans); }
code, pre, kbd { font-family: var(--font-mono); }
```

（原帖代码一行写的是 `var(-font-mono)`，少了一个 `-`，这里已修正为 `var(--font-mono)`。）

各段含义（原帖解释）：
- `-apple-system, BlinkMacSystemFont`：Apple 生态（macOS、iOS、Safari、Chrome）的系统默认字体入口。
- `"Segoe UI"`：Windows 的现代 UI 西文字体。
- `Roboto, "Helvetica Neue", Arial`：Android、macOS 及 Web 通用西文字体。
- `JetBrains Mono` 等：代码 / 等宽字体的主流写法。

三条避坑：
1. **先西后中**：西文字体一定写在中文字体前面，否则中文字体自带的英文字母会覆盖你的英文字体，导致英文和数字显示不佳。
2. **写英文名**：如 `"Microsoft YaHei"` 而不是 `微软雅黑`，避免部分 Linux / macOS 浏览器因编码问题识别不出。
3. **带空格加引号**：`"Helvetica Neue"`、`"Microsoft YaHei"` 必须用双引号。

另外：不声明字体时，浏览器渲染的是**默认字体**，不一定是系统字体。

> 与第 2 节的关系：等宽字体只给代码用（`--font-mono`），不要拿来做正文或标题装饰。

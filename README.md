# de-ai-ui · UI 设计去 AI 味 Skill

> 让 vibe coding 出来的界面不再"一眼 AI、一眼廉价"。

一个给 **Claude Code / Cursor / Codex** 等 Agent 使用的 Skill（`SKILL.md` 格式）。它把 8 位中文设计师在 X 上公开分享的"AI 界面哪里露馅、该怎么跟 AI 说"整理成**可执行、可检查**的规则、自查清单、工作流和可直接复制的 Prompt。

灵感与名单来自 [@bruc3van 的这条推文](https://x.com/bruc3van/status/2115963644811116732)：

> vibe 出来的界面一眼廉价，往往输在细节上。比如嵌套圆角，内圆角应该等于外圆角减去间距。

**English summary:** A drop-in agent skill that helps AI coding agents avoid the "AI-generated / cheap" look in UI work. It distills public posts by eight Chinese-speaking designers into checkable rules (nested radius `r = R − p`, superellipse corners, 0.5px hairlines, ≤4 font sizes ≥12px, Radix Colors, grayscale chrome with color reserved for content, CJK `font-family` stacks), a 19-item "AI slop" self-audit checklist, a before/while/after workflow, and copy-paste prompts. Every rule is attributed to its source post. Written in Chinese with bilingual headings.

## 包含什么

- **核心原则**：做减法、界面退后内容出彩、一致性靠系统、细节几何正确、先定义再动手、不同模式单独设计。
- **硬规则（可打勾）**：圆角与边框、颜色、字体与中文排版、文案、动效与交互、组件与图标。
- **AI slop 自查清单**：dingyi 的 19 条原清单 + 其他来源补充。
- **工作流**：动手前 → 编码中 → 自查，每轮只改一处。
- **Prompt**：Kubai087 的圆角 prompt 原文、ZaynHao 的 10 条提示词、ianneo_ai 的一句话、ricouii 的字体栈，以及一段合并版。
- **示例**：`tokens.css` 最小 token 集，`before-after.css` 前后对比。

## 目录

```text
skills/de-ai-ui/
├── SKILL.md                      # 入口：触发条件、原则、硬规则、工作流、合并版 Prompt
├── references/
│   ├── sources.md                # 8 位设计师 + @bruc3van 原帖链接与要点
│   ├── slop-checklist.md         # AI slop 自查清单
│   ├── radius-and-borders.md     # r = R − p、超椭圆、0.5px 与回退
│   ├── color.md                  # 黑白灰 + Radix Colors
│   ├── typography-cjk.md         # 字号层级、slop 字体、中文 font-family
│   ├── copy-and-content.md       # 文案规则
│   ├── motion-and-interaction.md # 动效参数、级联菜单、拖拽排序、拟物按钮
│   ├── icons-and-detail.md       # 图标一致性、多模式素材、AI 图标改造
│   ├── libraries-and-skills.md   # 10 个设计资源 + 5 个 AI 设计 Skill
│   └── prompts.md                # 全部可复制 Prompt
└── examples/
    ├── tokens.css
    └── before-after.css
```

## 安装

先克隆：

```bash
git clone https://github.com/Florious95/de-ai-ui-skill.git
```

**Claude Code**

```bash
# 个人（所有项目可用）
mkdir -p ~/.claude/skills && cp -r de-ai-ui-skill/skills/de-ai-ui ~/.claude/skills/
# 或仅当前项目
mkdir -p .claude/skills && cp -r de-ai-ui-skill/skills/de-ai-ui .claude/skills/
```

**Cursor**

```bash
# 个人
mkdir -p ~/.cursor/skills && cp -r de-ai-ui-skill/skills/de-ai-ui ~/.cursor/skills/
# 或仅当前项目
mkdir -p .cursor/skills && cp -r de-ai-ui-skill/skills/de-ai-ui .cursor/skills/
```

Cursor 也会读取 `.agents/skills/`、`~/.agents/skills/` 以及 Claude / Codex 的 skills 目录。在 Agent 对话里输入 `/de-ai-ui` 可手动调用。

**Codex**

```bash
# 个人
mkdir -p ~/.agents/skills && cp -r de-ai-ui-skill/skills/de-ai-ui ~/.agents/skills/
# 或仅当前仓库
mkdir -p .agents/skills && cp -r de-ai-ui-skill/skills/de-ai-ui .agents/skills/
```

旧版 Codex 使用 `~/.codex/skills/`。在 Codex 里可用 `/skills` 或 `$de-ai-ui` 调用。

**其他 Agent**：没有 Skill 机制的工具，可以直接把 `SKILL.md` 内容贴进项目规则（如 `AGENTS.md`、`.cursor/rules`、`CLAUDE.md`），或按需引用 `references/` 里的文件。

## 怎么用

装好后正常提需求即可，Agent 在做 UI / 落地页 / 组件，或你说"有 AI 味、太廉价"时会自动加载。也可以明确说：

- "用 de-ai-ui 审查这个页面，先列出命中的 slop 项，不要改代码。"
- "按 de-ai-ui 的规则重做设置页，每轮只改一处。"
- "把这个项目的圆角按 r = R − p 统一，并列出 element: old -> new。"

## 致谢 / Credits

所有规则整理自以下设计师的公开帖子，详见 [`sources.md`](skills/de-ai-ui/references/sources.md)。感谢他们的分享：

| 作者 | 主题 | 原帖 |
| --- | --- | --- |
| [@bruc3van](https://x.com/bruc3van) Bruce Van | 汇总推荐这 8 位设计师 | [链接](https://x.com/bruc3van/status/2115963644811116732) |
| [@Kubai087](https://x.com/Kubai087) 枯白啃设计 | 递进式圆角 + 超椭圆连续圆角 | [链接](https://x.com/Kubai087/status/2115469767650021796) |
| [@ZaynHao](https://x.com/ZaynHao) | 10 条让 AI 界面变精致的提示词 | [链接](https://x.com/ZaynHao/status/2113456751915982917) |
| [@ianneo_ai](https://x.com/ianneo_ai) 伊恩 | 只用黑白灰，把颜色留给内容 | [链接](https://x.com/ianneo_ai/status/2115277214149451968) |
| [@dingyi](https://x.com/dingyi) | AI slop 特征清单 | [链接](https://x.com/dingyi/status/2115790005423734818) |
| [@Xian0063](https://x.com/Xian0063) 弦 | 8 条审美原则 + 5 个 AI 设计 Skill | [链接](https://x.com/Xian0063/status/2114306504778256445) |
| [@yanliudreamer](https://x.com/yanliudreamer) | 10 个 UI 组件 / 工具资源 | [链接](https://x.com/yanliudreamer/status/2113188741452103685) |
| [@ricouii](https://x.com/ricouii) | 中文网站 font-family 写法 | [链接](https://x.com/ricouii/status/2113462025556996412) |
| [@remixdesigner](https://x.com/remixdesigner) | 苹果 Preview 图标的 Clear 模式图层 | [链接](https://x.com/remixdesigner/status/2100082157184229741) |

本仓库是个人整理，与上述作者无隶属关系；摘要如与原帖有出入，以原帖为准。欢迎提 Issue / PR 补充或更正。

## License

本仓库自有的文字与代码以 [MIT](LICENSE) 发布。规则内容是对上述公开帖子的转述与整理，原帖文字、图片与 Prompt 的权利归原作者所有，请通过链接阅读原文。

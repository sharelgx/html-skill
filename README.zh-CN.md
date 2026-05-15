# HTML Effectiveness Skill

一个用于 Codex/Cursor 的轻量 skill：当 Markdown 会让信息变得太长、太平、难比较时，引导 agent 生成可交互的单文件 HTML。

这个 skill 借鉴了 [`thariqs/html-effectiveness`](https://github.com/ThariqS/html-effectiveness) 的思路和视觉语言，但不打包、不依赖原仓库的 20 个 HTML demo。它抽象的是可复用方法：什么时候该用 HTML、选择什么信息结构、加入哪些真实有用的交互、如何验收。

## 适合做什么

- 交互式分析页
- 可视化报告和数据看板
- 产品或工程开发计划
- PR / 代码评审摘要
- 研究或功能解释页
- 设计系统展示
- 任务分拣看板
- Prompt 调参器
- 小型产品原型沙盒

## 安装

Codex：

```bash
mkdir -p ~/.codex/skills
git clone https://github.com/sharelgx/html-skill.git ~/.codex/skills/html-effectiveness
```

Cursor 或其他 agent：把仓库文件夹放到对应的 skills/rules 目录，或者把 `SKILL.md` 作为项目规则，并保留 `references/example-patterns.md` 作为模式参考。

## 使用示例

```text
做一个交互 HTML 分析页，比较这几个方案的取舍和风险。
```

```text
不要只写 Markdown，做成一个单文件 HTML 看板，可以筛选和导出。
```

```text
把这个开发计划做成 HTML 报告，包含里程碑、风险、任务清单和复制按钮。
```

## 它会引导 agent 做什么

- 判断是否值得用 HTML 替代 Markdown。
- 选择一个主模式，例如方案对比、代码评审、流程解释、任务看板、Prompt 调参器。
- 生成自包含 `.html` 文件，CSS 和 JS 内联。
- 默认使用 Claude paper 视觉系统，同时保留真正可用的交互。
- 验证文件可以本地打开，并且不丢失用户的原始数据。

## 仓库结构

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    └── example-patterns.md
```

`SKILL.md` 包含核心工作流和验收标准。`references/example-patterns.md` 是精简模式库，agent 只有在需要选择页面结构时才需要读取。

## 与 Claude Paper Web Design 的区别

- `html-skill` 解决的是：什么时候用交互 HTML，以及 HTML 应该承载什么结构。
- [`claude-paper-web-design`](https://github.com/sharelgx/claude-paper-web-design) 解决的是：网页、后台、原型如何做成 Claude paper 视觉风格。

两者可以一起使用：先用 `html-skill` 确定信息结构，再用 `claude-paper-web-design` 统一视觉语言。

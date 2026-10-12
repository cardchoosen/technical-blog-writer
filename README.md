# Technical Blog Writer

A Codex skill for writing in-depth Chinese technical articles, with source research, outline discussion, and explanations of principles, design trade-offs, and technical evolution.

从一个技术概念出发，帮助你生成学习材料，也把学过的内容沉淀成可以持续修改的中文 Markdown 文章。

## 它怎样写文章

这个技能面向有一定基础的读者，围绕具体问题展开讲解。它会主动研究资料，先与你讨论大纲，再完成文章。结构随主题安排，核心机制充分展开，代码优先采用伪代码，例子和图按解释需要使用。

文章会同时关注技术的发展脉络：出现前如何解决问题、旧方案遇到了什么局限、哪些需求促成新设计，以及后来怎样演进。这些内容与原理和设计取舍自然衔接。

写作流程包括：

1. **研究与大纲**：结合已有知识形成检索方向，查阅官方文档、规范、论文或其他相关资料，提出范围、前置知识与大纲，等待你确认。
2. **完整成稿**：按确认后的范围完成一篇中文 Markdown 文章。正文保持连贯，实际使用的参考资料统一列在文末，关键结论与来源的对应关系保存在单独的研究记录中。
3. **按反馈改稿**：你明确提出修改建议后，修改指定部分和直接相关的内容。讨论与追问先在对话中回答。
4. **按需核验**：你主动要求时，独立检查事实、推导、伪代码和全文连贯性，报告具体问题与建议；明确要求同时修正时再改稿。

如果已有相关文档，技能可以建议文章的归类，并引用确实存在的前置文章。分类由你决定；没有对应前置文章时，直接说明预期读者了解的概念。

## 安装

### 使用 Codex 的技能安装器

在 Codex 中输入：

```text
使用 $skill-installer 安装这个 GitHub 仓库中的技能：
仓库：https://github.com/cardchoosen/technical-blog-writer
路径：skills/technical-blog-writer
```

### 手动安装

也可以将技能目录复制到 Codex 当前官方文档中的个人技能目录 `~/.agents/skills`：

```bash
git clone https://github.com/cardchoosen/technical-blog-writer.git
mkdir -p ~/.agents/skills
cp -R technical-blog-writer/skills/technical-blog-writer ~/.agents/skills/
```

如果技能没有出现在选择器中，重启 Codex。更新时替换已安装的对应目录。安装位置与发现机制见 [OpenAI 的技能文档](https://learn.chatgpt.com/docs/build-skills)。

## 使用

### 从一个概念开始

```text
使用 $technical-blog-writer 写一篇关于「一致性哈希」的文章。
```

技能会先研究并给出大纲。你可以调整读者基础、覆盖范围、讲解重点和文章位置，确认后再生成完整正文。

也可以一开始就给出偏好：

```text
使用 $technical-blog-writer 写一篇关于「MVCC」的文章。
读者了解事务与索引，但不熟悉数据库内部实现。
重点讲清它解决的问题、版本可见性与设计取舍。
先给我大纲，成稿放到 docs/database/mvcc.md。
```

### 修改已有文章

```text
使用 $technical-blog-writer 修改 docs/database/mvcc.md：
补充旧方案的局限，以及版本可见性判断的伪代码。
保留其他内容，并调整直接相关的解释。
```

### 手动触发核验

```text
使用 $technical-blog-writer 对 docs/database/mvcc.md
做一次核验与通读，报告问题和修改建议，先不修改正文。
```

如果希望检查后直接修改，可以明确说「核验并修正这篇文章」。

## 示例文章

[OSI 与 TCP/IP：网络分层如何让通信变得可理解](examples/osi-and-tcp-ip.md) 来自一次实际试写与反馈修改，展示了技术形成背景、分层职责、数据转发、伪代码与后续演进的讲解方式。示例尚未执行独立的「核验与通读」。

它是输出效果的示例。其他主题的大纲、章节安排、篇幅和举例方式会根据解释需要调整。

## 文件结构

```text
technical-blog-writer/
├── README.md
├── LICENSE
├── skills/
│   └── technical-blog-writer/
│       ├── SKILL.md
│       └── agents/
│           └── openai.yaml
└── examples/
    └── osi-and-tcp-ip.md
```

`SKILL.md` 包含写作流程与行为要求，`agents/openai.yaml` 提供技能的显示名称、简介和默认提示词。

## 运行条件与范围

需要能够加载 Agent Skills 的 Codex 环境。资料研究需要可用的搜索或网页读取能力；技能本身以指令为主，检索与文件操作由运行它的环境提供。

文章默认面向有一定基础的读者，以中文 Markdown 交付，允许长文。具体任务中明确给出的语言、读者与写作要求优先。普通技术问答可以直接在对话中进行。

## 贡献

欢迎通过 Issue 或 Pull Request 提供改进。反馈写作效果时，请附上选题、读者基础、相关输出片段，以及你希望改善的具体问题。修改技能时，优先用实际写作反馈解释改动，并提供能够体现变化的例子。

## 许可证

本仓库的技能、说明文档与示例文章采用 [MIT License](LICENSE)。文末链接的外部参考资料遵循各自的许可。

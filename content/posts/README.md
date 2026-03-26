# 完整文章翻译：Lessons from Building Claude Code: How We Use Skills

## 文章信息

### 基本信息
- **标题**：Lessons from Building Claude Code: How We Use Skills
- **原推文作者**：Thariq (@trq212)
- **转发者**：Paweł Huryn (@PawelHuryn)
- **链接**：https://x.com/PawelHuryn/status/2025470280945041547
- **原始文章链接**：https://x.com/trq212/article/2033949937936085378
- **发布时间**：2026年3月18日

### 互动数据
- **回复**：362
- **转帖**：2,694
- **喜欢**：15,723
- **书签**：43,209
- **观看**：647.8万

---

## 📝 完整中英对照翻译

---

## 引言

### 英文原文
```
Skills have become one of most used extension points in Claude Code. They're flexible, easy to make, and simple to distribute. But this flexibility also makes it hard to know what works best.

What type of skills are worth making? What's the secret to writing a good skill? When do you share them with others?

We've been using skills in Claude Code extensively at Anthropic with hundreds of them in active use. These are the lessons we've learned about using skills to accelerate our development.
```

### 中文翻译
```
Skills 已经成为 Claude Code 中使用最广泛的扩展点之一。它们灵活、易于制作、易于分发。但这种灵活性也使得很难知道什么最有效。

什么类型的 Skills 值得制作？编写一个好 Skill 的秘诀是什么？什么时候与他人分享？

我们在 Anthropic 广泛使用 Claude Code 中的 Skills，有数百个 Skills 处于活跃使用状态。这些是我们关于使用 Skills 加速开发所学到的东西。
```

---

## What are Skills? (什么是 Skills?)

### 英文原文
```
If you're new to skills, I'd recommend reading our docs or watching our newest course on new Skilljar on Agent Skills, this post will assume you already have some familiarity with skills.

A common misconception we hear about skills is that they are "just markdown files", but the most interesting part of skills is that they're not just text files. They're folders that can include scripts, assets, data, etc. that the agent can discover, explore, and manipulate.

In Claude Code, skills also have a wide variety of configuration options including registering dynamic hooks. We've found that some of the most interesting skills in Claude Code use these configuration options and folder structure creatively.
```

### 中文翻译
```
如果你对 Skills 不熟悉，我建议阅读我们的文档或观看我们关于 Agent Skills 的最新 Skilljar 课程，这篇文章假设你已经对 Skills 有一定了解。

关于 Skills，我们听到的一个常见误解是它们"只是 markdown 文件"，但 Skills 最有趣的部分是它们不仅仅是文本文件。它们是文件夹，可以包含脚本、资源、数据等，代理可以发现、探索和操作。

在 Claude Code 中，Skills 也有各种各样的配置选项，包括注册动态挂钩。我们发现 Claude Code 中一些最有趣的 Skills 创造性地使用了这些配置选项和文件夹结构。
```

---

## Types of Skills (Skills 的类型)

![Skills 类型分类图](https://x.com/trq212/article/2033949937936085378/media/2033778969078861826)

### 英文原文
```
After cataloging all of our skills, we noticed they cluster into a few recurring categories. The best skills fit cleanly into one; the more confusing ones straddle several. This isn't a definitive list, but it is a good way to think about if you're missing any inside of your org.
```

### 中文翻译
```
在编目我们所有的 Skills 后，我们注意到它们聚集到几个重复的类别中。最好的 Skills 完全符合一个类别；更混乱的跨越几个类别。这不是一个确定的列表，但它是一个很好的方式来思考你的组织中是否缺少任何内容。
```

---

## 1. Library & API Reference (库和 API 参考)

### 英文原文
```
Skills that explain how to correctly use a library, CLI, or SDKs. These could be both for internal libraries or common libraries that Claude Code sometimes has trouble with. These skills often included a folder of reference code snippets and a list of gotchas for Claude to avoid when writing a script.

Examples:
- billing-lib — your internal billing library: edge cases, footguns, etc.
- internal-platform-cli — every subcommand of your internal CLI wrapper with examples on when to use them
- frontend-design — make Claude better at your design system
```

### 中文翻译
```
解释如何正确使用库、CLI 或 SDK 的 Skills。这些可以用于内部库或 Claude Code 有时难以处理的常见库。这些 Skills 通常包含参考代码片段的文件夹以及 Claude 在编写脚本时要避免的陷阱列表。

示例：
- billing-lib — 你的内部计费库：边缘情况、危险点等
- internal-platform-cli — 你的内部 CLI 包装器的每个子命令，以及何时使用它们的示例
- frontend-design — 让 Claude 更擅长你的设计系统
```

---

## 2. Product Verification (产品验证)

### 英文原文
```
Skills that describe how to test or verify that your code is working. These are often paired with an external tool like playwright, tmux, etc. for doing the verification.

Verification skills are extremely useful for ensuring Claude's output is correct. It can be worth having an engineer spend a week just making your verification skills excellent.

Consider techniques like having Claude record a video of its output so you can see exactly what it tested, or enforcing programmatic assertions on state at each step. These are often done by including a variety of scripts in the skill.

Examples:
- signup-flow-driver — runs through signup → email verify → onboarding in a headless browser, with hooks for asserting state at each step
- checkout-verifier — drives the checkout UI with Stripe test cards, verifies the invoice actually lands in the right state
- tmux-cli-driver — for interactive CLI testing where the thing you're verifying needs a TTY
```

### 中文翻译
```
描述如何测试或验证代码是否正常工作的 Skills。这些通常与外部工具（如 playwright、tmux 等）配对进行验证。

验证 Skills 对于确保 Claude 的输出是正确的非常有用。值得让工程师花一周时间让你的验证 Skills 变得优秀。

考虑诸如让 Claude 记录其输出的视频，这样你可以确切地看到它测试了什么，或者在每一步对状态强制执行程序化断言等技术。这些通常通过在 Skill 中包含各种脚本来完成。

示例：
- signup-flow-driver — 在无头浏览器中运行 signup → 邮箱验证 → 入职流程，并在每一步都有用于断言状态的挂钩
- checkout-verifier — 使用 Stripe 测试卡驱动结账 UI，验证发票实际上落在正确的状态
- tmux-cli-driver — 用于交互式 CLI 测试，其中你正在验证的东西需要 TTY
```

---

## 3. Data Fetching & Analysis (数据获取和分析)

### 英文原文
```
Skills that connect to your data and monitoring stacks. These skills might include libraries to fetch your data with credentials, specific dashboard ids, etc. as well as instructions on common workflows or ways to get data.

Examples:
- funnel-query — "which events do I join to see signup → activation → paid" plus a table that actually has the canonical user_id
- cohort-compare — compare two cohorts' retention or conversion, flag statistically significant deltas, link to segment definitions
- grafana — datasource UIDs, cluster names, problem → dashboard lookup table
```

### 中文翻译
```
连接到你的数据和监控栈的 Skills。这些 Skills 可能包含使用凭据、特定仪表板 ID 等获取数据的库，以及关于常见工作流或获取数据方式的说明。

示例：
- funnel-query — "我加入哪些事件以查看 signup → activation → paid"加上一个实际上具有规范 user_id 的表
- cohort-compare — 比较两个队列的保留率或转化率，标记统计上显著的差异，链接到段定义
- grafana — 数据源 UID、集群名称、问题 → 仪表板查找表
```

---

## 4. Business Process & Team Automation (业务流程和团队自动化)

### 英文原文
```
Skills that automate repetitive workflows into one command. These skills are usually fairly simple instructions but might have more complicated dependencies on other skills or MCPs. For these skills, saving previous results in log files can help the model stay consistent and reflect on previous executions of the workflow.

Examples:
- standup-post — aggregates your ticket tracker, GitHub activity, and prior Slack → formatted standup, delta-only
- create-<ticket-system>-ticket — enforces schema (valid enum values, required fields) plus post-creation workflow (ping reviewer, link in Slack)
- weekly-recap — merged PRs + closed tickets + deploys → formatted recap post
```

### 中文翻译
```
将重复的工作流自动化为一个命令的 Skills。这些 Skills 通常是相当简单的说明，但可能对其他 Skills 或 MCP 有更复杂的依赖。对于这些 Skills，将以前的结果保存在日志文件中可以帮助模型保持一致并反思工作流的以前执行。

示例：
- standup-post — 聚合你的工单跟踪器、GitHub 活动和以前的 Slack → 格式化的 standup，仅显示变化
- create-<ticket-system>-ticket — 强制执行模式（有效的枚举值、必填字段）加上创建后工作流（ping 审查者，在 Slack 中链接）
- weekly-recap — 合并的 PR + 关闭的工单 + 部署 → 格式化的回顾帖子
```

---

## 5. Code Scaffolding & Templates (代码脚手架和模板)

### 英文原文
```
Skills that generate framework boilerplate for a specific function in your codebase. You might combine these skills with scripts that can be composed. They are especially useful when your scaffolding has natural language requirements that can't be purely covered by code.

Examples:
- new-<framework>-workflow — scaffolds a new service/workflow/handler with your annotations
- new-migration — your migration file template plus common gotchas
- create-app — new internal app with your auth, logging, and deploy config pre-wired
```

### 中文翻译
```
为代码库中的特定功能生成框架样板代码的 Skills。你可以将这些 Skills 与可以组合的脚本结合。当你的脚手架有无法纯粹由代码覆盖的自然语言要求时，这些特别有用。

示例：
- new-<framework>-workflow — 使用你的注释搭建新的服务/工作流/处理程序
- new-migration — 你的迁移文件模板加上常见陷阱
- create-app — 带有你的身份验证、日志记录和部署配置预连线的新内部应用
```

---

## 6. Code Quality & Review (代码质量和审查)

### 英文原文
```
Skills that enforce code quality inside of your org and help review code. These can include deterministic scripts or tools for maximum robustness. You may want to run these skills automatically as part of hooks or inside of a GitHub Action.

Examples:
- adversarial-review — spawns a fresh-eyes subagent to critique, implements fixes, iterates until findings degrade to nitpicks
- code-style — enforces code style, especially styles that Claude does not do well by default.
- testing-practices — instructions on how to write tests and what to test.
```

### 中文翻译
```
在你的组织内强制执行代码质量并帮助审查代码的 Skills。这些可以包括确定性脚本或用于最大稳健性的工具。你可能希望作为 hooks 的一部分或在 GitHub Action 内自动运行这些 Skills。

示例：
- adversarial-review — 生成一个 fresh-eyes 子代理进行批评，实施修复，迭代直到发现降为吹毛求疵
- code-style — 强制执行代码风格，尤其是 Claude 默认做得不好的风格
- testing-practices — 关于如何编写测试以及测试什么的说明
```

---

## 7. CI/CD & Deployment (CI/CD 和部署)

### 英文原文
```
Skills that help you fetch, push, and deploy code inside of your codebase. These skills may reference other skills to collect data.

Examples:
- babysit-pr — monitors a PR → retries flaky CI → resolves merge conflicts → enables auto-merge
- deploy-<service> — build → smoke test → gradual traffic rollout with error-rate comparison → auto-rollback on regression
- cherry-pick-prod — isolated worktree → cherry-pick → conflict resolution → PR with template
```

### 中文翻译
```
帮助你在代码库内获取、推送和部署代码的 Skills。这些 Skills 可以引用其他 Skills 来收集数据。

示例：
- babysit-pr — 监控 PR → 重试不稳定的 CI → 解决合并冲突 → 启用自动合并
- deploy-<service> — 构建 → 冒烟测试 → 使用错误率比较的渐进式流量推出 → 回退时的自动回滚
- cherry-pick-prod — 隔离的工作树 → cherry-pick → 冲突解决 → 带模板的 PR
```

---

## 8. Runbooks (运维手册)

### 英文原文
```
Skills that take a symptom (such as a Slack thread, alert, or error signature), walk through a multi-tool investigation, and produce a structured report.

Examples:
- <service>-debugging — maps symptoms → tools → query patterns for your highest-traffic services
- oncall-runner — fetches alert → checks the usual suspects → formats a finding
- log-correlator — given a request ID, pulls matching logs from every system that might have touched it
```

### 中文翻译
```
获取症状（如 Slack 线程、警报或错误签名），通过多工具调查进行，并生成结构化报告的 Skills。

示例：
- <service>-debugging — 映射症状 → 工具 → 针对你最高流量服务的查询模式
- oncall-runner — 获取警报 → 检查常用嫌疑人 → 格式化发现
- log-correlator — 给定请求 ID，从可能触及它的每个系统提取匹配的日志
```

---

## 9. Infrastructure Operations (基础设施运维)

### 英文原文
```
Skills that perform routine maintenance and operational procedures — some of which involve destructive actions that benefit from guardrails. These make it easier for engineers to follow best practices in critical operations.

Examples:
- <resource>-orphans — finds orphaned pods/volumes → posts to Slack → soak period → user confirms → cascading cleanup
- dependency-management — your org's dependency approval workflow
- cost-investigation — "why did our storage/egress bill spike" with specific buckets and query patterns
```

### 中文翻译
```
执行例行维护和操作程序的 Skills — 其中一些涉及受益于护栏的破坏性操作。这些使工程师更容易在关键操作中遵循最佳实践。

示例：
- <resource>-orphans — 查找孤立的 pod/卷 → 发布到 Slack → 浸泡期 → 用户确认 → 级联清理
- dependency-management — 你组织的依赖项批准工作流
- cost-investigation — "为什么我们的存储/出口账单飙升"具有特定存储桶和查询模式
```

---

## Tips for Making Skills (制作 Skills 的技巧)

![Skills 制作技巧](https://x.com/trq212/article/2033949937936085378/media/2033949742137544704)

### 英文原文
```
Once you've decided on the skill to make, how do you write it? These are some of the best practices, tips, and tricks we've found. We also recently released Skill Creator to make it easier to create skills in Claude Code.
```

### 中文翻译
```
一旦你决定了要制作的 Skill，你如何编写它？这些是我们发现的一些最佳实践、提示和技巧。我们最近还发布了 Skill Creator，以使在 Claude Code 中创建 Skills 变得更容易。
```

---

### Don't State the Obvious (不要陈述显而易见的内容)

### 英文原文
```
Claude Code knows a lot about your codebase, and Claude knows a lot about coding, including many default opinions. If you're publishing a skill that is primarily about knowledge, try to focus on information that pushes Claude out of its normal way of thinking.

The frontend design skill is a great example — it was built by one of the engineers at Anthropic by iterating with customers on improving Claude's design taste, avoiding classic patterns like Inter font and purple gradients.
```

### 中文翻译
```
Claude Code 对你的代码库了解很多，Claude 对编码了解很多，包括许多默认观点。如果你正在发布一个主要关于知识的 Skill，尝试专注于将 Claude 推出其正常思维方式的信息。

前端设计 Skill 是一个很好的例子 — 它是由 Anthropic 的一位工程师通过与客户迭代改进 Claude 的设计品味而构建的，避免经典模式如 Inter 字体和紫色渐变。
```

---

### Build a Gotchas Section (构建陷阱部分)

![Gotchas 部分示例](https://x.com/trq212/article/2033949937936085378/media/2033779922590961669)

### 英文原文
```
The highest-signal content in any skill is the Gotchas section. These sections should be built up from common failure points that Claude runs into when using your skill. Ideally, you will update your skill over time to capture these gotchas.
```

### 中文翻译
```
任何 Skill 中最高信噪比的内容是陷阱（Gotchas）部分。这些部分应该从 Claude 在使用你的 Skill 时遇到的常见失败点构建。理想情况下，你会随着时间的推移更新你的 Skill 以捕获这些陷阱。
```

---

### Use File System & Progressive Disclosure (使用文件系统和渐进式披露)

![文件系统和渐进式披露示例](https://x.com/trq212/article/2033949937936085378/media/2033780423952896002)

### 英文原文
```
Like we said earlier, a skill is a folder, not just a markdown file. You should think of the entire file system as a form of context engineering and progressive disclosure. Tell Claude what files are in your skill, and it will read them at appropriate times.

The simplest form of progressive disclosure is to point to other markdown files for Claude to use. For example, you may split detailed function signatures and usage examples into references/api.md. Another example: if your end output is a markdown file, you might include a template file for it in assets/ to copy and use.

You can have folders of references, scripts, examples, etc., which help Claude work more effectively.
```

### 中文翻译
```
就像我们之前说的，Skill 是文件夹，而不仅仅是 markdown 文件。你应该将整个文件系统视为一种上下文工程和渐进式披露的形式。告诉 Claude 你的 Skill 中有什么文件，它会在适当的时候读取它们。

渐进式披露的最简单形式是指向其他 markdown 文件供 Claude 使用。例如，你可以将详细的函数签名和使用示例拆分到 references/api.md 中。另一个例子：如果你的最终输出是 markdown 文件，你可以在 assets/ 中包含一个模板文件供复制和使用。

你可以有引用、脚本、示例等的文件夹，这些帮助 Claude 更有效地工作。
```

---

### Avoid Railroading Claude (避免限制 Claude)

![避免限制 Claude 示例](https://x.com/trq212/article/2033949937936085378/media/2033780654052413443)

### 英文原文
```
Claude will generally try to stick to your instructions, and because Skills are so reusable you'll want to be careful of being too specific in your instructions. Give Claude the information it needs, but give it the flexibility to adapt to the situation. For example:
```

### 中文翻译
```
Claude 通常会尝试坚持你的说明，而且因为 Skills 如此可重用，你会希望小心不要在说明中过于具体。给 Claude 它需要的信息，但给它适应情况的灵活性。例如：
```

---

### Think through the Setup (考虑设置)

![设置配置示例](https://x.com/trq212/article/2033949937936085378/media/2033780772872851462)

### 英文原文
```
Some skills may need to be set up with context from the user. For example, if you are making a skill that posts your standup to Slack, you may want Claude to ask which Slack channel to post it in.

A good pattern to do this is to store this setup information in a config.json file in the skill directory like the above example. If the config is not set up, the agent can then ask the user for information.

If you want the agent to present structured, multiple choice questions you can instruct Claude to use the AskUserQuestion tool.
```

### 中文翻译
```
一些 Skills 可能需要从用户那里设置上下文。例如，如果你正在制作一个将你的 standup 发布到 Slack 的 Skill，你可能希望 Claude 询问要在哪个 Slack 频道中发布。

这样做的一个好模式是在 Skill 目录中的 config.json 文件中存储此设置信息，如上面的示例所示。如果未设置 config，则代理可以询问用户信息。

如果你希望代理呈现结构化的多选题，你可以指示 Claude 使用 AskUserQuestion 工具。
```

---

### The Description Field Is For the Model (描述字段是给模型的)

![描述字段示例](https://x.com/trq212/article/2033949937936085378/media/2033780836705964036)

### 英文原文
```
When Claude Code starts a session, it builds a listing of every available skill with its description. This listing is what Claude scans to decide "is there a skill for this request?" Which means the description field is not a summary — it's a description of when to trigger this skill.
```

### 中文翻译
```
当 Claude Code 启动会话时，它会构建每个可用 Skill 及其描述的列表。这个列表是 Claude 扫描以决定"是否有针对此请求的 Skill？"的内容。这意味着描述字段不是摘要 — 它是关于何时触发此 Skill 的描述。
```

---

### Memory & Storing Data (内存和存储数据)

![内存和存储数据示例](https://x.com/trq212/article/2033949937936085378/media/2033947639721693189)

### 英文原文
```
Some skills can include a form of memory by storing data within them. You could store data in anything as simple as an append-only text log file or JSON files, or as complicated as a SQLite database.

For example, a standup-post skill might keep a standups.log with every post it's written, which means the next time you run it, Claude reads its own history and can tell what's changed since yesterday. Data stored in the skill directory may be deleted when you upgrade the skill, so you should store this in a stable folder, as of today we provide `${CLAUDE_PLUGIN_DATA}` as a stable folder per plugin to store data in.
```

### 中文翻译
```
一些 Skills 可以通过在其中存储数据来包含一种形式的内存。你可以将数据存储在任何东西中，从简单的仅追加文本日志文件或 JSON 文件，到复杂的 SQLite 数据库。

例如，standup-post Skill 可能会保留一个包含它所写的每篇帖子的 standups.log，这意味着下次你运行它时，Claude 读取自己的历史记录并可以告诉自昨天以来发生了什么变化。存储在 Skill 目录中的数据可能会在你升级 Skill 时被删除，所以你应该将其存储在稳定的文件夹中，从今天开始我们提供 `${CLAUDE_PLUGIN_DATA}` 作为每个插件存储数据的稳定文件夹。
```

---

### Store Scripts & Generate Code (存储脚本和生成代码)

![存储脚本示例](https://x.com/trq212/article/2033949937936085378/media/2033781427637293056)

### 英文原文
```
One of the most powerful tools you can give Claude is code. Giving Claude scripts and libraries lets Claude spend its turns on composition, deciding what to do next rather than reconstructing boilerplate.

For example, in your data science skill you might have a library of functions to fetch data from your event source. In order for Claude to do complex analysis, you could give it a set of helper functions like so:

[Code example image follows]
```

![生成的脚本示例](https://x.com/trq212/article/2033949937936085378/media/2033781485233491968)

### 英文原文（续）
```
Claude can then generate scripts on the fly to compose this functionality to do more advanced analysis for prompts like "What happened on Tuesday?"
```

### 中文翻译
```
你可以给 Claude 的最强大的工具之一是代码。给 Claude 脚本和库让 Claude 在其回合中专注于组合、决定下一步要做什么，而不是重建样板代码。

例如，在你的数据科学 Skill 中，你可能有一个从事件源获取数据的函数库。为了让 Claude 进行复杂的分析，你可以给它一组像这样的辅助函数：

[代码示例图片跟随]

然后 Claude 可以动态生成脚本来组合此功能，以便对像"星期二发生了什么？"这样的提示进行更高级的分析。
```

---

### On Demand Hooks (按需挂钩)

### 英文原文
```
Skills can include hooks that are only activated when the skill is called, and last for the duration of the session. Use this for more opinionated hooks that you don't want to run all the time, but are extremely useful sometimes.

For example:
- /careful — blocks rm -rf, DROP TABLE, force-push, kubectl delete via PreToolUse matcher on Bash. You only want this when you know you're touching prod — having it always on would drive you insane
- /freeze — blocks any Edit/Write that's not in a specific directory. Useful when debugging: "I want to add logs but I keep accidentally 'fixing' unrelated code"
```

### 中文翻译
```
Skills 可以包含仅在调用 Skill 时激活并在会话持续时间内存在的挂钩。将这些用于你不希望一直运行但在某些时候极其有用的更固执的挂钩。

例如：
- /careful — 通过 Bash 上的 PreToolUse 匹配器阻止 rm -rf、DROP TABLE、force-push、kubectl delete。你只希望在你知道你正在接触生产环境时使用它 — 一直开着它会让你发疯
- /freeze — 阻止不在特定目录中的任何编辑/写入。调试时有用："我想添加日志但我总是意外地'修复'不相关的代码"
```

---

## Distributing Skills (分发 Skills)

### 英文原文
```
One of the biggest benefits of Skills is that you can share them with the rest of your team. There are two ways you might share skills with others:

- check your skills into your repo (under ./.claude/skills)
- internal plugin marketplace
```

### 中文翻译
```
Skills 的最大好处之一是你可以与团队的其余部分分享它们。你可能与他人分享 Skills 的方式有两种：

- 将你的 skills 检查到你的仓库（在 ./.claude/skills 下）
- 内部插件市场
```

### 英文原文（续）
```
For smaller teams working across relatively few repos, checking your skills into repos works well. But every skill that is checked in also adds a little bit to the context of the model. As you scale, an internal plugin marketplace allows you to distribute skills and let your team decide which ones to install.
```

### 中文翻译（续）
```
对于在相对较少的存储库中工作的较小团队，将你的 skills 检查到存储库效果很好。但是每个检查的 skill 也会给模型的上下文增加一点点。当你扩展时，内部插件市场允许你分发 skills 并让你的团队决定安装哪些 skills。
```

---

### Managing a Marketplace (管理市场)

### 英文原文
```
How do you decide which skills go in a marketplace? How do people submit them?

We don't have a centralized team that decides; instead we try and find the most useful skills organically. If you have a skill that you want people to try out, you can upload it to a sandbox folder in GitHub and point people to it in Slack or other forums.

Once a skill has gotten traction (which is up to the skill owner to decide), they can put in a PR to move it into the marketplace.

A note of warning, it can be quite easy to create bad or redundant skills, so making sure you have some method of curation before release is important.
```

### 中文翻译
```
你如何决定哪些 skills 进入市场？人们如何提交它们？

我们没有集中的决策团队；相反，我们尝试有机地找到最有用的 skills。如果你有一个希望人们尝试的 skill，你可以将其上传到 GitHub 中的沙箱文件夹，并在 Slack 或其他论坛中指向它。

一旦一个 skill 获得了关注（这由 skill 所有者决定），他们可以提交 PR 将其移动到市场中。

一个警告说明，创建糟糕或冗余的 skills 可能很容易，因此在发布之前确保你有某种策划方法很重要。
```

---

### Composing Skills (组合 Skills)

### 英文原文
```
You may want to have skills that depend on each other. For example, you may have a file upload skill that uploads a file, and a CSV generation skill that makes a CSV and uploads it. This sort of dependency management is not natively built into marketplaces or skills yet, but you can just reference other skills by name, and the model will invoke them if they are installed.
```

### 中文翻译
```
你可能希望有相互依赖的 skills。例如，你可能有一个上传文件的文件上传 skill，以及一个生成 CSV 并上传它的 CSV 生成 skill。这种依赖管理不是市场或 skills 原生内置的，但你可以仅按名称引用其他 skills，如果它们已安装，模型将调用它们。
```

---

### Measuring Skills (衡量 Skills)

### 英文原文
```
To understand how a skill is doing, we use a PreToolUse hook that lets us log skill usage within the company (example code here). This means we can find skills that are popular or are under-triggering compared to our expectations.
```

### 中文翻译
```
为了了解 skill 的表现如何，我们使用 PreToolUse 挂钩，它让我们在公司内记录 skill 使用（示例代码在这里）。这意味着我们可以找到比我们的预期更受欢迎或触发的 skills。
```

---

## Conclusion (结论)

### 英文原文
```
Skills are incredibly powerful, flexible tools for agents, but it's still early and we're all figuring out how to use them best. Think of this more as a grab bag of useful tips that we've seen work than a definitive guide. The best way to understand skills is to get started, experiment, and see what works for you. Most of ours began as a few lines and a single gotcha, and got better because people kept adding to them as Claude hit new edge cases.

I hope this was helpful, let me know if you have any questions.
```

### 中文翻译
```
Skills 对于代理来说是极其强大、灵活的工具，但这仍然处于早期阶段，我们都在弄清楚如何最好地使用它们。将此更多地视为一袋我们看到的有效的有用技巧，而不是一个确定的指南。理解 skills 的最好方法是开始、实验，并看看什么对你有效。我们的大多数都是从几行和一个陷阱开始的，并且随着 Claude 遇到新的边缘情况人们不断添加它们而变得更好。

我希望这有帮助，如果你有任何问题，请告诉我。
```

---

## 📊 词汇表

| 英文 | 中文 | 解释 |
|------|------|------|
| Skills | 技能/能力 | Claude Code 的扩展点 |
| Extension points | 扩展点 | 可扩展的功能接口 |
| Flexible | 灵活的 | 适应性强，易于定制 |
| Distribute | 分发 | 传播和分享 |
| Agents | 代理/智能体 | AI 助手或自动化工具 |
| Build on | 基于构建 | 在...基础上开发 |
| Gotchas | 陷阱/注意事项 | 常见问题和失败点 |
| Progressive disclosure | 渐进式披露 | 逐步提供信息 |
| Context engineering | 上下文工程 | 通过提供上下文来引导 AI |
| Railroading | 限制/强制定向 | 过度限制，不给灵活性 |
| Hooks | 挂钩 | 在特定事件时执行的代码 |
| Marketplace | 市场 | 插件/Skills 分发平台 |
| Traction | 关注度/受欢迎程度 | 受欢迎程度 |
| Boilerplate | 样板代码 | 标准化的代码模板 |
| Scaffolding | 脚手架 | 项目结构搭建 |
| Deterministic | 确定性的 | 可预测的，相同的输入总是产生相同的输出 |
| CI/CD | 持续集成/持续部署 | 自动化构建和部署流程 |
| Runbooks | 运维手册 | 系统运维和故障排除指南 |
| PreToolUse hook | PreToolUse 挂钩 | 在工具使用前执行的代码 |

---

## 💡 学习笔记 / Learning Notes

### 为什么这很重要？

**英文**: Understanding how to build and use skills in Claude Code is crucial for maximizing productivity and building effective AI agents.

**中文**: 理解如何在 Claude Code 中构建和使用 Skills，对于最大化生产力和构建有效的 AI 代理至关重要。

---

### 实际应用

**英文**: These skills patterns can be applied across various domains including development, operations, and automation.

**中文**: 这些 Skills 模式可以应用于各个领域，包括开发、运维和自动化。

---

## 🎓 学习总结 / Learning Summary

### 今天学到

1. ✅ **Skills 的本质**：不仅仅是 markdown 文件，而是包含脚本、资源、数据的文件夹
2. ✅ **9 种 Skills 类型**：从库参考到基础设施运维
3. ✅ **制作技巧**：渐进式披露、避免限制 Claude、构建陷阱部分
4. ✅ **分发策略**：内部市场、有机发现、PR 提交流程
5. ✅ **作者经验**：数百个 Skills 在活跃使用中，持续改进

### 下一步学习

- [ ] 深入学习每种 Skills 类型的具体实现
- [ ] 实践制作自己的 Skills
- [ ] 探索社区分享的 Skills
- [ ] 研究 MCPs (Model Context Protocols)

---

## 📝 备注

这篇文章是 Anthropic 内部团队分享的 Claude Code Skills 实战经验，包含 9 大 Skills 类型分类、编写技巧和团队分发策略。

这是由 @PawelHuryn 转发的内容，原作者是 Thariq Shihipar (@trq212)。

内容质量极高，值得深入学习并实践。

---

## 📅 备份信息

- **备份时间**: 2026-03-24 13:35
- **本地路径**: `/Users/aizhushou/.openclaw/workspace/backup/claude-code-skills-pawelhuryn-2026-03-24/README.md`
- **NAS 路径**: `/Volumes/公共空间/龙虾/测试/claude-code-skills-pawelhuryn-2026-03-24/README.md`
- **备份人**: 铁蛋 🛡️

---

## 🔗 相关链接

- **转发链接**: https://x.com/PawelHuryn/status/2025470280945041547
- **原始文章**: https://x.com/trq212/article/2033949937936085378
- **作者 X**: https://x.com/trq212
- **作者 GitHub**: https://github.com/ThariqS
- **Claude Code**: https://claude.ai/code
- **Skills 文档**: https://code.claude.com/docs/en/skills
- **Skill Creator**: https://claude.com/blog/improving-skill-creator-test-measure-and-refine-agent-skills

---

## 📸 文章图片

所有图片均使用原始链接引用，无需下载到本地。

---

**完整文章翻译完成！** 🛡️✨

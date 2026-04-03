---
title: "长推文翻译：17 Best Practices That Make Claude Cowork 100x More Powerful"
date: 2026-03-27T01:33:19+08:00
draft: false
tags: []
---

# 长推文翻译：17 Best Practices That Make Claude Cowork 100x More Powerful

## 帖子信息

### 基本信息
- **作者**：Nav Toor 认证账号 (@heynavtoor)
- **链接**：https://x.com/heynavtoor/status/2028148844891152554
- **发布时间**：2026年3月2日 00:42
- **类型**：长推文（Thread）
- **互动数据**：
  - 回复：67
  - 转帖：594
  - 喜欢：3,533
  - 书签：14,161
  - 观看：216.6万

---

## 📝 中英对照翻译

### 开头部分

**英文原文**：
> I've been using Claude Cowork since January 12, the day it launched. In seven weeks, I've run over 400 Cowork sessions. I've tested every plugin, every connector, every slash command. I've broken it in ways Anthropic probably hasn't seen. And I've figured out the exact practices that separate people who think Cowork is "kind of cool" from people who've replaced half their software stack with it. The gap is enormous. And it has nothing to do with prompting skill. It's about setup. Structure. And seventeen specific practices that most users will never discover on their own because Anthropic doesn't document them. I tested each one. Measured the difference. Here's the complete list — ranked by impact.

**中文翻译**：
> 我从1月12日 Claude Cowork 发布那天就开始使用了。七周内，我运行了超过400次 Cowork 会话。我测试了每一个插件、每一个连接器、每一个斜杠命令。我以 Anthropic 可能都没见过的方式把它搞崩过。我发现了那些认为 Cowork "有点酷" 的人和那些用它替代了一半软件栈的人之间的确切区别。差距是巨大的。这与提示词技巧无关。而是关于设置。结构。以及17个具体实践，大多数用户永远不会自己发现，因为 Anthropic 没有文档记录它们。我测试了每一个。测量了差异。这是完整列表——按影响力排序。

---

## 🎯 Part 1: Context architecture (practices 1–5)
**第一部分：上下文架构（实践 1-5）**

> These five practices alone will transform your Cowork experience. Everything else builds on this foundation.

> 这五个实践 alone 就能改变你的 Cowork 体验。其他一切都建立在这个基础之上。

### 1. Build a _MANIFEST.md for every working folder
**为每个工作文件夹创建 _MANIFEST.md**

**英文原文**：
> This is the single highest-impact practice nobody talks about. Here's the problem. When you point Cowork at a folder, Claude reads everything. Every file. Every subfolder. Every outdated draft and superseded version. A developer on DEV Community documented this after a 462-file consulting folder started producing contradictory output — Claude was pulling context from pricing models that had been replaced three months earlier. The fix: a _MANIFEST.md file you drop into any working folder. It tells Claude which documents are the source of truth, which subfolders map to which domains, and what to skip entirely. Structure it in three tiers: Tier 1 (Canonical): The source-of-truth documents Claude must read first. Your brand guidelines. Your project brief. Your current strategy document. Tier 2 (Domain): Subfolders mapped to specific topics. Claude only loads these when the task touches that domain. "/pricing → pricing models and rate cards" or "/research → competitor analysis." Tier 3 (Archival): Old drafts, superseded versions, reference material. Claude ignores these unless you explicitly ask. The underscore prefix keeps it sorted to the top of your folder. Takes five minutes to fill out. Saves hours of confused output. For folders under ten files, you don't need one. For anything bigger and especially project folders that accumulate files over weeks this is non-negotiable.

**中文翻译**：
> 这是没人谈论的单一最高影响力实践。问题在这里。当你把 Cowork 指向一个文件夹时，Claude 会读取所有内容。每个文件。每个子文件夹。每个过时的草稿和被取代的版本。DEV Community 上的一位开发者记录了这个问题——在一个462个文件的咨询文件夹开始产生矛盾输出后——Claude 从三个月前已被替换的定价模型中提取上下文。解决方案：_MANIFEST.md 文件，放入任何工作文件夹。它告诉 Claude 哪些文档是真相来源，哪些子文件夹映射到哪些领域，以及完全跳过什么。用三层结构：第一层（规范）：Claude 必须首先读取的真相来源文档。你的品牌指南。你的项目简介。你当前的策略文档。第二层（领域）：映射到特定主题的子文件夹。Claude 只在任务触及该领域时加载这些。"/pricing → 定价模型和价目表" 或 "/research → 竞品分析。" 第三层（归档）：旧草稿、被取代的版本、参考材料。Claude 忽略这些除非你明确要求。下划线前缀让它排在文件夹顶部。填写需要五分钟。节省数小时的混乱输出。对于少于十个文件的文件夹，你不需要。对于任何更大的文件夹——特别是那些几周来积累文件的项目文件夹——这是不可协商的。

### 2. Use Global Instructions as your permanent operating system
**将 Global Instructions 用作你的永久操作系统**

**英文原文**：
> Settings → Cowork → Edit next to Global Instructions. Most people leave this blank. That's like buying a car and never adjusting the mirrors. Global Instructions load before everything else before your files, before your prompt, before Claude even looks at your folder. They're the baseline behavior that applies to every single session. Mine says: "I'm [name], a [role]. Before starting any task, look for _MANIFEST.md and read Tier 1 files first. Always ask clarifying questions before executing. Show a brief plan before taking action. Default output format: .docx. Never use filler language. Never pad outputs. Quality bar: every deliverable should be client-ready without editing. If confidence is low, say so." This means even my laziest, most rushed prompt still produces calibrated output. Claude always knows who I am. Always reads the right files first. Always asks before guessing. The Global Instructions handle the baseline. Your prompt just handles the task.

**中文翻译**：
> 设置 → Cowork → 编辑 Global Instructions。大多数人留空。这就像买了车却从不调整后视镜。Global Instructions 在其他所有内容之前加载——在你的文件之前，在你的提示词之前，在 Claude 甚至查看你的文件夹之前。它们是适用于每个会话的基线行为。我的是："我是[姓名]，一个[角色]。在开始任何任务之前，查找 _MANIFEST.md 并首先读取第一层文件。总是在执行之前询问澄清问题。在采取行动之前展示一个简要计划。默认输出格式：.docx。从不使用填充语言。从不填充输出。质量标准：每个可交付成果都应该无需编辑即可客户就绪。如果信心不足，说出来。" 这意味着即使我最懒、最匆忙的提示词也能产生校准的输出。Claude 总是知道我是谁。总是先读取正确的文件。总是在猜测之前询问。Global Instructions 处理基线。你的提示词只处理任务。

### 3. Create three persistent context files
**创建三个持久上下文文件**

**英文原文**：
> I covered this in depth in my previous article, but it's too important not to repeat here. Create a folder called "Claude Context" (or "00_Context" so it sorts first). Add three files: about-me.md Your professional identity. Not your resume. What you actually do, who you serve, what your current priorities are, and one or two examples of your best work. brand-voice.md — Your communication style. Tone descriptors, words you use, words you never use, formatting preferences, and two to three paragraphs of your actual writing as reference. working-style.md How Claude should behave. Collaboration rules, output format defaults, quality standards, and a list of things to avoid. These three files eliminate the "generic AI output" problem overnight. Without them, every session starts cold. With them, Claude starts every session already knowing your voice, your standards, and your preferences. The key insight most people miss: these files compound. Refine them weekly. Every time Claude produces something you don't like, ask yourself whether it's a prompt problem or a context problem. Nine times out of ten, it's context. Add one line to one file. Permanent fix.

**中文翻译**：
> 我在前一篇文章中深入介绍了这个，但它太重要了，不能不在这里重复。创建一个名为 "Claude Context" 的文件夹（或 "00_Context" 让它排在第一位）。添加三个文件：about-me.md 你的职业身份。不是你的简历。你实际做什么、为谁服务、你当前的优先事项是什么，以及一两个你最好作品的例子。brand-voice.md——你的沟通风格。语气描述词、你使用的词、你从不使用的词、格式偏好，以及两到三段你实际写作作为参考。working-style.md Claude 应该如何表现。协作规则、输出格式默认值、质量标准，以及要避免的事项列表。这三个文件 overnight 消除了"通用 AI 输出"问题。没有它们，每个会话都是冷启动。有了它们，Claude 在每个会话开始时就已经知道你的声音、你的标准和你的偏好。大多数人错过的关键洞察：这些文件会复合。每周完善它们。每次 Claude 产生你不喜欢的东西时，问问自己这是提示词问题还是上下文问题。十分之九，是上下文。给一个文件添加一行。永久修复。

### 4. Use Folder Instructions for project-specific context
**使用 Folder Instructions 获取项目特定上下文**

**英文原文**：
> Global Instructions are the same for every session. Folder Instructions are specific to whatever folder you're working in. When you select a folder in Cowork, Claude can read and update Folder Instructions automatically. But you can also set them manually. This is where you put project-specific rules: client name, project goals, specific terminology, deliverable formats, review deadlines. The layering matters. Global Instructions set universal behavior. Folder Instructions add project context. Your prompt specifies the task. Three layers, each one more specific than the last. This is how you go from "generic AI" to "this sounds like it came from someone who's been on my team for six months."

**中文翻译**：
> Global Instructions 对每个会话都是一样的。Folder Instructions 特定于你正在工作的文件夹。当你在 Cowork 中选择一个文件夹时，Claude 可以自动读取和更新 Folder Instructions。但你也可以手动设置它们。这是你放置项目特定规则的地方：客户名称、项目目标、特定术语、可交付成果格式、审核截止日期。分层很重要。Global Instructions 设置通用行为。Folder Instructions 添加项目上下文。你的提示词指定任务。三层，每一层都比前一层更具体。这就是你从"通用 AI"到"这听起来像来自我团队中待了六个月的人"的方式。

### 5. Never let Claude read everything scope your context deliberately
**永远不要让 Claude 读取所有内容——有意识地限定你的上下文**

**英文原文**：
> This is the practice that separates power users from everyone else. Claude's context window is enormous over a million tokens on Opus 4.6. But bigger context doesn't mean better output. In fact, the opposite is often true. The more irrelevant files Claude reads, the more noise enters its reasoning, and the worse your output gets. Tell Claude what to read. In your Global Instructions, add: "When starting any task, look for _MANIFEST.md first. Load Tier 1 files. Only load Tier 2 files when the task explicitly touches that domain. Never load Tier 3 files unless I specifically ask." If you're using subagents, scope them even tighter: "When decomposing tasks into subagents, give each subagent only the minimum context it needs for its specific subtask." Deliberate context management is the single biggest differentiator between Cowork users who get inconsistent results and Cowork users who get reliable, high-quality output every time.

**中文翻译**：
> 这是区分高级用户和其他人的实践。Claude 的上下文窗口是巨大的——在 Opus 4.6 上超过一百万 token。但更大的上下文并不意味着更好的输出。事实上，相反的情况往往是真的。Claude 读取的无关文件越多，进入其推理的噪音就越多，你的输出就越差。告诉 Claude 要读取什么。在你的 Global Instructions 中，添加："在开始任何任务时，首先查找 _MANIFEST.md。加载第一层文件。只在任务明确触及该领域时加载第二层文件。永远不要加载第三层文件，除非我特别要求。"如果你在使用子代理，更严格地限定它们："在将任务分解为子代理时，只给每个子代理其特定子任务所需的最小上下文。"有意识的上下文管理是获得不一致结果的 Cowork 用户和每次都能获得可靠、高质量输出的 Cowork 用户之间最大的区别因素。

---

## 🎯 Part 2: Task design (practices 6–10)
**第二部分：任务设计（实践 6-10）**

> How you frame a task determines whether Cowork delivers a finished product or an expensive rough draft.

> 你如何构建任务决定了 Cowork 是交付成品还是昂贵的草稿。

### 6. Define the end state, not the process
**定义最终状态，而不是过程**

**英文原文**：
> This is the mindset shift that changes everything. Cowork isn't a chatbot. It's a coworker. You don't tell a coworker how to do their job step by step. You tell them what "done" looks like. Bad prompt: "Help me with my files." Good prompt: "Organize all files in this folder into subfolders by client name. Use the format YYYY-MM-DD-descriptive-name for all filenames. Create a summary log documenting every change. Don't delete anything. If a file could belong to multiple clients, put it in /needs-review." The second prompt defines the end state (organized folders), the naming convention, the output artifact (summary log), the safety constraint (no deletion), and the uncertainty protocol (needs-review folder). Claude can now execute autonomously and you can walk away. Every task prompt should answer three questions: What does "done" look like? What are the constraints? What should Claude do when it's uncertain?

**中文翻译**：
> 这是改变一切的心态转变。Cowork 不是聊天机器人。它是同事。你不会一步步告诉同事如何做他们的工作。你告诉他们"完成"是什么样子的。糟糕的提示词："帮我处理我的文件。"好的提示词："将这个文件夹中的所有文件按客户名称整理到子文件夹中。对所有文件名使用 YYYY-MM-DD-描述性名称 格式。创建一个总结日志记录每个更改。不要删除任何东西。如果一个文件可能属于多个客户，把它放在 /needs-review。"第二个提示词定义了最终状态（有序的文件夹）、命名约定、输出产物（总结日志）、安全约束（不删除）和不确定性协议（needs-review 文件夹）。Claude 现在可以自主执行，你可以走开。每个任务提示词应该回答三个问题："完成"是什么样子的？约束是什么？当 Claude 不确定时应该做什么？

### 7. Always request a plan before execution
**总是在执行之前要求一个计划**

**英文原文**：
> Add this to your Global Instructions: "Show a brief plan before taking action on any task. Wait for my approval before executing." This single line prevents 90% of Cowork disasters. Without it, Claude reads your prompt and immediately starts executing. Sometimes it's exactly right. Sometimes it misinterprets one word and reorganizes three months of files in the wrong direction. With the plan step, you get a 30-second review window. "I'm going to create these six subfolders, move these files, rename them using this convention, and save a log here. Proceed?" You scan it. It looks right. You approve. Claude executes. The cost: an extra 30 seconds per task. The benefit: you never have to undo a 20-minute autonomous mistake.

**中文翻译**：
> 把这添加到你的 Global Instructions："在对任何任务采取行动之前展示一个简要计划。在执行之前等待我的批准。"这一行防止了90%的 Cowork 灾难。没有它，Claude 读取你的提示词并立即开始执行。有时它是完全正确的。有时它误解一个词并以错误的方向重新组织三个月的文件。有了计划步骤，你得到一个30秒的审查窗口。"我要创建这六个子文件夹，移动这些文件，使用这个约定重命名它们，并在这里保存一个日志。继续？"你扫描它。它看起来正确。你批准。Claude 执行。成本：每个任务额外的30秒。好处：你永远不必撤销一个20分钟的自主错误。

### 8. Tell Claude what to do with uncertainty
**告诉 Claude 如何处理不确定性**

**英文原文**：
> This is the most underrated practice in the entire list. Most people give Claude clear instructions for the happy path but say nothing about edge cases. What happens when a receipt image is blurry? When a file could belong to two categories? When a data source is incomplete? Claude will guess. And Claude's guesses are often wrong not because it's stupid, but because it doesn't know your preferences for ambiguous situations. Build uncertainty handling into every task: "If a date isn't clear, mark it as VERIFY. If a file could go in multiple folders, put it in /needs-review. If you're less than 80% confident in a classification, flag it instead of guessing." This transforms Cowork from a tool that sometimes produces errors into a tool that tells you exactly where it needs your judgment. That's a fundamentally different value proposition.

**中文翻译**：
> 这是整个列表中最被低估的实践。大多数人给 Claude 清晰的快乐路径指令，但对边缘情况只字不提。当收据图像模糊时会发生什么？当一个文件可能属于两个类别时？当数据源不完整时？Claude 会猜测。Claude 的猜测往往是错的——不是因为它愚蠢，而是因为它不知道你对模糊情况的偏好。在每个任务中构建不确定性处理："如果日期不清楚，标记为 VERIFY。如果一个文件可能放在多个文件夹中，把它放在 /needs-review。如果你对分类的信心低于80%，标记它而不是猜测。"这将 Cowork 从有时产生错误的工具转变为准确告诉你它在哪里需要你的判断的工具。这是一个根本不同的价值主张。

### 9. Batch related work into single sessions
**将相关工作批处理到单个会话中**

**英文原文**：
> Every Cowork session has startup cost. Claude reads your files, loads your context, processes your folder structure. That's compute you're paying for. Don't run five separate sessions for five related tasks. Run one session: "I need to process this month's expense receipts, update the budget spreadsheet, generate a summary report, draft an email to finance, and save everything to /monthly-reports/february." Claude plans all five tasks, shares context across them (the receipt data feeds into the budget which feeds into the report which feeds into the email), and produces five connected deliverables in one run. Faster. Cheaper. Higher quality because the context from each task informs the next. If you're hitting usage limits, this is usually the fix. Fewer sessions with more tasks per session is almost always better than many sessions with one task each.

**中文翻译**：
> 每个 Cowork 会话都有启动成本。Claude 读取你的文件，加载你的上下文，处理你的文件夹结构。这是你在支付的计算。不要为五个相关任务运行五个单独的会话。运行一个会话："我需要处理这个月的费用收据，更新预算电子表格，生成一份总结报告，起草一封给财务的邮件，并把所有内容保存到 /monthly-reports/february。" Claude 计划所有五个任务，在它们之间共享上下文（收据数据输入预算，预算输入报告，报告输入邮件），并在一个运行中产生五个相互关联的可交付成果。更快。更便宜。更高质量，因为每个任务的上下文都会通知下一个。如果你达到使用限制，这通常是解决方案。每个会话有更多任务的更少会话几乎总是比每个会话一个任务的许多会话更好。

### 10. Use subagents deliberately by asking for parallel processing
**通过要求并行处理来有意识地使用子代理**

**英文原文**：
> Cowork's most powerful feature is one most users never trigger. When you give Cowork a task with independent parts, it can spin up multiple subagents to work on them simultaneously. Each subagent gets fresh context, tackles its piece, and hands results back to the main agent for synthesis. How to trigger it: include "Spin up subagents to..." or "Work on these in parallel using subagents" in your prompt. Example: "I'm evaluating four vendors. Spin up subagents to research each one's pricing, support reputation, and integration options. Give me a comparison table." Instead of researching sequentially vendor A, then B, then C, then D Cowork launches four parallel agents. The task that used to take 40 minutes takes 10. Use it for: competitive analysis, multi-source research, processing batches of files, evaluating options from different angles (financial, operational, customer experience), and any task where subtasks don't depend on each other. Caveat: subagents work best on Opus 4.6 and consume more tokens. Use them for complex tasks where the time savings justify the cost. Don't use them to organize your Downloads folder.

**中文翻译**：
> Cowork 最强大的功能是大多数用户从未触发的功能。当你给 Cowork 一个具有独立部分的任务时，它可以启动多个子代理同时处理它们。每个子代理获得新鲜的上下文，处理它的部分，并将结果交回给主代理进行综合。如何触发它：在你的提示词中包含"启动子代理来..."或"使用子代理并行处理这些"。示例："我正在评估四个供应商。启动子代理来研究每个供应商的定价、支持声誉和集成选项。给我一个比较表。" Cowork 不是按顺序研究供应商 A，然后 B，然后 C，然后 D，而是启动四个并行代理。过去需要40分钟的任务现在需要10分钟。用于：竞争分析、多源研究、批处理文件、从不同角度评估选项（财务、运营、客户体验），以及任何子任务不相互依赖的任务。注意事项：子代理在 Opus 4.6 上工作效果最好，并消耗更多 token。将它们用于时间节省证明成本合理的复杂任务。不要用它们来整理你的下载文件夹。

---

## 🎯 Part 3: Automation and scheduling (practices 11–13)
**第三部分：自动化和调度（实践 11-13）**

> This is where Cowork goes from productivity tool to autonomous system.

> 这是 Cowork 从生产力工具转变为自主系统的地方。

### 11. Schedule recurring tasks with /schedule
**使用 /schedule 安排重复任务**

**英文原文**：
> Type /schedule in any Cowork task. Claude walks you through setting up a task that runs automatically daily, weekly, monthly, or on demand. The best scheduled tasks I've set up: Monday morning briefing: "Every Monday at 7 AM, check my Slack channels and calendar for the week. Summarize what's coming up, flag anything that needs prep, and save a briefing to /weekly-briefings." Friday status report: "Every Friday at 4 PM, pull my completed tasks from Asana, summarize what I shipped this week, draft a status update, and save to /reports." Daily competitor tracking: "Every day at 9 AM, research [competitor names] for news, product updates, or pricing changes. Save a summary only if there's something new." Critical limitation: scheduled tasks only run when your computer is awake and Claude Desktop is open. If your machine is asleep when a task is due, Cowork catches up when you're back and notifies you. Plan around this.

**中文翻译**：
> 在任何 Cowork 任务中输入 /schedule。Claude 会引导你设置一个每天、每周、每月或按需自动运行的任务。我设置的最佳定时任务：周一早晨简报："每周一早上7点，检查我的 Slack 频道和本周日历。总结即将发生的事情，标记任何需要准备的事项，并将简报保存到 /weekly-briefings。"周五状态报告："每周五下午4点，从我的 Asana 中提取已完成的任务，总结本周我交付了什么，起草状态更新，并保存到 /reports。"每日竞品跟踪："每天早上9点，研究[竞争对手名称]的新闻、产品更新或定价变化。只有在有新内容时才保存总结。"关键限制：定时任务只在你电脑醒着且 Claude Desktop 打开时运行。如果你的机器在任务到期时处于睡眠状态，Cowork 会在你回来时补上并通知你。围绕这一点做计划。

### 12. Build once, run weekly externalize everything to files
**构建一次，每周运行——将所有内容外部化到文件**

**英文原文**：
> Cowork has no memory between sessions. This is simultaneously its biggest limitation and its greatest design feature. No memory means no context bleed. No hallucinated recollections from three weeks ago. Every session starts clean. But it also means you can't rely on "Claude remembers how I like this done." The solution: externalize everything to files. Your preferences live in context files. Your project plans live in markdown documents. Your standard operating procedures live in skill files. Your decisions and outcomes live in log files. One power user documented building a weekly review system: 1,500+ lines across five specialized subagent instructions. Built once. Runs weekly. Claude reads the instructions, spins up five parallel agents, each with scoped permissions and defined outputs, and produces a complete weekly review without any new input. If you want continuity, you have to build it into files. But the upside is massive: a well-documented workflow is portable, shareable, and version-controlled. It doesn't live in one AI's memory. It lives in your system.

**中文翻译**：
> Cowork 在会话之间没有记忆。这同时是它最大的限制和最伟大的设计特性。没有记忆意味着没有上下文泄露。没有三周前的幻觉回忆。每个会话都是干净的开始。但这也意味着你不能依赖"Claude 记得我喜欢怎么做这个。"解决方案：将所有内容外部化到文件。你的偏好存在于上下文文件中。你的项目计划存在于 markdown 文档中。你的标准操作程序存在于技能文件中。你的决策和结果存在于日志文件中。一位高级用户记录了构建每周审查系统的过程：五个专门的子代理指令，超过1500行。构建一次。每周运行。Claude 读取指令，启动五个并行代理，每个都有限定权限和定义的输出，并产生一个完整的每周审查，无需任何新输入。如果你想要连续性，你必须将它构建到文件中。但好处是巨大的：一个文档完善的流程是可移植的、可共享的、版本控制的。它不存在于一个 AI 的记忆中。它存在于你的系统中。

### 13. Use the /schedule + connectors combo for real automation
**使用 /schedule + 连接器组合实现真正的自动化**

**英文原文**：
> Scheduled tasks become genuinely powerful when combined with connectors. Connect Gmail, Slack, Google Drive, Notion, Asana, or any of the 50+ available integrations. Then schedule tasks that pull live data: "Every Monday, pull all unread Slack messages from #product-feedback, categorize them by theme, and create a summary in Google Drive." "Every morning, check my Gmail for invoices, extract amounts and dates, and update the expenses spreadsheet in my local /finance folder." This is where Cowork stops being a task executor and starts being an autonomous system. The scheduled task runs. The connector pulls live data. Claude processes it. The output appears in your folder or your connected tool. You review when you're ready. Settings → Connectors → Browse connectors to see what's available. Start with Slack and Gmail. Those two alone will save you hours per week.

**中文翻译**：
> 当与连接器结合时，定时任务变得真正强大。连接 Gmail、Slack、Google Drive、Notion、Asana 或任何50多个可用的集成。然后安排拉取实时数据的任务："每周一，从 #product-feedback 拉取所有未读的 Slack 消息，按主题分类，并在 Google Drive 中创建总结。""每天早上，检查我的 Gmail 中的发票，提取金额和日期，并更新我本地 /finance 文件夹中的费用电子表格。"这是 Cowork 停止作为任务执行者并开始成为自主系统的地方。定时任务运行。连接器拉取实时数据。Claude 处理它。输出出现在你的文件夹或你连接的工具中。你在准备好时审查。设置 → 连接器 → 浏览连接器查看可用的内容。从 Slack 和 Gmail 开始。仅这两个每周就会为你节省数小时。

---

## 🎯 Part 4: Plugins and skills (practices 14–16)
**第四部分：插件和技能（实践 14-16）**

> Plugins are Cowork's modular brain. Skills are its playbook. Most users install one plugin and never look back. That's leaving 80% of the value on the table.

> 插件是 Cowork 的模块化大脑。技能是它的剧本。大多数用户安装一个插件就不再回头。这浪费了80%的价值。

### 14. Stack plugins for compound capability
**堆叠插件以获得复合能力**

**英文原文**：
> Each plugin is a bundle of skills, slash commands, and subagent configurations designed for a specific domain Sales, Legal, Finance, Product Management, Data Analysis, and so on. But here's what most people miss: plugins are composable. You can install multiple plugins and use capabilities from all of them in a single task. Example: Install the Data Analysis plugin and the Sales plugin. Then: "Analyze our Q1 pipeline data (use Data Analysis), identify the three weakest deals, and draft personalized follow-up emails for each (use Sales)." Claude uses capabilities from both plugins in one workflow. My current stack: Productivity (always on), Data Analysis (always on), Sales (for outreach weeks), and Marketing (for content weeks). Rotate the last two based on what I'm focused on. Start with the tier list I published install the S-tier and A-tier plugins that match your role. Then experiment with combinations.

**中文翻译**：
> 每个插件都是为特定领域设计的一包技能、斜杠命令和子代理配置——销售、法律、财务、产品管理、数据分析等等。但大多数人错过的是：插件是可组合的。你可以安装多个插件，并在单个任务中使用它们的所有能力。示例：安装数据分析插件和销售插件。然后："分析我们第一季度的管道数据（使用数据分析），识别三个最弱的交易，并为每个交易起草个性化的跟进邮件（使用销售）。" Claude 在一个工作流中使用两个插件的能力。我当前的堆栈：生产力（始终开启）、数据分析（始终开启）、销售（用于外联周）和营销（用于内容周）。根据我关注的内容轮换最后两个。从我发布的等级列表开始——安装与你角色匹配的 S 级和 A 级插件。然后尝试组合。

### 15. Build custom skills for your specific workflows
**为你的特定工作流构建自定义技能**

**英文原文**：
> A skill is a markdown file that teaches Claude how to approach a specific, repeatable task. Plugins bundle many skills. But you can also create your own. Structure of a custom skill file: # [Skill Name] ## Purpose: What this skill does. ## Inputs: What information Claude needs. ## Process: Step-by-step instructions. ## Output: What the finished deliverable looks like. ## Constraints: Rules and guardrails. Example: I created a "Weekly Article Drafting" skill. Purpose: Draft a 2,000-word article from a topic and outline. Inputs: topic, outline, target audience, key evidence. Process: research using web search, draft sections, match brand-voice.md, generate VISUAL SUGGESTIONS and QUOTABLE LINES. Output: .docx file in /articles/drafts. Constraints: no AI semantic language, no filler phrases, minimum 8 evidence points. Now I say "Run my article drafting skill on [topic]" and get a publication-ready draft. The skill encodes everything I'd normally spend 20 minutes explaining in a prompt. Save custom skills as .md files in your working folder or upload them through the Customize menu. Claude reads them at the start of every relevant session.

**中文翻译**：
> 技能是一个 markdown 文件，教 Claude 如何处理特定的、可重复的任务。插件捆绑了许多技能。但你也可以创建自己的。自定义技能文件的结构：# [技能名称] ## 目的：这个技能做什么。## 输入：Claude 需要什么信息。## 过程：分步说明。## 输出：完成的可交付成果是什么样子的。## 约束：规则和护栏。示例：我创建了一个"每周文章起草"技能。目的：从主题和大纲起草一篇2000字的文章。输入：主题、大纲、目标受众、关键证据。过程：使用网络搜索进行研究，起草章节，匹配 brand-voice.md，生成视觉建议和可引用行。输出：/articles/drafts 中的 .docx 文件。约束：没有 AI 语义语言，没有填充短语，最少8个证据点。现在我说"在[主题]上运行我的文章起草技能"，就会得到一个可发布的草稿。技能编码了我通常在提示词中花费20分钟解释的所有内容。将自定义技能保存为 .md 文件放在你的工作文件夹中，或通过自定义菜单上传。Claude 在每个相关会话开始时读取它们。

### 16. Use the Plugin Management plugin to build plugins conversationally
**使用插件管理插件通过对话构建插件**

**英文原文**：
> This is the most meta feature in Cowork and the most underused. Install the Plugin Management plugin. Then say: "Help me create a plugin for [your workflow]." Claude walks you through defining skills, slash commands, and configuration conversationally. No code. No GitHub. No markdown syntax you need to learn. You describe what you want. Claude builds the plugin. You test it. You refine it. In under an hour, you have a custom plugin that codifies your specific workflow, your specific standards, and your specific terminology. For teams, this is transformative. One person builds a plugin for your team's standard processes. Everyone installs it. Suddenly the whole team produces consistent, on-brand, process-compliant output because the standards live in the plugin, not in individual memory. Enterprise teams: Anthropic launched a private plugin marketplace in February. Admins can create, curate, and distribute custom plugins across the organization. Build once. Deploy to hundreds.

**中文翻译**：
> 这是 Cowork 中最元的功能，也是最未被充分利用的。安装插件管理插件。然后说："帮我为[你的工作流]创建一个插件。" Claude 通过对话引导你定义技能、斜杠命令和配置。没有代码。没有 GitHub。没有你需要的 markdown 语法。你描述你想要什么。Claude 构建插件。你测试它。你完善它。在一个小时内，你有一个自定义插件，将你的特定工作流、你的特定标准、你的特定术语编纂成法典。对于团队来说，这是变革性的。一个人为你的团队的标准流程构建一个插件。每个人都安装它。突然间，整个团队产生一致的、符合品牌的、符合流程的输出，因为标准存在于插件中，而不是个人记忆中。企业团队：Anthropic 在二月推出了一个私有插件市场。管理员可以在整个组织中创建、策划和分发自定义插件。构建一次。部署到数百人。

---

## 🎯 Part 5: Safety and efficiency (practice 17)
**第五部分：安全与效率（实践 17）**

### 17. Treat Cowork like a powerful employee, not a toy
**将 Cowork 视为强大的员工，而不是玩具**

**英文原文**：
> Cowork has real file system access. It can create, move, rename, and with your permission delete files on your actual computer. It can browse the web. It can interact with connected tools. It can run for hours unsupervised. That power demands respect. Here are the non-negotiable safety practices: Back up before experimenting. Especially with file organization tasks. Cowork gets it right most of the time. "Most of the time" isn't good enough for your client contracts. Keep sensitive files in separate folders. Financial documents, passwords, personal information put them in folders Cowork never touches. Don't grant access to your entire Documents directory. Scope tightly. Always add "Don't delete anything" unless you specifically want deletions. Even with deletion protection (Claude asks before deleting), it's better to prevent the request entirely. Monitor the first few runs of any new workflow. Watch what Claude does. Read the plan. Check the output. Once you trust a workflow, you can step away. But earn that trust first. Be aware of prompt injection risk. If Claude reads a malicious document or website, hidden instructions could alter its behavior. Don't point Cowork at untrusted file sources or unfamiliar URLs without reviewing them first. Track your usage. Cowork consumes significantly more of your allocation than regular chat. Complex, multi-step tasks with subagents are compute-intensive. If you're hitting limits, batch related work, use "revise section 2 only" instead of "redo everything," and pre-load context through files instead of re-explaining in chat.

**中文翻译**：
> Cowork 有真正的文件系统访问权限。它可以在你的实际计算机上创建、移动、重命名，并在你的许可下删除文件。它可以浏览网页。它可以与连接的工具交互。它可以无人监督地运行数小时。这种力量需要尊重。以下是不可协商的安全实践：在实验之前备份。特别是对于文件组织任务。Cowork 大部分时间都做得对。"大部分时间"对你的客户合同来说不够好。将敏感文件放在单独的文件夹中。财务文件、密码、个人信息——把它们放在 Cowork 从不触及的文件夹中。不要授予对整个 Documents 目录的访问权限。严格限定范围。总是添加"不要删除任何东西"，除非你特别想要删除。即使有删除保护（Claude 在删除之前询问），完全防止请求更好。监控任何新工作流的前几次运行。观察 Claude 做什么。阅读计划。检查输出。一旦信任一个工作流，你可以走开。但首先要赢得这种信任。注意提示词注入风险。如果 Claude 读取恶意文档或网站，隐藏指令可能改变其行为。不要在没有先审查的情况下将 Cowork 指向不受信任的文件来源或不熟悉的 URL。跟踪你的使用情况。Cowork 比普通聊天消耗更多的配额。复杂的、多步骤的、带有子代理的任务是计算密集型的。如果你达到限制，批处理相关工作，使用"只修改第2节"而不是"重做所有内容"，并通过文件预加载上下文而不是在聊天中重新解释。

---

## 🎯 The pattern behind all 17 practices
**所有17个实践背后的模式**

**英文原文**：
> If you zoom out, every practice on this list follows the same principle: Invest in setup. Reduce prompting. The people struggling with Cowork are writing long, detailed prompts for every task and getting inconsistent results. The people thriving with Cowork spent an afternoon building their context architecture manifest files, global instructions, context files, folder instructions, custom skills and now write ten-word prompts that produce client-ready deliverables. This is the fundamental shift from ChatGPT-era thinking to Cowork-era thinking. ChatGPT rewarded prompt engineering. Cowork rewards system engineering. The prompt is the least important part of a Cowork session. The context, the structure, the skills, and the constraints you've built around it that's where the output quality comes from. As one Substack writer who runs five parallel workflows before breakfast put it: "It feels less like a conversation and more like leaving tasks for a capable coworker." That's the target. Not a chatbot. Not a prompt-and-respond tool. A coworker who already knows your standards, your voice, your projects, and your preferences because you built that knowledge into files it reads every single time.

**中文翻译**：
> 如果你缩小视野，这个列表上的每个实践都遵循相同的原则：投资于设置。减少提示词。与 Cowork 斗争的人正在为每个任务写长而详细的提示词，并得到不一致的结果。在 Cowork 中茁壮成长的人花了一个下午构建他们的上下文架构——清单文件、全局指令、上下文文件、文件夹指令、自定义技能——现在写十个词的提示词，产生可客户就绪的可交付成果。这是从 ChatGPT 时代思维到 Cowork 时代思维的根本转变。ChatGPT 奖励提示词工程。Cowork 奖励系统工程。提示词是 Cowork 会话中最不重要的部分。上下文、结构、技能和你围绕它构建的约束——这才是输出质量的来源。正如一位在早餐前运行五个并行工作流的 Substack 作者所说："这感觉不像对话，更像给一个有能力的同事留下任务。"这就是目标。不是聊天机器人。不是提示词和响应工具。一个已经知道你的标准、你的声音、你的项目、你的偏好的同事——因为你把这些知识构建进了它每次读取的文件中。

---

## ✅ Your implementation checklist
**你的实施清单**

**英文原文**：
> Do these in order. Each one compounds on the last. Today (30 minutes): Create your three context files and set your Global Instructions. This alone puts you ahead of 95% of Cowork users. This week: Add a _MANIFEST.md to your most-used project folder. Install two to three plugins that match your role. Set up one scheduled task. This month: Build your first custom skill for your most repeated workflow. Experiment with subagents on a complex research task. Refine your context files based on output quality. By the end of month one, you'll have a Cowork setup that produces higher-quality output in less time than any AI tool you've used before. The difference between Cowork as a toy and Cowork as a system is seventeen practices and about two hours of setup. The gap between people who know these practices and people who don't is already massive. In six months, it'll be a canyon.

**中文翻译**：
> 按顺序做这些。每个都在上一个的基础上复合。今天（30分钟）：创建你的三个上下文文件并设置你的 Global Instructions。这一点 alone 就让你领先95%的 Cowork 用户。本周：给你最常用的项目文件夹添加一个 _MANIFEST.md。安装两到三个与你角色匹配的插件。设置一个定时任务。本月：为你最重复的工作流构建你的第一个自定义技能。在复杂的研究任务上尝试子代理。根据输出质量完善你的上下文文件。到第一个月结束时，你将拥有一个 Cowork 设置，在比以前使用的任何 AI 工具更短的时间内产生更高质量的输出。Cowork 作为玩具和 Cowork 作为系统之间的区别是十七个实践和大约两小时的设置。知道这些实践的人和不知道的人之间的差距已经很大了。六个月后，它将是一个峡谷。

---

## 🔗 相关资源

### 作者信息
- **X 账号**：@heynavtoor
- **主页**：https://x.com/heynavtoor
- **认证状态**：✅ 认证账号

### 文章统计
- **发布时间**：2026年3月2日 00:42
- **互动数据**：
  - 回复：67
  - 转帖：594
  - 喜欢：3,533
  - 书签：14,161
  - 观看：216.6万

---

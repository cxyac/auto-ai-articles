---
title: "推出 Claude Managed Agents"
date: 2026-04-09T12:10:00+08:00
draft: false
tags: ["Claude", "Managed Agents", "AI", "Anthropic", "Agent"]
---

# 推出 Claude Managed Agents

- **来源**: [X.com - @RLanceMartin](https://x.com/rlancemartin/status/2041927992986009773)
- **作者**: Lance Martin (@RLanceMartin)
- **翻译时间**: 2026-04-09
- **原文标题**: Launching Claude Managed Agents

---

## 正文内容

**TL;DR** – Claude Managed Agents 是一个预构建、可配置的代理 harness，在托管基础设施中运行。你将代理定义为模板——工具、技能、文件/仓库等。代理 harness 和基础设施为你提供。该系统旨在跟上 Claude 快速增长的智能，并支持长周期任务。

**一些有用的链接：**
- [Claude 博客](https://claude.com/blog/claude-managed-agents)：使用模式和客户示例
- [工程博客](https://www.anthropic.com/engineering/managed-agents)：Claude Managed Agents 的设计
- [文档](https://platform.claude.com/docs/en/managed-agents/quickstart)：入门、快速开始、CLI 和 SDK 概述

---

## 为什么推出 Claude Managed Agents

Claude [Messages API](https://platform.claude.com/docs/en/build-with-claude/working-with-messages) 是通往模型的直接通道：它接收消息并返回内容块。在 Messages API 上构建的代理使用 harness 将 Claude 的工具调用路由到处理程序并管理上下文。这带来了一些挑战：

- **Harness 需要跟上 Claude** – 我最近写了一篇[博客](https://claude.com/blog/harnessing-claudes-intelligence)，专注于使用 Claude API 原语构建代理来处理工具编排和上下文管理。但代理 harness 编码了关于 Claude*不能*做什么的假设。随着 Claude 变得更有能力，这些假设会过时，并可能[瓶颈](https://rlancemartin.github.io/2025/07/30/bitter_lesson/) Claude 的性能。Harness 需要不断更新以跟上 Claude。

- **Claude 运行时间更长** – Claude 的[任务周期正在呈指数增长](https://metr.org/time-horizons/)，在 METR 基准测试中已经超过 10 个人类工作小时。这给代理周围的基础设施带来压力：它需要安全、对长周期任务中发生的基础设施故障具有弹性，并支持扩展（例如，到许多代理团队）。

解决这些挑战很重要，因为我们期望未来的 Claude 能够在人类最重大的挑战上运行数天、数周或数月。[Claude Agent SDK](https://platform.claude.com/docs/en/agent-sdk/overview) 是第一步，提供了一个优秀的通用代理 harness。Claude Managed Agents 是这一进展的下一步：一个具有 harness 和托管基础设施的系统，旨在支持我们期望 Claude 工作的时间周期内安全、可靠的执行。

---

## 如何开始

一个简单的入门方法是使用我们的开源 [claude-api 技能](https://github.com/anthropics/skills/tree/main/skills/claude-api)，它在 Claude Code 中开箱即用。获取最新版本的 Claude Code 并运行以下子命令进行 Claude Managed Agents 入门。我对技能作为入门新功能的方式感到兴奋，并广泛使用这个技能：

```bash
$ claude update
$ claude /claude-api managed-agents-onboarding
```

另请参阅我们的[文档](https://platform.claude.com/docs/en/managed-agents/quickstart)以使用 SDK 或 CLI 快速开始，并在 [Claude Console](https://platform.claude.com/docs/en/managed-agents/onboarding) 中原型化代理。

---

## 使用场景

你可以在我们的 [Claude 博客](https://claude.com/blog/claude-managed-agents)中看到许多有趣的示例。我在这些示例和自己的工作中注意到的一些常见模式：

- **事件触发**：服务触发 Managed Agent 执行任务。例如，系统标记一个错误，managed agent 编写补丁并打开 PR。从标记到行动之间没有人类参与。

- **定时执行**：Managed Agent 被定时执行任务。例如，我和许多其他人使用这种模式进行定时每日简报（例如，X 或 Github 活动、代理团队正在做什么）。这是我使用的一个 X 活动每日简报示例。

- **发射后不管**：人类触发 Managed Agent 执行任务。例如，通过 Slack 或 Teams 向 Managed Agent 分配任务并获取交付物（电子表格、幻灯片、应用）。

- **长周期任务**：长运行任务是一个我认为 Managed Agents 将特别有用的领域。我通过复刻 [@karpathy](https://x.com/@karpathy) 的 auto-research 仓库并探索一些不同的想法来探索这一点。例如，我最近拿了 [@_chenglou](https://x.com/@_chenglou) 的优秀 [pretext 库](https://github.com/chenglou/pretext)，让一个 Managed Agent 探索将其应用于我们工程博客内容的方法。

---

## 核心概念

入门时，有三个核心概念需要理解：

- **Agent** — 一个版本化的配置，包含代理的身份：模型、系统提示词、工具、技能、MCP 服务器等。你创建一次并通过 ID 引用。

- **Environment** — 描述如何配置代理工具运行的沙盒的模板（例如，运行时类型、网络策略和包配置）。

- **Session** — 使用预创建的代理配置和环境的状态化运行。它从环境模板配置一个全新的沙盒，挂载任何每次运行的资源（文件、GitHub 仓库），将认证存储在安全 vault 中（MCP 凭证）。

将代理视为配置，环境描述你希望代理访问的用于代码执行的沙盒的模板，session 视为任何代理执行。一个代理可以有多个 session。

---

## 使用方法

请参阅[文档](https://platform.claude.com/docs/en/managed-agents/quickstart)：

- **SDKs** – 这些是面向代码的：在你的应用中导入它们以在运行时驱动 session。六种语言支持 Managed Agents：Python、TypeScript、Java、Go、Ruby、PHP。

- **CLI** – 面向终端：每个 API 资源（代理、环境、session、vault、技能、文件）都作为子命令暴露。

- **常见模式** – 使用 CLI 进行设置，使用 SDK 进行运行时。代理模板是持久的：你创建一个，存储它（例如，作为包含模型、系统提示词、工具、MCP 服务器、技能的 git 中的 YAML），并让 CLI 在你的部署管道中应用它。

---

## 工作原理

我与 [@mc_anthropic](https://x.com/@mc_anthropic)、[@gcemaj](https://x.com/@gcemaj) 和 [@jkeatn](https://x.com/@jkeatn) 一起写了一篇 Anthropic 工程[博客文章](https://www.anthropic.com/engineering/managed-agents)，介绍构建 Claude Managed Agents 的过程：我们在文章中分享的一个教训是，构建与 Claude 智能规模相匹配的代理是一个基础设施挑战，而不仅仅是 harness 设计的问题。

考虑到这一点，我们没有设计特定的代理 harness；我们期望代理 harness 不断演变。相反，我们将"大脑"（Claude 及其 harness）与"手"（执行动作的沙盒和工具）和"session"（session 事件日志）解耦。

每个都成为对其他方面做很少假设的接口，每个都可以独立失败或被替换。我们分享这如何为系统提供可靠性、安全性和灵活性，以添加未来的 harness、沙盒或基础设施来容纳 session。

---

## 结论

我对探索不同多代理编排模式或长运行任务的项目感到兴奋。我[过去写过](https://rlancemartin.github.io/2025/07/30/bitter_lesson/)的一个挫折是让代理 harness 跟上模型能力。Claude Managed Agents 为你处理代理 harness 和基础设施，允许在代理作为 Claude API 中的新核心原语之上进行探索。

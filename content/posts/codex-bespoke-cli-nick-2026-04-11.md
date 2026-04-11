---
title: "我提供给 Codex 的最佳工具是定制的 CLI"
date: 2026-04-11T10:50:00+08:00
draft: false
tags: ["Codex", "CLI", "OpenAI", "AI工具", "开发"]
---

# 我提供给 Codex 的最佳工具是定制的 CLI

- **来源**: [X.com - @nickbaumann_](https://x.com/nickbaumann_/status/2042705384306336083)
- **作者**: Nick (@nickbaumann_)
- **翻译时间**: 2026-04-11
- **原文标题**: The best tools I give Codex are bespoke CLIs

---

## 正文内容

Codex 非常擅长使用工具，当工具可以表示为精确命令时。

这听起来很明显，但它改变了我对如何让 Codex 访问我每天使用的东西的思考方式。

连接器或 MCP 服务器非常适合访问。我以这种方式使用 Slack、Linear 和 Sentry。但有时源输出太大、太嘈杂或太尴尬，无法一直直接交给 Codex。在这些情况下，我经常想要一个在旁边的东西：一个带有标志的命令、稳定的 JSON、可预测的错误和一个帮助屏幕。

这给了 Codex 它已经非常擅长使用的东西。

它可以搜索、缩小范围、重试、管道输出、将大结果写入文件、检查 --help，并从最后一个结果组合下一个命令。几乎没有仪式。

**如果你想要操作指南，我写了如何让 Codex 构建一个的指南：**
- 创建 CLI Codex 可以使用：https://developers.openai.com/codex/use-cases/agent-friendly-clis

第一部分是使用 Codex 创建 CLI。第二部分是将 CLI 包装在技能中，这样未来的 Codex 线程就知道首先运行哪些命令、拉回多少输出以及哪些操作需要批准。

以下是我实际以这种方式使用的三个 CLI。它们不是连接器的替代品。当我希望 Codex 处理一个大数据源而不将整个东西拖入线程时，它们坐在连接器旁边。

---

## Codex 线程

我的旧 Codex 线程充满了有趣的模式，我想从中学习并将其编码成对未来有用的技能和自动化。

我让 Codex 一直引用它自己的线程。我还设置了一个自动化，扫描最近的线程以寻找值得保存为技能的模式。

原始会话存档太嘈杂，无法直接交给 Codex。它包括工具输出、部分尝试和仅在该时刻有用的上下文。你可以告诉 Codex 直接阅读它的线程。它有效，但如果你经常这样做，它会变慢和嘈杂。

所以我使用 codex-threads。

```
codex-threads --json sync
codex-threads --json messages search "build a CLI" --limit 20
codex-threads --json threads resolve "tweet idea"
codex-threads --json threads read <session-id>
codex-threads --json events read <session-id> --limit 50
```

它保持一个本地可搜索的 ~/.codex/sessions 索引，然后给 Codex 搜索、解析和阅读旧线程的命令。

这在我想要将线程转换为技能时特别有用。很多好的技能都是从"找到这个进行得很好的线程，然后保留模式"开始的。

---

## Slack

当答案埋在我不会手动找到的线程中时，我让 Codex 阅读 Slack：为什么做出应用服务器身份验证决策、其他人是否看到相同的本地开发失败，或者审查员在启动频道中已经同意什么。

Slack 连接器很有用，但重复研究在 Codex 有命令形状的工具时更容易：

```
slack-cli search "app server auth" --all-pages --max-pages 3 --json
slack-cli resolve-permalink "https://openai.slack.com/archives/..."
slack-cli read-thread L143 123522523239.633199 --json
slack-cli context R152 25723525099.626199 --before 5 --after 5 --json
```

这让 Codex 广泛搜索、解析确切的线程、拉取附近的上下文，并引用重要的消息。

slack-cli 仍然使用批准的 Codex 应用网关。它不是权限的变通方法。它是相同的访问模型，被塑造成代理可以组合的命令。

---

## Typefully

我用 Codex 写和安排很多内容，我为此使用 Typefully。

Typefully 有一个很好的 API，但我不需要 Codex 每次想要帮助草稿时都重新学习整个 API。我需要的只是我实际使用的几个操作：

```
typefully-cli --json drafts list --social-set <id> --limit 20
typefully-cli --json drafts read --social-set <id> <draft-id>
typefully-cli --json drafts create --social-set <id> --body-file draft.json
typefully-cli --json media upload --social-set <id> ./image.png
typefully-cli --json queue schedule-read --social-set <id>
```

所以我让 Codex 阅读 API 文档并构建 typefully-cli 作为一个小 Rust 二进制文件，我可以在任何仓库中运行。

围绕它的技能与二进制文件本身一样重要。它告诉 Codex 使用 JSON、默认创建草稿、当 shell 引用变得烦人时使用 body 文件，并且永远不要发布、安排、删除或覆盖任何东西，除非我明确要求。

最后一部分是关键。我不想每次请求帮助发帖时都继续输入"不要发布这个"。

---

## 构建一个

有用的部分非常简单：如果我不断将相同的文档、导出、日志或 API 怪异之处交给 Codex，我通常想停止解释它并给它一个命令。

然后我将该 CLI 包装在技能中，以便 Codex 记住如何使用它。如果你想让 Codex 为你自己的工具构建一个，我在这里写了操作指南：

- 用例：https://developers.openai.com/codex/use-cases/agent-friendly-clis
- $cli-creator: https://github.com/openai/skills/tree/main/skills/.curated/cli-creator

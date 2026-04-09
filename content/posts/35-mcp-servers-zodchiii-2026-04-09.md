---
title: "35个顶级MCP服务器，让Claude成为生产力机器"
date: 2026-04-09T09:30:00+08:00
draft: false
tags: ["MCP", "Claude", "AI工具", "生产力", "开发工具"]
---

# 35个顶级MCP服务器，让Claude成为生产力机器

- **来源**: [X.com - @zodchiii](https://x.com/zodchiii/status/2041804097628582294)
- **作者**: darkzodchi (@zodchiii)
- **翻译时间**: 2026-04-09
- **原文标题**: Top MCP Servers That Turn Claude Into a Productivity Machine

---

## 正文内容

**你需要的唯一清单。每个服务器1-2行介绍，附链接。**

目前各个目录中列出了超过10,000个MCP服务器。其中大多数是周末项目，第一次尝试就会崩溃。

在过去一年的vibe coding中，我测试了几十个，保留了那些真正有效、积极维护并解决真实问题的。

这些是值得安装的MCP服务器，按功能分类。

**如果你不知道MCP是什么：**
它是你将Claude连接到外部工具的方式。

---

## 搜索与研究 🔍

**01 — Tavily**
AI优化的网络搜索。返回干净的内容，而不仅仅是链接。专为AI代理构建。
- 免费：每月1,000次查询
- https://github.com/tavily-ai/tavily-mcp

**02 — Exa**
语义搜索。通过含义而非关键词查找页面。非常适合研究和查找类似内容。
- 免费：每月1,000次搜索
- https://github.com/exa-labs/exa-mcp-server

**03 — Brave Search**
独立的网络搜索索引，无Google追踪。6个工具：网页、本地、图片、视频、新闻、摘要器。
- 付费：每月$5起
- https://github.com/anthropics/anthropic-quickstarts

**04 — Perplexity**
带有深度研究和推理的问答引擎。返回综合答案，而非原始结果。
- 免费 tier 可用
- https://github.com/ppl-ai/perplexity-mcp

**05 — Context7**
任何框架的实时文档。Claude停止幻觉过时的API。对于使用快速变化库的开发者来说是必不可少的。
- 免费开源
- https://github.com/context-labs/context7

---

## 网页抓取与数据提取 🌐

**06 — Firecrawl**
任何URL在几秒钟内变成干净的markdown。自主研究代理，JS渲染，全站抓取。RAG管道的首选。
- 免费：500终身积分
- https://github.com/firecrawl/firecrawl-mcp-server

**07 — Apify**
3,000+现成的抓取器。Google地图、Amazon、LinkedIn、社交媒体。如果网站存在，Apify可能有抓取器。
- 免费：每月$5积分
- https://github.com/apify/actors-mcp-server

**08 — Bright Data**
重度反机器人绕过。Cloudflare、CAPTCHA、企业保护。当Firecrawl和Apify无法通过时使用。
- 仅付费
- https://github.com/nicholasgriffintn/bright-data-mcp

**09 — Crawl4AI**
免费开源抓取，最佳markdown提取。GitHub 61k+星。无需API密钥。
- 免费开源
- https://github.com/unclecode/crawl4ai

---

## 浏览器自动化 🖥️

**10 — Playwright**
Claude控制真实的Chrome浏览器。点击、填写表单、导航、截图。无需编写测试脚本即可测试。
- 免费开源
- https://github.com/anthropics/anthropic-quickstarts

**11 — Browserbase**
AI的云托管浏览器。无需本地Puppeteer设置。每个会话返回你的代理控制的实时浏览器URL。
- 免费：每月100个会话
- https://github.com/browserbase/mcp-server-browserbase

---

## 开发工具与代码 💻

**12 — GitHub**
PR、issues、代码搜索、CI/CD工作流。每个开发者应该安装的第一个MCP服务器。
- 使用GitHub账户免费
- https://github.com/github/github-mcp-server

**13 — Linear**
无需离开Claude的问题跟踪。创建工单、带过滤器搜索、更新状态、管理冲刺。
- 免费 tier 可用
- https://github.com/linear/linear-mcp-server

**14 — Sentry**
生产错误上下文。完整的堆栈跟踪、面包屑、崩溃诊断。从警报到修复无需切换工具。
- 免费：每月5K错误
- https://mcp.sentry.dev

**15 — Vercel**
部署、检查构建日志、检查错误、管理项目。在一个循环中调试失败的部署。
- 免费 tier 可用
- https://github.com/vercel/mcp-server-vercel

**16 — Jira / Atlassian**
JQL搜索、工单创建、冲刺管理、工作流转换。对于生活在Jira中的团队。
- 免费：最多10个用户
- https://github.com/atlassian/mcp-server-atlassian

---

## 数据库 🗄️

**17 — Supabase**
通过提示实现Postgres + auth + storage。为开发环境构建。提供只读模式。
- 免费 tier 可用
- https://github.com/supabase/mcp-server-supabase

**18 — PostgreSQL**
自然语言数据库查询。模式检查、数据分析、迁移帮助。
- 免费开源
- https://github.com/anthropics/anthropic-quickstarts

**19 — MongoDB**
40+工具。Atlas管理、性能顾问、聚合管道。最全面的数据库MCP。
- 免费：512MB集群
- https://github.com/mongodb/mongodb-mcp-server

**20 — Neo4j**
图数据库查询。关系分析、知识图谱、连接数据探索。
- 免费：社区版
- https://github.com/neo4j/neo4j-mcp-server

---

## 向量与AI记忆 🧠

**21 — Pinecone**
带重新排序的云向量搜索。用于RAG管道和大规模语义检索。
- 免费：2GB存储
- https://github.com/pinecone-io/pinecone-mcp

**22 — Qdrant**
语义记忆和向量搜索。开源，可自托管。
- 免费开源
- https://github.com/qdrant/mcp-server-qdrant

**23 — Chroma**
轻量级向量数据库。适合本地开发和原型设计RAG系统。
- 免费开源
- https://github.com/chroma-core/chroma-mcp

**24 — Memory MCP**
基于知识图谱的持久记忆。Claude跨会话记住，无需Projects。
- 免费开源
- https://github.com/anthropics/anthropic-quickstarts

---

## 生产力与协作 📋

**25 — Notion**
通过提示实现文档、wiki、数据库。搜索、总结和处理你的工作空间，无需打开Notion。
- 免费 tier 可用
- https://github.com/anthropics/anthropic-quickstarts

**26 — Slack**
阅读线程、搜索历史、发送消息。"总结一下团队关于发布的讨论"实际上有效。
- 使用Slack工作区免费
- https://github.com/anthropics/anthropic-quickstarts

**27 — Todoist**
通过Claude进行任务管理。创建、组织和跟踪任务，无需打开应用。
- 免费 tier 可用
- https://github.com/abhiz123/todoist-mcp-server

**28 — Zapier**
任何应用之间的自动化。从Slack、Gmail、Trello、Sheets和6,000+其他应用触发工作流，只需一个提示。
- 免费：每月100个任务
- https://github.com/zapier/zapier-mcp-server

---

## 商业与金融 💰

**29 — Stripe**
通过提示实现支付、订阅、发票、客户数据。检查收入、管理订阅、调试支付问题。
- 免费：测试模式
- https://github.com/stripe/agent-toolkit

**30 — HubSpot**
通过Claude实现CRM。联系人、交易、管道管理、活动跟踪，无需HubSpot UI。
- 免费CRM可用
- https://github.com/hubspot/mcp-server-hubspot

---

## 设计与媒体 🎨

**31 — Figma**
设计文件到代码。读取token、检查组件、抓取frame截图。设计到代码的鸿沟缩小到零。
- 使用Figma账户免费
- https://github.com/nicholasgriffintn/figma-mcp

**32 — Bannerbear**
从模板自动生成图片和横幅。社交媒体图形、OG图片、大规模证书。
- 免费：每月30张图片
- https://github.com/bannerbear/bannerbear-mcp

---

## 基础设施与监控 ⚙️

**33 — Cloudflare**
通过Claude管理Workers、KV存储、D1数据库、DNS和安全规则。
- 免费 tier 可用
- https://github.com/cloudflare/mcp-server-cloudflare

**34 — Docker**
通过提示进行容器管理。列出、启动、停止、检查容器和镜像。
- 免费开源
- https://github.com/docker/docker-mcp

**35 — Grafana**
查询仪表板、检查指标、调查警报。无需切换标签的监控。
- 免费：Grafana Cloud
- https://github.com/grafana/mcp-grafana

---

## 如何安装任何MCP服务器

**所有服务器使用相同的模式：**

```bash
# 添加服务器到Claude Code
claude mcp add server-name -- npx -y @package/server

# 添加API密钥
claude mcp add server-name -e API_KEY=your-key -- npx -y @package/server

# 全局添加（所有项目）
claude mcp add --scope user server-name -- npx -y @package/server

# 列出已安装服务器
claude mcp list

# 移除服务器
claude mcp remove server-name
```

**对于Claude Desktop，添加到你的配置文件：**

```json
{
  "mcpServers": {
    "server-name": {
      "command": "npx",
      "args": ["-y", "@package/server"],
      "env": {
        "API_KEY": "your-key"
      }
    }
  }
}
```

---

## 从哪里开始

你不需要全部35个。

**从解决你当前问题的3-5个开始：**

```
如果你是开发者：GitHub + Sentry + Context7 + Playwright
如果你做研究：Tavily + Firecrawl + Exa
如果你管理项目：Linear + Slack + Notion
如果你经营业务：Stripe + HubSpot + Zapier
如果你处理数据：Supabase + Firecrawl + Apify
```

每个MCP服务器都使用token上下文。3-5个服务器是最佳点。超过这个数量，你在提问之前就在工具描述上燃烧token。

Claude Code有工具搜索功能，可以延迟加载服务器以减少这个问题，但保持精简。

---

感谢阅读 🙏🏼

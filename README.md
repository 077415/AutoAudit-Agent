# AutoAudit-Agent 🛡️🤖

Automated PR Code Review & Security Auditing System powered by Multi-Agent Collaboration.

## 📖 项目简介 (Introduction)
AutoAudit-Agent 是一个基于大语言模型（LLM）的多 Agent 协作系统。它通过监听 GitHub Webhook，自动介入代码审查（Code Review）流程，重点进行深度的业务逻辑校验、性能瓶颈分析以及安全漏洞排查（如越权、注入等），并能自动生成修复建议。

## ⚙️ 核心架构 (Architecture)
系统采用长链推理与多 Agent 协作模式，主要包含四个核心 Agent：

```mermaid
graph TD
    A[GitHub Webhook / PR Event] --> B[Monitor Agent]
    B -->|Fetch Diff & Context| C[Reviewer Agent]
    C -->|Security & Logic Check| D{Issues Found?}
    D -- Yes --> E[Refactor Agent]
    E -->|Generate Fix Code| F[Summary Agent]
    D -- No --> F
    F -->|Post Comments & Approve/Reject| G[GitHub PR Comment]

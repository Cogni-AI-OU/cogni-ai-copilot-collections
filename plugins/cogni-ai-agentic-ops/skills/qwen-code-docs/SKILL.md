---
name: qwen-code-docs
description: >-
  USE FOR: Reading, searching, or referencing Qwen Code documentation (docs directory, CLI reference, configuration, features, MCP, and design docs).
  DO NOT USE FOR: Executing Qwen Code commands; use appropriate development skills when implementing plugins/extensions.
  You MUST load this skill when you need to consult Qwen Code documentation while working with or using Qwen Code.
license: MIT
---

# Qwen Code Docs

<!-- markdownlint-disable MD013 MD023 MD031 MD032 -->

## When to Use

- **Documentation Lookup**: Finding specific Qwen Code doc pages for features, channels, auto-mode, configuration, and settings.
- **Developer Reference**: Fetching architecture docs, tool specs (file system, MCP server, web fetch), or SDK docs for Java/Python/TypeScript.
- **Design & Architecture**: Looking up plans, structured output design, channels design, worktree specs, telemetry gaps, and E2E test reports.

## When Not to Use

- **Running Qwen Code Commands**: Interacting with a live session — use direct CLI execution instead.
- **Writing Extensions/Skills**: Authoring new agent skills — use the appropriate development skill.

## Core Process

1. **Identify the Topic**: Determine the docs area (users, developers, design, plans, superpowers/plans, e2e-tests, or root).
2. **Fetch Doc Content**: Build the URL path using the pattern:
   ```text
   https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/<filename>
   ```
3. **Process Content**: Extract relevant information to answer the query.

Use `webfetch` or equivalent to retrieve raw markdown files.

## References

### Docs (root)

- [docs/index.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/index.md)
  - USE FOR: Qwen Code Documentation

### Design

- [docs/design/2026-05-15-async-memory-recall-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/2026-05-15-async-memory-recall-design.md)
  - USE FOR: Async Memory Recall — Design Spec
- [docs/design/adaptive-output-token-escalation/adaptive-output-token-escalation-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/adaptive-output-token-escalation/adaptive-output-token-escalation-design.md)
  - USE FOR: Adaptive Output Token Escalation Design
- [docs/design/auth/motivation.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/auth/motivation.md)
  - USE FOR: Auth Provider Registry Motivation
- [docs/design/auto-compaction-threshold-redesign.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/auto-compaction-threshold-redesign.md)
  - USE FOR: Auto-Compaction Threshold Redesign
- [docs/design/auto-memory/memory-system.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/auto-memory/memory-system.md)
  - USE FOR: Memory 记忆管理系统
- [docs/design/channels/channels-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/channels/channels-design.md)
  - USE FOR: Channels Design
- [docs/design/compact-mode/compact-mode-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/compact-mode/compact-mode-design.md)
  - USE FOR: Compact Mode Design: Competitive Analysis & Optimization
- [docs/design/compaction-image-stripping/compaction-image-stripping-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/compaction-image-stripping/compaction-image-stripping-design.md)
  - USE FOR: Compaction Image Stripping + Token Estimation Fix
- [docs/design/custom-api-key-auth-wizard-prd.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/custom-api-key-auth-wizard-prd.md)
  - USE FOR: Custom API Key Auth Wizard PRD
- [docs/design/customize-banner-area/customize-banner-area.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/customize-banner-area/customize-banner-area.md)
  - USE FOR: Customize Banner Area Design
- [docs/design/customize-banner-area/customize-banner-area.zh-CN.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/customize-banner-area/customize-banner-area.zh-CN.md)
  - USE FOR: Banner 自定义区域设计方案
- [docs/design/fork-subagent/fork-subagent-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/fork-subagent/fork-subagent-design.md)
  - USE FOR: Fork Subagent Design
- [docs/design/markdown-syntax-extension.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/markdown-syntax-extension.md)
  - USE FOR: Markdown Syntax Extension Design
- [docs/design/openrouter-auth-and-models.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/openrouter-auth-and-models.md)
  - USE FOR: OpenRouter Auth and Model Management Design
- [docs/design/prompt-suggestion/prompt-suggestion-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/prompt-suggestion/prompt-suggestion-design.md)
  - USE FOR: Prompt Suggestion (NES) Design
- [docs/design/prompt-suggestion/prompt-suggestion-implementation.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/prompt-suggestion/prompt-suggestion-implementation.md)
  - USE FOR: Prompt Suggestion Implementation Status
- [docs/design/prompt-suggestion/speculation-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/prompt-suggestion/speculation-design.md)
  - USE FOR: Speculation Engine Design
- [docs/design/session-recap/session-recap-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/session-recap/session-recap-design.md)
  - USE FOR: Session Recap Design
- [docs/design/session-title/session-title-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/session-title/session-title-design.md)
  - USE FOR: Session Title Design
- [docs/design/skill-nudge/skill-nudge.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/skill-nudge/skill-nudge.md)
  - USE FOR: AutoSkill：自动技能提炼系统设计文档
- [docs/design/slash-command/compare.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/slash-command/compare.md)
  - USE FOR: Qwen Code Command 模块重构方案
- [docs/design/slash-command/phase1-technical-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/slash-command/phase1-technical-design.md)
  - USE FOR: Phase 1 技术设计文档：基础设施重建
- [docs/design/slash-command/phase2-technical-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/slash-command/phase2-technical-design.md)
  - USE FOR: Phase 2 技术设计文档：能力扩展
- [docs/design/slash-command/phase3-technical-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/slash-command/phase3-technical-design.md)
  - USE FOR: Phase 3 技术设计文档：体验对齐
- [docs/design/slash-command/roadmap.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/slash-command/roadmap.md)
  - USE FOR: Slash Command 重构路线图
- [docs/design/structured-output/structured-output.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/structured-output/structured-output.md)
  - USE FOR: Structured Output (`--json-schema`) — Design
- [docs/design/telemetry-llm-request-timing-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/telemetry-llm-request-timing-design.md)
  - USE FOR: LLM Request Timing Decomposition Design (P3 Phase 4)
- [docs/design/telemetry-resource-attributes-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/telemetry-resource-attributes-design.md)
  - USE FOR: Telemetry: Custom Resource Attributes + Metric Cardinality Controls
- [docs/design/tool-use-summary/tool-use-summary-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/tool-use-summary/tool-use-summary-design.md)
  - USE FOR: Tool-Use Summary Design
- [docs/design/workflow-tracing-gaps.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/workflow-tracing-gaps.md)
  - USE FOR: Workflow 级 Span 粒度不足分析 (P1)
- [docs/design/worktree.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/design/worktree.md)
  - USE FOR: Worktree 通用能力设计

### Developers

- [docs/developers/architecture.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/architecture.md)
  - USE FOR: Qwen Code Architecture Overview
- [docs/developers/channel-plugins.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/channel-plugins.md)
  - USE FOR: Channel Plugin Developer Guide
- [docs/developers/contributing.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/contributing.md)
  - USE FOR: How to Contribute
- [docs/developers/daemon-client-adapters/channel-web.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/daemon-client-adapters/channel-web.md)
  - USE FOR: Channel And Web Backend Daemon Adapter Draft
- [docs/developers/daemon-client-adapters/ide.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/daemon-client-adapters/ide.md)
  - USE FOR: IDE Daemon Adapter Draft
- [docs/developers/daemon-client-adapters/tui.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/daemon-client-adapters/tui.md)
  - USE FOR: TUI Daemon Adapter Draft
- [docs/developers/development/deployment.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/development/deployment.md)
  - USE FOR: Qwen Code Execution and Deployment
- [docs/developers/development/integration-tests.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/development/integration-tests.md)
  - USE FOR: Integration Tests
- [docs/developers/development/issue-and-pr-automation.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/development/issue-and-pr-automation.md)
  - USE FOR: Automation and Triage Processes
- [docs/developers/development/npm.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/development/npm.md)
  - USE FOR: Package Overview
- [docs/developers/development/telemetry.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/development/telemetry.md)
  - USE FOR: Observability with OpenTelemetry
- [docs/developers/examples/daemon-client-quickstart.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/examples/daemon-client-quickstart.md)
  - USE FOR: DaemonClient quickstart (TypeScript)
- [docs/developers/examples/proxy-script.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/examples/proxy-script.md)
  - USE FOR: Example Proxy Script
- [docs/developers/qwen-serve-protocol.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/qwen-serve-protocol.md)
  - USE FOR: `qwen serve` HTTP protocol reference
- [docs/developers/roadmap.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/roadmap.md)
  - USE FOR: Qwen Code RoadMap
- [docs/developers/sdk-java.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/sdk-java.md)
  - USE FOR: Qwen Code Java SDK
- [docs/developers/sdk-python.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/sdk-python.md)
  - USE FOR: Python SDK
- [docs/developers/sdk-typescript.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/sdk-typescript.md)
  - USE FOR: Typescript SDK
- [docs/developers/tools/exit-plan-mode.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/tools/exit-plan-mode.md)
  - USE FOR: Exit Plan Mode Tool (`exit_plan_mode`)
- [docs/developers/tools/file-system.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/tools/file-system.md)
  - USE FOR: Qwen Code file system tools
- [docs/developers/tools/introduction.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/tools/introduction.md)
  - USE FOR: Qwen Code tools
- [docs/developers/tools/mcp-server.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/tools/mcp-server.md)
  - USE FOR: MCP servers with Qwen Code
- [docs/developers/tools/multi-file.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/tools/multi-file.md)
  - USE FOR: Multi File Read Tool (`read_many_files`)
- [docs/developers/tools/sandbox.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/tools/sandbox.md)
  - USE FOR: Sandbox Tool (`sandbox`)
- [docs/developers/tools/shell.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/tools/shell.md)
  - USE FOR: Shell Tool (`run_shell_command`)
- [docs/developers/tools/task.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/tools/task.md)
  - USE FOR: Task Tool (`task`)
- [docs/developers/tools/todo-write.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/tools/todo-write.md)
  - USE FOR: Todo Write Tool (`todo_write`)
- [docs/developers/tools/web-fetch.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/tools/web-fetch.md)
  - USE FOR: Web Fetch Tool (`web_fetch`)
- [docs/developers/tools/web-search.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/developers/tools/web-search.md)
  - USE FOR: Web Search

### E2E-tests

- [docs/e2e-tests/2026-05-18-qwen-memory-benchmark-report.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/e2e-tests/2026-05-18-qwen-memory-benchmark-report.md)
  - USE FOR: Qwen Code Runtime Memory Benchmark Report
- [docs/e2e-tests/2026-05-19-oom-reproduction-report.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/e2e-tests/2026-05-19-oom-reproduction-report.md)
  - USE FOR: OOM 压力测试与长任务 Replay 报告
- [docs/e2e-tests/2026-05-19-qwen-runtime-diagnostics-benchmark-report.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/e2e-tests/2026-05-19-qwen-runtime-diagnostics-benchmark-report.md)
  - USE FOR: Qwen Code Runtime Diagnostics Benchmark Report
- [docs/e2e-tests/2026-05-21-qwen-0.15.11-default-heap-oom-stress-report.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/e2e-tests/2026-05-21-qwen-0.15.11-default-heap-oom-stress-report.md)
  - USE FOR: Qwen Code 0.15.11 默认 Heap OOM 压测报告
- [docs/e2e-tests/worktree-phase-c.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/e2e-tests/worktree-phase-c.md)
  - USE FOR: Worktree Phase C E2E Test Plan
- [docs/e2e-tests/worktree.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/e2e-tests/worktree.md)
  - USE FOR: Worktree Feature E2E Test Plan (Phase A + B)

### Plans

- [docs/plans/2026-03-22-agent-tool-display-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/plans/2026-03-22-agent-tool-display-design.md)
  - USE FOR: Agent Tool Display Implementation Plan
- [docs/plans/2026-05-18-qwen-runtime-memory-investigation.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/plans/2026-05-18-qwen-runtime-memory-investigation.md)
  - USE FOR: Qwen Code Runtime Memory Investigation Plan
- [docs/plans/memory-diagnostics-reference-design.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/plans/memory-diagnostics-reference-design.md)
  - USE FOR: Memory Diagnostics Reference Design

### Superpowers Plans

- [docs/superpowers/plans/2026-05-15-worktree-phase-c.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/superpowers/plans/2026-05-15-worktree-phase-c.md)
  - USE FOR: Worktree Phase C Implementation Plan

### Users

- [docs/users/common-workflow.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/common-workflow.md)
  - USE FOR: Common workflows
- [docs/users/configuration/auth.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/configuration/auth.md)
  - USE FOR: Authentication
- [docs/users/configuration/model-providers.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/configuration/model-providers.md)
  - USE FOR: Model Providers
- [docs/users/configuration/qwen-ignore.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/configuration/qwen-ignore.md)
  - USE FOR: Ignoring Files
- [docs/users/configuration/settings.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/configuration/settings.md)
  - USE FOR: Qwen Code Configuration
- [docs/users/configuration/themes.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/configuration/themes.md)
  - USE FOR: Themes
- [docs/users/configuration/trusted-folders.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/configuration/trusted-folders.md)
  - USE FOR: Trusted Folders
- [docs/users/extension/extension-releasing.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/extension/extension-releasing.md)
  - USE FOR: Extension Releasing
- [docs/users/extension/getting-started-extensions.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/extension/getting-started-extensions.md)
  - USE FOR: Getting Started with Qwen Code Extensions
- [docs/users/extension/introduction.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/extension/introduction.md)
  - USE FOR: Qwen Code Extensions
- [docs/users/features/approval-mode.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/approval-mode.md)
  - USE FOR: Approval Mode
- [docs/users/features/arena.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/arena.md)
  - USE FOR: Agent Arena
- [docs/users/features/auto-mode.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/auto-mode.md)
  - USE FOR: Auto Mode
- [docs/users/features/channels/dingtalk.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/channels/dingtalk.md)
  - USE FOR: DingTalk (Dingtalk)
- [docs/users/features/channels/overview.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/channels/overview.md)
  - USE FOR: Channels
- [docs/users/features/channels/plugins.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/channels/plugins.md)
  - USE FOR: Custom Channel Plugins
- [docs/users/features/channels/telegram.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/channels/telegram.md)
  - USE FOR: Telegram
- [docs/users/features/channels/weixin.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/channels/weixin.md)
  - USE FOR: WeChat (Weixin)
- [docs/users/features/checkpointing.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/checkpointing.md)
  - USE FOR: Checkpointing
- [docs/users/features/code-review.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/code-review.md)
  - USE FOR: Code Review
- [docs/users/features/commands.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/commands.md)
  - USE FOR: Commands
- [docs/users/features/dual-output.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/dual-output.md)
  - USE FOR: Dual Output
- [docs/users/features/followup-suggestions.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/followup-suggestions.md)
  - USE FOR: Followup Suggestions
- [docs/users/features/headless.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/headless.md)
  - USE FOR: Headless Mode
- [docs/users/features/hooks.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/hooks.md)
  - USE FOR: Qwen Code Hooks
- [docs/users/features/language.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/language.md)
  - USE FOR: Internationalization (i18n) & Language
- [docs/users/features/lsp.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/lsp.md)
  - USE FOR: Language Server Protocol (LSP) Support
- [docs/users/features/markdown-rendering.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/markdown-rendering.md)
  - USE FOR: Markdown Rendering
- [docs/users/features/mcp.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/mcp.md)
  - USE FOR: Connect Qwen Code to tools via MCP
- [docs/users/features/memory.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/memory.md)
  - USE FOR: Memory
- [docs/users/features/sandbox.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/sandbox.md)
  - USE FOR: Sandbox
- [docs/users/features/scheduled-tasks.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/scheduled-tasks.md)
  - USE FOR: Run Prompts on a Schedule
- [docs/users/features/skills.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/skills.md)
  - USE FOR: Agent Skills
- [docs/users/features/status-line.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/status-line.md)
  - USE FOR: Status Line
- [docs/users/features/structured-output.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/structured-output.md)
  - USE FOR: Structured Output (`--json-schema`)
- [docs/users/features/sub-agents.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/sub-agents.md)
  - USE FOR: Subagents
- [docs/users/features/tips.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/tips.md)
  - USE FOR: Contextual Tips
- [docs/users/features/token-caching.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/token-caching.md)
  - USE FOR: Token Caching and Cost Optimization
- [docs/users/features/tool-use-summaries.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/features/tool-use-summaries.md)
  - USE FOR: Tool-Use Summaries
- [docs/users/ide-integration/ide-companion-spec.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/ide-integration/ide-companion-spec.md)
  - USE FOR: Qwen Code Companion Plugin: Interface Specification
- [docs/users/ide-integration/ide-integration.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/ide-integration/ide-integration.md)
  - USE FOR: IDE Integration
- [docs/users/integration-github-action.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/integration-github-action.md)
  - USE FOR: Github Actions：qwen-code-action
- [docs/users/integration-jetbrains.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/integration-jetbrains.md)
  - USE FOR: JetBrains IDEs
- [docs/users/integration-vscode.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/integration-vscode.md)
  - USE FOR: Visual Studio Code
- [docs/users/integration-zed.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/integration-zed.md)
  - USE FOR: Zed Editor
- [docs/users/overview.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/overview.md)
  - USE FOR: Qwen Code overview
- [docs/users/quickstart.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/quickstart.md)
  - USE FOR: Quickstart
- [docs/users/qwen-serve.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/qwen-serve.md)
  - USE FOR: Daemon mode (`qwen serve`)
- [docs/users/reference/keyboard-shortcuts.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/reference/keyboard-shortcuts.md)
  - USE FOR: Qwen Code Keyboard Shortcuts
- [docs/users/support/Uninstall.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/support/Uninstall.md)
  - USE FOR: Uninstall
- [docs/users/support/tos-privacy.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/support/tos-privacy.md)
  - USE FOR: Qwen Code: Terms of Service and Privacy Notice
- [docs/users/support/troubleshooting.md](https://raw.githubusercontent.com/QwenLM/qwen-code/refs/tags/v0.16.1/docs/users/support/troubleshooting.md)
  - USE FOR: Troubleshooting

### Repository

- [Qwen Code Repository](https://github.com/QwenLM/qwen-code)
  - USE FOR: source code, issues, pull requests, main entry point

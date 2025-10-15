---
title: "Tìm hiểu Repo Git: cc-sdd (https://github.com/gotalab/cc-sdd)"
date: 2025-10-15
authors: [dsitweed]
categories:
  - テクノロジー
  - データ
tags:
  - cc-sdd
  - spec-driven-development
  - ai-coding
  - git-repo
  - development-tools
comments: true
---

# Tìm hiểu Repo Git: cc-sdd (https://github.com/gotalab/cc-sdd)

## Giới thiệu
Repo `cc-sdd` (Customize spec-driven development) là một công cụ NPM package được phát triển bởi gotalab, nhằm tùy chỉnh quy trình phát triển theo hướng Spec-Driven Development (SDD) cho các AI coding agents như Claude Code, Cursor IDE, Gemini CLI, Codex CLI, GitHub Copilot, và Qwen Code. Nó giúp chuyển đổi từ prototype sang production-ready development bằng cách tích hợp AI-Driven Development Life Cycle (AI-DLC) với các workflow có cấu trúc.

- **Ngôn ngữ chính**: TypeScript (99.2%), JavaScript (0.8%)
- **License**: MIT
- **Stars**: ~1.5k
- **Forks**: 127
- **Contributors**: 7 (bao gồm gotalab, claude, devin-ai-integration[bot], v.v.)
- **Latest Release**: v1.1.5 (3 tuần trước)
- **Commits gần đây**: Merge pull request #75 từ hotfix/templates (2 ngày trước)

## Mục đích và Tính năng Chính
- **Spec-Driven Development (SDD)**: Cung cấp quy trình có cấu trúc từ requirements → design → tasks → implementation.
- **Project Memory (Steering)**: AI học codebase, patterns, và preferences của dự án để duy trì context toàn diện.
- **Team Workflow Alignment**: Tùy chỉnh templates cho requirements, design, task, và steering docs để phù hợp với quy trình phê duyệt của team.
- **11 Slash Commands**: Như `/kiro:spec-init`, `/kiro:steering`, `/kiro:spec-requirements`, v.v., để quản lý specs và workflows.
- **Quality Gates**: Mỗi phase yêu cầu phê duyệt trước khi tiến hành (có thể auto-approve với `-y`).
- **Kiro IDE Compatibility**: Tái sử dụng specs và workflows từ Kiro IDE.

## Cách Cài đặt và Sử dụng
### Cài đặt Cơ bản
```bash
# Cài đặt mặc định cho Claude Code
npx cc-sdd@latest

# Alpha version với cập nhật lớn (v2.0.0-alpha.2)
npx cc-sdd@next

# Với ngôn ngữ cụ thể (en|ja|zh-TW|zh|es|pt|de|fr|ru|it|ko|ar)
npx cc-sdd@latest --lang ja
```

### Cài đặt cho Các Agent Khác
```bash
# Claude Code
npx cc-sdd@latest --claude

# Claude Code SubAgents (yêu cầu @next)
npx cc-sdd@next --claude-agent

# Gemini CLI
npx cc-sdd@latest --gemini

# Cursor IDE
npx cc-sdd@latest --cursor

# Codex CLI (yêu cầu alpha)
npx cc-sdd@next --codex

# GitHub Copilot (yêu cầu alpha)
npx cc-sdd@next --copilot

# Qwen Code
npx cc-sdd@latest --qwen
```

Sau khi cài đặt, agent có thể chạy `/kiro:spec-init <what-to-build>` để bắt đầu.

### Tùy chọn Nâng cao
```bash
# Preview changes trước khi áp dụng
npx cc-sdd@latest --dry-run

# Cập nhật an toàn với backup
npx cc-sdd@latest --backup --overwrite force

# Thư mục specs tùy chỉnh
npx cc-sdd@latest --kiro-dir docs/specs
```

## Các Agent Được Hỗ trợ
| Agent | Flag | Files Generated |
|-------|------|-----------------|
| Claude Code | --claude-code, --claude | .claude/commands/kiro/, {{KIRO_DIR}}/settings/, CLAUDE.md |
| Claude Code SubAgents | --claude-code-agent, --claude-agent | .claude/commands/kiro/ (12 commands), .claude/agents/kiro/ (9 subagents), {{KIRO_DIR}}/settings/, CLAUDE.md |
| Codex CLI | --codex, --codex-cli | .codex/prompts/, {{KIRO_DIR}}/settings/, AGENTS.md |
| Cursor IDE | --cursor | .cursor/commands/kiro/, {{KIRO_DIR}}/settings/, AGENTS.md |
| GitHub Copilot Chat | --copilot, --github-copilot | .github/prompts/, {{KIRO_DIR}}/settings/, AGENTS.md |
| Gemini CLI | --gemini-cli, --gemini | .gemini/commands/kiro/, {{KIRO_DIR}}/settings/, GEMINI.md |
| Qwen Code | --qwen-code, --qwen | .qwen/commands/kiro/, {{KIRO_DIR}}/settings/, QWEN.md |

Claude Code là mặc định nếu không chỉ định flag.

## Ngôn ngữ Hỗ trợ
- English (en) 🇬🇧
- Japanese (ja) 🇯🇵
- Traditional Chinese (zh-TW) 🇹🇼
- Simplified Chinese (zh) 🇨🇳
- Spanish (es) 🇪🇸
- Portuguese (pt) 🇵🇹
- German (de) 🇩🇪
- French (fr) 🇫🇷
- Russian (ru) 🇷🇺
- Italian (it) 🇮🇹
- Korean (ko) 🇰🇷
- Arabic (ar) 🇸🇦

Sử dụng: `npx cc-sdd@latest --lang <code>`

## AI-DLC Workflow
### Cho Dự án Mới
```
/kiro:spec-init User authentication with OAuth and 2FA
/kiro:spec-requirements user-auth
/kiro:spec-design user-auth -y
/kiro:spec-tasks user-auth -y
/kiro:spec-impl user-auth 1.1,1.2,1.3
```

### Cho Dự án Hiện Tại (Khuyến nghị)
```
/kiro:steering  # AI học context dự án hiện tại
/kiro:spec-init Add OAuth to existing auth system
/kiro:spec-requirements oauth-enhancement
/kiro:validate-gap oauth-enhancement  # Tùy chọn: phân tích gap
/kiro:spec-design oauth-enhancement -y
/kiro:validate-design oauth-enhancement  # Tùy chọn: validate design
/kiro:spec-tasks oauth-enhancement -y
/kiro:spec-impl oauth-enhancement 1.1,1.2,1.3
```

Specs có thể tái sử dụng với Kiro IDE.

## Tài nguyên Liên quan
- **Bài viết**: [Kiroの仕様書駆動開発プロセスをClaude Codeで徹底的に再現した](https://zenn.dev/gotalab/articles/3db0621ce3d6d2) (Zenn, tiếng Nhật)
- **Presentation**: [Claude Codeは仕様駆動の夢を見ない](https://speakerdeck.com/gotalab555/claude-codehashi-yang-qu-dong-nomeng-wojian-nai) (Speaker Deck, tiếng Nhật)
- **Ví dụ Spec**: [photo-albums-en](https://github.com/gotalab/cc-sdd/blob/main/.kiro/specs/photo-albums-en)

## Cấu trúc Dự án
```
cc-sdd/
├── tools/cc-sdd/              # Main NPM package
│   ├── src/                   # TypeScript source code
│   ├── templates/             # Agent templates
│   ├── package.json           # Package config
│   └── README.md              # Tool documentation
├── docs/                      # Documentation
├── .claude/                   # Example Claude Code commands
└── README.md                  # This file
```

## Thông tin Package
- NPM: [cc-sdd](https://www.npmjs.com/package/cc-sdd)
- Install Size: [Packagephobia](https://packagephobia.com/result?p=cc-sdd)
- Documentation: [Tool Docs](https://github.com/gotalab/cc-sdd/blob/main/tools/cc-sdd/README.md), [Japanese](https://github.com/gotalab/cc-sdd/blob/main/tools/cc-sdd/README_ja.md)

## Kết luận
cc-sdd là công cụ hữu ích để tích hợp SDD vào quy trình phát triển với AI agents, giúp đảm bảo chất lượng và tính cấu trúc. Nó phù hợp cho teams muốn tùy chỉnh workflows và duy trì project memory. Để bắt đầu, thử cài đặt với `npx cc-sdd@latest` và khám phá các slash commands.

Nếu cần chi tiết hơn về một phần nào đó, hãy cho biết!
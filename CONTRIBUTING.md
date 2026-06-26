# Contributing to awesome-mimo-agent

Thanks for helping build the community knowledge base for MiMo integrations!

## Before You Start

- Check [open PRs](../../pulls) to avoid duplicating existing work.
- Read the [MiMo API Docs](https://platform.xiaomimimo.com/) — guides must reflect the current API.

## What Makes a Good Integration Guide

Each guide should walk through **installation → configuration → first run** for a specific tool. Follow the format of existing guides in `docs/`.

### Required: Bilingual

Every guide must include both an English version (`docs/tool_name.md`) and a Simplified Chinese version (`docs/tool_name.zh-CN.md`). Submit them in a single PR.

### Required: README Table Entry

Add your guide to the tools table in **both** `README.md` and `README.zh-CN.md`. Insert the entry in **alphabetical order** within the table.

## Critical Checks

### 1. Model Naming

```
[correct]   mimo-v2.5-pro
```

### 2. 1M Context Window

MiMo V2.5 Pro supports up to **1 million tokens** of context. Make sure your configuration reflects this.

### 3. Anthropic Protocol

MiMo exposes an Anthropic-compatible endpoint at `https://api.xiaomimimo.com/anthropic`. When configuring via Moon Bridge or similar proxies, use the Anthropic protocol (not `openai-chat`) to ensure thinking blocks are properly preserved across multi-turn conversations.

## Common Pitfalls

- Don't document workarounds for upstream bugs — check whether the upstream project has already fixed the issue.
- Only document configuration options that actually exist and have been verified to work.
- One tool = one PR. Don't split English and Chinese versions into separate PRs.

## Images

Place screenshots in `docs/assets/`. Use descriptive filenames and keep file sizes reasonable.

Thank you for contributing!

# 🧙 Magic Docs — Auto-Updating Living Documents

**English** | [中文](README_CN.md)

An OpenClaw Skill that keeps your Markdown documents automatically up-to-date.

Inspired by Claude Code's `# MAGIC DOC:` mechanism.

## The Problem

Documentation rots the moment you write it. Projects evolve, APIs change, decisions shift — but nobody updates the docs.

Your Agent does tons of work and learns new information every conversation, but that knowledge stays trapped in chat history.

## The Solution

Add `<!-- MAGIC DOC -->` to any Markdown file. Magic Docs will:

1. **Detect** when a conversation contains new information relevant to the document
2. **Update** the document automatically — append new facts, correct outdated info
3. **Preserve** your original content — never deletes what you wrote

## How It Works

```markdown
<!-- MAGIC DOC scope="devices,network" -->
# Network Configuration

- NAS IP: 192.168.5.27
- Router: 192.168.5.1
```

After a conversation where you mention "NAS IP changed to 192.168.5.30":

```markdown
<!-- MAGIC DOC scope="devices,network" -->
# Network Configuration

- NAS IP: 192.168.5.30 <!-- updated 2026-04-02 -->
- Router: 192.168.5.1

---
## Changelog
- 2026-04-02: Updated NAS IP from .27 to .30
```

## Options

| Parameter | Values | Default | Description |
|-----------|--------|---------|-------------|
| `scope` | comma-separated keywords | (all topics) | Only update when conversation matches these topics |
| `update` | `realtime` / `daily` / `manual` | `realtime` | Update frequency |

## Install

```bash
# ClawHub
clawhub install wavmson/magic-docs

# Or clone directly
git clone https://github.com/wavmson/openclaw-skill-magic-docs.git ~/.openclaw/skills/magic-docs
```

## Safety

- Never deletes user-written content
- Never writes secrets/passwords (references TOOLS.md instead)
- Never writes temporary debug info
- When uncertain, preserves both old and new versions

## License

MIT

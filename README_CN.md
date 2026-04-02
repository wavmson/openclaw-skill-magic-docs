# 🧙 Magic Docs — 自动更新的活文档

[English](README.md) | **中文**

一个让你的 Markdown 文档自动保持最新的 OpenClaw Skill。

灵感来源：Claude Code 的 `# MAGIC DOC:` 机制。

## 痛点

文档写完就开始过时。项目变了、API 改了、配置换了——但没人更新文档。

Agent 每天做大量操作，学到很多新信息，但这些信息散落在对话里，不会自动沉淀到文档。

## 解决方案

给任何 Markdown 文件加一行 `<!-- MAGIC DOC -->` 标记，Agent 就会：

1. **自动检测**：每轮对话后判断是否有与文档相关的新信息
2. **自动更新**：追加新事实、修正过时信息
3. **安全保留**：绝不删除你手写的内容

## 使用方式

```markdown
<!-- MAGIC DOC scope="设备,网络" -->
# 网络配置

- NAS IP: 192.168.5.27
- 路由器: 192.168.5.1
```

当你在对话中提到"NAS 的 IP 换成 192.168.5.30 了"：

```markdown
<!-- MAGIC DOC scope="设备,网络" -->
# 网络配置

- NAS IP: 192.168.5.30 <!-- 更新于 2026-04-02 -->
- 路由器: 192.168.5.1

---
## 更新日志
- 2026-04-02: NAS IP 从 .27 更新为 .30
```

## 参数说明

| 参数 | 可选值 | 默认值 | 说明 |
|------|--------|--------|------|
| `scope` | 逗号分隔的关键词 | (所有主题) | 只在对话涉及这些主题时更新 |
| `update` | `realtime` / `daily` / `manual` | `realtime` | 更新频率 |

## 三种模式

- 📝 **realtime** — 每轮对话后自动检查（默认）
- 📅 **daily** — 每天更新一次
- 🔧 **manual** — 只在主动要求时更新

## 安装

```bash
# ClawHub
clawhub install wavmson/magic-docs

# 或直接 clone
git clone https://github.com/wavmson/openclaw-skill-magic-docs.git ~/.openclaw/skills/magic-docs
```

## 安全原则

- ✅ 只追加和修正，绝不删除你写的内容
- ✅ 不写密码密钥，只写"见配置文件"
- ✅ 拿不准的信息，新旧版本都保留
- ✅ 不写入临时调试信息

## License

MIT

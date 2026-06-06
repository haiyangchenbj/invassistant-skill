# Skill 发布优化规则 v1.0

> 用于所有 ClawHub + GitHub 同步发布的 Skill。在发布前逐条检查。

---

## 1. Frontmatter 规范

| 字段 | 规则 |
|------|------|
| `name` | 纯英文 slug，**不带版本号**。如 `invassistant`，不是 `invassistant-v2` |
| `description` | 最多 3 句英文描述 skill 用途。**不含**版本号、股票代码、关键词列表、改动日志 |
| `disable` | `false`（发布时） |
| `metadata.openclaw.tags` | 英文标签，5-10 个 |

**反面案例**（不可出现）：
```yaml
description: |
  个人投资组合管理框架 v2.1.1（执行简化版）。覆盖 A 股、港股、美股全市场。
  新增 §7.4 模式 D...
  触发关键词：检查持仓, COST, LLY, AXP, MCO...
```

**正面案例**：
```yaml
description: >
  Multi-asset investment portfolio management framework.
  A/B/C-class differentiated rules, 7 red-line risk controls,
  4-factor QMS scoring. Covers US, A-share, and HK stocks.
```

## 2. 标题与版本

- **H1 标题不带版本号**：`# InvAssistant`，不是 `# InvAssistant v2.1.2`
- 版本信息放在标题下方的 subtitle 段落中，一句话带过
- 版本号出现在 SKILL.md 内部的 `## Version History` 章节中

## 3. 语言规范

- **SKILL.md**：主体英文。可在末尾附一段中文简介（但不是全文翻译）
- **README.md**：英文
- **README_zh.md**：中文，与英文版内容对应
- 其他文档（references/、CONTRIBUTING.md）：英文

## 4. 内容净化

**必须删除的章节**：
- `## 详细参考` / `## References`（列出 `references/*.md` 文件路径 — 对用户无意义，是 AI 内部用的）
- 版本历史中的未发布版本（如 "v3.0 计划 2027"）
- 内部开发备注（"审计清理版"、"接下来 6-12 月不加规则"）

**版本历史规范**：
- 只列已发布到线上（ClawHub/GitHub）的版本
- 每行：`| 版本 | 日期 | 改动摘要（1 句话） |`
- 最多保留 5 个版本

## 5. GitHub 与 ClawHub 文件清单

| 文件 | GitHub | ClawHub |
|------|--------|---------|
| `SKILL.md`（英文主体） | ✅ | ✅（展示用） |
| `README.md`（英文） | ✅ | — |
| `README_zh.md`（中文） | ✅ | — |
| `CONTRIBUTING.md` | ✅ | — |
| `LICENSE` | ✅ | — |
| `references/*.md` | ✅ | ✅（AI 加载用，不展示） |
| `scripts/*.py` | ✅ | ✅（执行用） |
| `_meta.json` | — | ✅（ClawHub 元数据） |

## 6. 发布前检查清单

```
[ ] description ≤ 3 sentences, English only, no version numbers
[ ] H1 title has no version number
[ ] Version history shows only published versions (max 5)
[ ] No "详细参考/References" section in SKILL.md
[ ] No internal dev notes (审计清理版, 计划, 内部约定)
[ ] README.md exists and is English
[ ] README_zh.md exists and is Chinese
[ ] _meta.json version matches published version
```

---

*规则版本: v1.0 | 制定日期: 2026-06-06*

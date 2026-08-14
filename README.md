# literature-reading（文献阅读）Skill

面向 DeepSeek Harness 的**学术文献精读技能**（中文输出）。负责把 PDF / DOCX / Markdown / 纯文本文献提取为可读文本，并输出结构化精读报告，支持按章节精读、术语问答、文献对比与笔记整理。

## 功能

- 📄 多格式输入：PDF / DOCX / Markdown / 纯文本
- 🔍 文本提取：Python 3.13 + pypdf 按页提取，输出分页文本便于分段阅读
- 📑 结构化精读：基本信息 → 摘要 → 引言综述 → 方法模型 → 结果 → 结论 → 可复现性
- 🗂️ 多种输出：精读报告（10 节模板）、文献笔记、精确问答（标注章节/页码）、多篇对比表格
- ✅ 质量要求：引用数据注明出处、术语保留英文原文、指出局限与阅读疑问

## 安装

将本仓库的 `SKILL.md` 放入 DeepSeek Harness 的技能扫描目录之一：

| 优先级 | 路径 |
|---|---|
| 项目级 | `<工作区>/.dsh/skills/literature-reading/SKILL.md` |
| 用户级 | `~/.dsh/skills/literature-reading/SKILL.md` |
| Agent 级 | `~/.agents/skills/literature-reading/SKILL.md` |

（`<工作区>` 为当前会话的工作目录或其最近的含 `.git` 的祖先目录。）

例如（PowerShell）：

```powershell
# 项目级安装
New-Item -ItemType Directory -Path "F:\deepseek harness\.dsh\skills\literature-reading" -Force | Out-Null
Copy-Item SKILL.md "F:\deepseek harness\.dsh\skills\literature-reading\SKILL.md"
```

安装后，在会话中通过 `skill` 工具以名称 `literature-reading` 加载即可。

## 使用

在会话中对助手说类似：

- “阅读 `G:\麒麟菜合计\xxx.pdf`，输出精读报告”
- “精读这篇论文的方法部分，并解释参数来源”
- “对比这几篇文献的研究方法”

助手会按技能流程：确认输入 → 提取文本 → 结构化精读 → 按需输出（报告/笔记/问答/对比）。

## 依赖

- 本机需有 Python 3.13（或可用 `uv run --with pypdf` 临时环境）
- PDF 提取依赖 `pypdf` 包

## 精读报告模板

```markdown
# 《论文标题》精读报告

## 1. 基本信息
## 2. 研究背景与问题
## 3. 研究问题与假设
## 4. 方法与数据
## 5. 主要结果与发现
## 6. 结论与政策/管理启示
## 7. 创新点与贡献
## 8. 局限性与开放问题
## 9. 可复现性（公式/参数/软件/数据）
## 10. 阅读疑问（可追问点）
```

## 说明

- 本技能专注“阅读与分析”，如需将文献内容做成公众号文章 / PPT / 综述，请另行使用对应技能。
- 扫描版 PDF（无文字层）需 OCR，本技能默认不做强 OCR。

## License

[MIT](LICENSE) © 2026 wengxiaonan

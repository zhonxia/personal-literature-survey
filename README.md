# Personal Literature Survey

系统化个人文献调研工作流。在动笔写论文、做项目、或参加竞赛之前，用这个工作流摸清「这个方向已经有什么、差什么、我的贡献在哪里」。

## 核心能力

- **多源学术搜索**：通过 `paper-search-mcp` 并发搜索 20+ 学术源（arXiv, PubMed, Semantic Scholar, CrossRef, OpenAlex, dblp, CORE, 等）
- **通用搜索补漏**：通过 AnySearch 搜 survey 论文、技术博客、中文资料
- **个人知识库集成**：搜索 IMA（腾讯知识库）中已收集的文献
- **结构化工作流**：5 阶段（范围定义 → 搜索 → 筛选 → 深度阅读 → 综述输出）
- **PDF 下载**：多源回退链自动下载论文全文

## 依赖

| 工具 | 安装方式 | 用途 |
|------|---------|------|
| [paper-search-mcp](https://github.com/openags/paper-search-mcp) | `pip install paper-search-mcp` | 专业学术文献搜索 |
| [AnySearch skill](https://github.com/anysearch-ai/anysearch-skill) | 安装 Hermes skill | 通用网页搜索补漏 |
| IMA 腾讯知识库 | ima.qq.com | 个人文献知识库（可选） |

## 工作流

```
Phase 0: 范围定义     ← 明确关键词/时间/目标
Phase 1: 公开搜索     ← paper-search-mcp (20+源) + AnySearch (通用)
Phase 2: IMA 搜索     ← 个人知识库
Phase 3: 筛选+登记    ← 快速优先级矩阵
Phase 4: 深度阅读     ← 结构化模板 + 关联分析
Phase 5: 综述输出     ← 调研报告 / Related Work
```

## 相关项目

- [research-ideation](https://github.com/zhonxia/research-ideation) — 研究点子生成与评估（互补工作流）

## License

MIT

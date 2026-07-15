<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://img.shields.io/badge/status-active-success?style=for-the-badge&label=个人文献调研工作流">
    <img alt="Personal Literature Survey" src="https://img.shields.io/badge/status-active-success?style=for-the-badge&label=个人文献调研工作流">
  </picture>
</p>

<h1 align="center">📚 Personal Literature Survey（个人文献调研）</h1>

<p align="center">
  <em>系统化个人文献调研工作流 —— 在动笔写论文、做项目、或参加竞赛之前，用这个工作流摸清「这个方向已经有什么、差什么、我的贡献在哪里」。</em>
</p>

<p align="center">
  <a href="README.md">🌐 English</a>
  ·
  <a href="https://github.com/zhonxia/personal-literature-survey">GitHub</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/工作流-5--阶段-blue?style=flat-square" alt="5-Stage Workflow">
  <img src="https://img.shields.io/badge/学术源-20%2B%20数据库-brightgreen?style=flat-square" alt="20+ Academic Sources">
  <img src="https://img.shields.io/badge/许可证-MIT-green?style=flat-square" alt="MIT License">
  <img src="https://img.shields.io/badge/python-3.9%2B-blue?style=flat-square" alt="Python 3.9+">
  <img src="https://img.shields.io/badge/集成-IMA%20知识库-orange?style=flat-square" alt="IMA Integration">
</p>

---

## 📋 目录

- [这是什么？](#-这是什么)
- [核心理念](#-核心理念)
- [核心能力](#-核心能力)
- [工作流全景](#-工作流全景)
- [依赖安装](#-依赖安装)
- [快速开始](#-快速开始)
- [详细用法](#-详细用法)
  - [Phase 0：定义调研范围](#phase-0定义调研范围)
  - [Phase 1：公开学术数据库搜索](#phase-1公开学术数据库搜索)
  - [Phase 2：个人知识库搜索（IMA）](#phase-2个人知识库搜索ima)
  - [Phase 3：筛选与登记](#phase-3筛选与登记)
  - [Phase 4：深度阅读与分析](#phase-4深度阅读与分析)
  - [Phase 5：综述输出](#phase-5综述输出)
- [效率技巧](#-效率技巧)
- [快查表](#-快查表)
- [局限性](#-局限性)
- [相关项目](#-相关项目)
- [许可证](#-许可证)

---

## 🎯 这是什么？

**Personal Literature Survey** 是一套结构化的个人文献调研方法论。它帮助研究者、学生和工程师在投入时间写论文、做项目或参加竞赛之前，快速摸清一个研究领域的全貌。

文献调研不是「读一堆论文然后总结一下」——它是一个**有目标的搜索-筛选-分析过程**：

1. **搜索**：既要搜公开学术数据库（arXiv、PubMed、Semantic Scholar 等 20+ 源），也要搜你的个人知识库（IMA 腾讯知识库）
2. **筛选**：用结构化标准快速判断相关/不相关，不恋战
3. **分析**：不只「这篇做了什么」，更要「这个方向整体结构是什么」
4. **输出**：可消费的综述文档，不是笔记散片

### 适用场景

| 场景 | 说明 |
|------|------|
| 📝 **写论文前摸底** | 确认方向是否有人做过、差距在哪、创新点如何定位 |
| 🏆 **竞赛技术调研** | 快速掌握 SOTA、找 baseline、了解主流方法 |
| 📖 **课程文献综述** | 系统性完成文献调研作业或课程项目 |
| 🔬 **开题/立项** | 为研究计划提供文献依据，识别研究空白 |
| 🤝 **找合作/找方法** | 了解领域关键人物、关键论文和关键方法 |

---

## 💡 核心理念

本工作流基于几条关键认知：

1. **搜索不是一次性的**：多关键词、多源、多语言、多轮迭代才能保证覆盖度
2. **Survey 优先**：先读 1-2 篇综述论文，比从零散论文拼全景图效率高 10 倍
3. **关联分析 > 单篇精读**：读 3-5 篇后做一次跨论文分析，比继续读 10 篇更有价值
4. **个人知识库是金矿**：你已经读过、标注过的论文，往往比从零搜索更高效
5. **有输出才有价值**：调研的终点不是「读完了」，而是「能产出什么」

---

## ✨ 核心能力

| 能力 | 说明 |
|------|------|
| **多源学术搜索** | 通过 `paper-search-mcp` 并发搜索 20+ 学术源（arXiv, PubMed, Semantic Scholar, CrossRef, OpenAlex, dblp, CORE 等），自动去重 |
| **通用搜索补漏** | 通过 AnySearch 搜 survey 论文、技术博客、中文资料、教程 |
| **个人知识库集成** | 搜索 IMA（腾讯知识库）中已收集的文献、阅读笔记和分类文件夹 |
| **结构化 5 阶段工作流** | 范围定义 → 搜索 → 筛选 → 深度阅读 → 综述输出 |
| **PDF 下载** | 多源回退链自动下载论文全文：源原生链接 → CORE/Europe PMC → Unpaywall → Sci-Hub（可选） |
| **引用网络分析** | 通过 Semantic Scholar API 追踪前向引用（谁引用了它）和后向引用（它引用了谁） |
| **结构化阅读模板** | 统一格式记录每篇论文的核心信息，便于后续对比和引用 |
| **关联分析** | 识别主流范式、关键对比维度、研究空白（Research Gap） |

---

## 🔄 工作流全景

```
┌──────────────────────────────────────────────────────────────┐
│                     Phase 0: 范围定义                        │
│  ┌─ 明确方向 ─ 核心问题 ─ 关键词(中+英) ─ 时间范围 ─ 目标 ┐ │
│  └──────────────── 用户确认 ──────────────────────────────┘  │
├──────────────────────────────────────────────────────────────┤
│                Phase 1: 公开学术数据库搜索                    │
│  ┌────────────────────────────────────────────────────────┐  │
│  │   paper-search-mcp (20+ 学术源并发搜索)                 │  │
│  │   ├── arXiv · Semantic Scholar · PubMed                │  │
│  │   ├── CrossRef · OpenAlex · dblp · CORE                │  │
│  │   ├── bioRxiv · medRxiv · Europe PMC · IACR            │  │
│  │   ├── HAL · Zenodo · Google Scholar                    │  │
│  │   ├── DOAJ · Unpaywall · 3+ 更多                       │  │
│  │   └── 自动去重 + 结构化 JSON 输出                      │  │
│  ├────────────────────────────────────────────────────────┤  │
│  │   AnySearch (通用搜索补漏)                               │  │
│  │   ├── Survey 论文 · 技术博客 · 教程                     │  │
│  │   └── 中文资料 · 技术报告                               │  │
│  └────────────────────────────────────────────────────────┘  │
├──────────────────────────────────────────────────────────────┤
│                Phase 2: 个人知识库搜索 (IMA)                  │
│  ┌────────────────────────────────────────────────────────┐  │
│  │   IMA 腾讯知识库                                        │  │
│  │   ├── 已收集的论文                                     │  │
│  │   ├── 阅读笔记与标注                                   │  │
│  │   ├── 分类文件夹（media_type: 99）                     │  │
│  │   └── 游标翻页支持                                     │  │
│  └────────────────────────────────────────────────────────┘  │
├──────────────────────────────────────────────────────────────┤
│                Phase 3: 筛选与登记                            │
│  ┌────────────────────────────────────────────────────────┐  │
│  │   快速判断相关/不相关                                  │  │
│  │   优先级矩阵（直接/间接/边缘/跳过）                    │  │
│  │   论文登记（待读 / 已读 / 已排除）                     │  │
│  └────────────────────────────────────────────────────────┘  │
├──────────────────────────────────────────────────────────────┤
│                Phase 4: 深度阅读与分析                        │
│  ┌────────────────────────────────────────────────────────┐  │
│  │   单篇论文结构化阅读模板                               │  │
│  │   跨论文关联分析                                       │  │
│  │   主流范式识别与对比                                   │  │
│  │   研究空白（Research Gap）发现                         │  │
│  └────────────────────────────────────────────────────────┘  │
├──────────────────────────────────────────────────────────────┤
│                Phase 5: 综述输出                              │
│  ┌────────────────────────────────────────────────────────┐  │
│  │   调研报告（摸底/找方向）                              │  │
│  │   Related Work 段落（论文用）                           │  │
│  │   文献笔记归档                                         │  │
│  └────────────────────────────────────────────────────────┘  │
└──────────────────────────────────────────────────────────────┘
```

---

## 📦 依赖安装

| 工具 | 安装方式 | 用途 | 必需? |
|------|---------|------|-------|
| [paper-search-mcp](https://github.com/openags/paper-search-mcp) | `pip install paper-search-mcp` | 专业学术文献搜索（20+ 源） | ✅ |
| [AnySearch](https://github.com/anysearch-ai/anysearch-skill) | 安装 Hermes skill | 通用网页搜索补漏 | ✅ |
| IMA 腾讯知识库 | [ima.qq.com](https://ima.qq.com) 注册 | 个人文献知识库 | ⚠️ 可选 |
| Semantic Scholar API | 免费，无需 key | 引用链分析 | ⚠️ 可选 |
| flomo / short-mind | Hermes skill | 替代个人知识库 | ⚠️ 可选 |

### 安装 paper-search-mcp

```bash
pip install paper-search-mcp
```

### 配置 IMA（可选）

在 `~/.hermes/.env` 中添加：

```env
IMA_BASE_URL=https://ima.qq.com
IMA_OPENAPI_CLIENTID=<你的 Client ID>
IMA_OPENAPI_APIKEY=<你的 API Key>
```

未配置 IMA 时，工作流自动降级为仅搜索公开数据库。

---

## 🚀 快速开始

### 第 1 步：安装依赖

```bash
pip install paper-search-mcp
```

### 第 2 步：定义调研范围

在开始搜索之前，先明确你的目标：

```text
研究方向: [一句话描述]
核心问题: [具体的研究问题]
关键词 (中文+英文):
  - 核心词: [3-5 个]
  - 扩展词: [相关概念、同义词、上下位词]
搜索范围:
  - 时间窗口: 近3年 / 近5年 / 全部
  - 文献类型: 期刊论文 / 会议论文 / 预印本 / 报告
排除标准: [明确排除哪些方向/方法]
调研目标: 摸底 / 找 baseline / 找方法 / 写 related work / 找合作者
```

### 第 3 步：执行首次搜索

```bash
# 搜索全部源（并发搜索，自动去重）
paper-search search "你的研究主题" --max-results 10

# 指定源（推荐：提速 + 减少噪音）
paper-search search "reinforcement learning from human feedback" \
  --sources arxiv,semantic,crossref,openalex \
  --max-results 10
```

### 第 4 步：下载论文

```bash
# 按 ID 下载（arXiv ID、DOI 等）
paper-search download "2402.03300" --output ./papers/

# 多源回退自动下载
```

### 第 5 步：阅读与输出

使用 [Phase 4](#phase-4深度阅读与分析) 的结构化模板记录笔记，用 [Phase 5](#phase-5综述输出) 的格式输出综述。

---

## 📖 详细用法

### Phase 0：定义调研范围

> ⏱ 建议耗时：10-15 分钟

在开始搜索前，必须与用户（或自己）确认调研范围。关键问题：

- **研究什么？**
- **为什么重要？**
- **已经有什么？**
- **你的独特角度是什么？**
- **需要多深多广？**

将范围文档化——这能防止在搜索阶段无限发散，也让最终的调研产出可衡量。

---

### Phase 1：公开学术数据库搜索

> ⏱ 建议耗时：20-30 分钟

使用两个搜索工具形成互补。

#### 1.1 paper-search-mcp：专业文献搜索（首选）

覆盖 **20+ 学术源**，并发搜索，自动去重：

| 源 | 搜索 | 下载 | 特点 |
|----|------|------|------|
| arXiv | ✅ | ✅ | 预印本，最前沿 |
| Semantic Scholar | ✅ | ✅(OA) | 引用链+影响力，**推荐优先使用** |
| PubMed | ✅ | ❌ | 生物医学 |
| bioRxiv / medRxiv | ✅ | ✅ | 生命科学预印本 |
| Crossref | ✅ | ❌ | DOI 元数据主干 |
| OpenAlex | ✅ | ❌ | 开放元数据 |
| dblp | ✅ | ❌ | 计算机科学文献 |
| CORE | ✅ | ✅ | 开放获取全文 |
| Europe PMC | ✅ | ✅ | 欧洲 PubMed 中心 |
| IACR | ✅ | ✅ | 密码学 |
| HAL | ✅ | ✅ | 法国开放存档 |
| Zenodo | ✅ | ✅ | 欧洲开放获取库 |
| Google Scholar | ⚠️ | ❌ | 发现+DOI 恢复 |
| DOAJ | ✅ | ❌ | 开放获取期刊 |
| Unpaywall | ❌ | ✅ | PDF 定位 |
| + 更多 | ✅ | 视源而定 | |

> **注意**：部分源（CORE、DOAJ）有免费 API key 可提升频率限制，无 key 也可以使用但较慢。

##### 基础搜索

```bash
# 搜索全部源（自动去重）
paper-search search "YOUR_TOPIC" --max-results 10

# 指定源（推荐：更快、更少噪音）
paper-search search "reinforcement learning from human feedback" \
  --sources arxiv,semantic,crossref,openalex \
  --max-results 10
```

##### 结构化 JSON 输出

```bash
paper-search search "YOUR_TOPIC" --sources arxiv,semantic --max-results 10 | python3 -c "
import sys, json
data = json.load(sys.stdin)
for paper in data.get('papers', []):
    print(f\"📄 {paper['title'][:80]}\")
    print(f\"   作者: {', '.join(paper['authors'][:3])}...\")
    print(f\"   年份: {paper['published_date'][:4]} | 引用: {paper.get('citations', 0)}\")
    print(f\"   PDF: {paper.get('pdf_url', 'N/A')}\")
    print()
"
```

##### 下载 PDF

```bash
# 按 ID 下载
paper-search download "2402.03300" --output ./papers/

# 多源回退下载链
# 源原生链接 → CORE/Europe PMC → Unpaywall → Sci-Hub(可选)
```

##### 多关键词搜索策略

每个关键词组合跑一次，至少跑 **4-6 组**：

```bash
# 核心词
paper-search search "YOUR_TOPIC" --sources arxiv,semantic --max-results 10

# 核心词 + 应用域
paper-search search "YOUR_TOPIC YOUR_DOMAIN" --sources arxiv --max-results 10

# 相关方法名
paper-search search "preference optimization" --sources arxiv --max-results 10

# 找 survey
paper-search search "YOUR_TOPIC survey" --sources semantic,crossref --max-results 5
```

#### 1.2 Semantic Scholar — 引用关系分析

`paper-search` 的 Semantic Scholar 源已包含引用数。如需更深引用链分析，直接用 API：

```bash
# 查看论文引用数
curl -s "https://api.semanticscholar.org/graph/v1/paper/arXiv:2402.03300?fields=title,citationCount,influentialCitationCount,year,abstract" \
  | python3 -m json.tool

# 谁引用了它（追踪后续工作）
curl -s "https://api.semanticscholar.org/graph/v1/paper/arXiv:2402.03300/citations?fields=title,authors,year&limit=10"

# 它引用了谁（找基础工作）
curl -s "https://api.semanticscholar.org/graph/v1/paper/arXiv:2402.03300/references?fields=title,authors,year&limit=10"
```

#### 1.3 AnySearch：通用搜索补漏

用于找 survey 论文、技术博客、中文资料、技术报告——`paper-search` 不覆盖的内容：

```bash
# 找 survey 论文
python3 ~/.hermes/skills/anysearch/scripts/anysearch_cli.py search \
  "YOUR_TOPIC survey 2024 2025" --max_results 5

# 找中文资料
python3 ~/.hermes/skills/anysearch/scripts/anysearch_cli.py search \
  "YOUR_TOPIC 综述 研究进展" --max_results 5

# 批量并行搜索
python3 ~/.hermes/skills/anysearch/scripts/anysearch_cli.py batch_search \
  --query "YOUR_TOPIC survey" \
  --query "YOUR_TOPIC 综述" \
  --query "YOUR_TOPIC latest progress" \
  --max_results 5
```

#### 搜索策略总结

```
层1（推荐优先）：paper-search     → 专业文献（元数据+PDF）
层2（补漏）：     AnySearch        → 通用内容（博客、教程、中文）
层3（深度）：     Semantic API     → 引用链追踪
```

**实战策略：**

1. **多角度**：核心词 + 扩展词 + 同义表达 + 中英文
2. **多源并发**：paper-search 自动并发搜索多个学术源，比单一 arXiv 更全面
3. **滚雪球**：从好论文的引用链（Semantic Scholar）找更多
4. **Survey 优先**：先读 1-2 篇 survey 可快速获得领域全景图
5. **时间分层**：同时搜近 1 年（最新）、近 3 年（主流）、5 年+（经典）
6. **遍历检查**：对于被排除的方向，简要记录排除理由，避免后续重复浪费时间

---

### Phase 2：个人知识库搜索（IMA）

> ⏱ 建议耗时：5-10 分钟

搜索你的个人文献知识库——这里已经存了你之前读过、标注过的论文，往往比从零搜索更高效。

> **API 基础信息**：
> - Base URL: `https://ima.qq.com`
> - Auth: `ima-openapi-clientid`、`ima-openapi-apikey` headers（非 Bearer token）
> - Body: JSON，`Content-Type: application/json`

#### 方法 A：搜索知识库列表

找出你有哪些知识库，然后针对特定知识库搜索：

```bash
CLIENT_ID="${IMA_OPENAPI_CLIENTID}"
API_KEY="${IMA_OPENAPI_APIKEY}"
BASE="${IMA_BASE_URL:-https://ima.qq.com}"

curl -s -X POST "$BASE/openapi/wiki/v1/search_knowledge_base" \
  -H "ima-openapi-clientid: $CLIENT_ID" \
  -H "ima-openapi-apikey: $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"query":"文献","cursor":"","limit":10}' \
  | python3 -m json.tool
```

#### 方法 B：搜索知识库内容（核心）

```bash
KB_ID="<从上面获取的 kb_id>"

curl -s -X POST "$BASE/openapi/wiki/v1/search_knowledge" \
  -H "ima-openapi-clientid: $CLIENT_ID" \
  -H "ima-openapi-apikey: $API_KEY" \
  -H "Content-Type: application/json" \
  -d "{\"query\":\"YOUR_KEYWORDS\",\"cursor\":\"\",\"knowledge_base_id\":\"$KB_ID\"}" \
  | python3 -c "
import sys, json
data = json.load(sys.stdin)
if data.get('code') != 0:
    print('Error:', data.get('msg'))
    exit()
items = data.get('data', {}).get('info_list', [])
for item in items:
    title = item.get('title', '无标题')
    media_id = item.get('media_id', '')
    media_type = item.get('media_type', -1)
    highlight = item.get('highlight_content', '')
    print(f'  📄 {title}')
    print(f'     ID: {media_id} | Type: {media_type}')
    if highlight:
        print(f'     🔍 {highlight[:150]}')
    print()
"
```

#### 方法 C：搜索笔记

IMA 笔记中可能记录了你的论文精读、想法和总结：

```bash
curl -s -X POST "$BASE/openapi/note/v1/search_note" \
  -H "ima-openapi-clientid: $CLIENT_ID" \
  -H "ima-openapi-apikey: $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"query_info":{"title":"KEYWORD","content":"KEYWORD"},"search_type":1,"sort_type":0,"start":0,"end":20}'
```

#### 搜索 IMA 的技巧

- **多种表达**：同一个概念的多种表述（中英文、缩写全称）都要试
- **搜索文件夹**：IMA 中标记的分类文件夹（`media_type: 99`）也值得关注
- **搜索笔记**：你的阅读笔记、想法和评论也是宝贵资源
- **交叉引用**：如果 IMA 有论文 A 和论文 B，但调研主题是 A+B 的交集，这也算重要发现
- **游标翻页**：搜索知识库结果使用 `cursor` 翻页（首次传空字符串，后续用 `next_cursor`）

#### IMA 不可用时的降级

如果 IMA 未配置或 API 调用失败：

1. 仅搜索公开数据库（自动降级）
2. 如果有 flomo 笔记（配置了 `short-mind` skill），可搜索 flomo 中的文献笔记
3. 配置 `~/.hermes/.env` 中的 IMA 变量来重新启用

---

### Phase 3：筛选与登记

> ⏱ 建议耗时：15-20 分钟

#### 3.1 快速筛选矩阵

对每篇论文快速判断：

| 论文 | 是否相关 | 优先级 | 理由 | 操作 |
|------|---------|--------|------|------|
| Paper A | ✅ 直接相关 | ⭐⭐⭐ | 核心方法，必须读 | 深度阅读 |
| Paper B | ✅ 间接相关 | ⭐⭐ | 方法变体，作为对比 | 快速浏览 |
| Paper C | ⚠️ 边缘相关 | ⭐ | 场景相似但方法不同 | 略读摘要 |
| Paper D | ❌ 不相关 | - | 关于不同问题 | 跳过 |

快速读摘要的方法：

```bash
# 走 arXiv → 快速纯文本
web_extract(urls=["https://arxiv.org/abs/2402.03300"])

# 或用 HTML 版
web_extract(urls=["https://arxiv.org/html/2402.03300"])
```

#### 3.2 论文登记

筛选出要读的论文后，临时登记到调研工作目录：

```markdown
# 调研暂存：<topic>

## 📥 待读
- [ ] [论文标题](arXiv:ID) | ⭐⭐⭐ | 理由 |
- [ ] [论文标题](URL) | ⭐⭐ | 理由 |

## 📖 已读
- [x] [标题] | 核心结论 | 关键词 | 阅读日期

## ❌ 已排除
- [标题] | 排除理由
```

---

### Phase 4：深度阅读与分析

> ⏱ 建议耗时：30-60 分钟/篇

#### 4.1 结构化阅读模板

对每篇高优先级论文，用以下结构提取核心信息：

```markdown
## [论文标题] (arXiv:XXXX.XXXXX)

**基本信息**
- 作者 | 年份 | 会议/期刊
- DOI/链接

**要解决的问题**
- 研究问题是什么？
- 动机/为什么重要？

**方法**
- 核心思路（一句话）
- 技术细节（关键公式/架构图）
- 与最相关工作的区别

**实验与结果**
- 数据集/设置
- 主要指标和结果（有数字就记数字）
- 消融实验结论

**局限与未来工作**

**对本调研的意义**
- 直接相关 / 对比基线 / 背景参考
- 一句话：这论文对我有什么用
```

#### 4.2 关联分析

读几篇后，停下来做**关联分析**——这比读更多论文更重要：

```markdown
## 领域结构

### 主流范式
1. 范式 A（Paper 1, 2, 3）
   - 共同假设：...
   - 适用条件：...
2. 范式 B（Paper 4, 5）
   - 与 A 的区别：...

### 关键对比维度
| 维度 | Paper 1 | Paper 2 | Paper 3 |
|------|---------|---------|---------|
| 方法核心 | ... | ... | ... |
| 适用场景 | ... | ... | ... |
| 关键假设 | ... | ... | ... |
| 性能指标 | ... | ... | ... |

### 未解决的问题（Research Gap）
1. ...
2. ...
```

> 🔑 **关键判断：** 当同一对比维度在不同论文间出现 2 次以上，就说明你找到了领域的关键张力——这正是写综述的骨架。

---

### Phase 5：综述输出

> ⏱ 建议耗时：30-60 分钟

根据调研目标选择输出格式：

#### 5.1 调研报告（摸底/找方向）

适合「这个方向有什么、我能做什么」的场景：

```markdown
# <方向> 文献调研报告

## 1. 调研范围
- 关键词 | 时间窗口 | 数据库

## 2. 领域全景
- 主要研究方向分类
- 各方向核心工作（2-3 篇代表论文）
- 发展脉络（按时间线）

## 3. 关键方法对比
- 对比表（方法/数据集/性能/适用场景）

## 4. 未解决的问题（Research Gap）
- Gap 1: 说明 + 证据
- Gap 2: 说明 + 证据

## 5. 对本项目的启示
- 可直接采用的方法
- 可改进的方向
- 需要规避的坑

## 6. 参考文献
```

#### 5.2 Related Work 段落（论文用）

```markdown
## Related Work

### <子方向 A>
[相关工作1] 做了什么，[相关工作2] 在此基础上改进了什么，但它们在 [某方面] 有局限...
我们的工作与它们的关键区别：...

### <子方向 B>
...
```

#### 5.3 文献笔记归档

调研结束后，把值得长期保存的论文笔记追加到你的长期文献库（如 IMA 知识库或 IDEA 工作区的 `05-文献库/`）。

---

## ⚡ 效率技巧

### 并行阅读

同时拉多篇论文的摘要来加快初期筛选：

```bash
web_extract(urls=[
    "https://arxiv.org/abs/2402.03300",
    "https://arxiv.org/abs/2401.12345",
    "https://arxiv.org/abs/2403.00001"
])
```

### 递减搜索法

```
第一轮：搜 "survey" / "review" → 拿到领域全景（1-2 篇 survey）
第二轮：从 survey 的引用链抓关键论文
第三轮：搜近 1 年的最新成果（追截止日期）
第四轮：验证性搜索（确认没有遗漏重要方向）
```

### 时间盒

给每个阶段设定时间预算，防止在搜论文阶段无限发散：

| 阶段 | 建议耗时 |
|------|---------|
| Phase 0：范围定义 | 10-15 分钟 |
| Phase 1：公开搜索 | 20-30 分钟 |
| Phase 2：个人搜索 | 5-10 分钟 |
| Phase 3：筛选+登记 | 15-20 分钟 |
| Phase 4：深度阅读 | 30-60 分钟/篇 |
| Phase 5：综述输出 | 30-60 分钟 |

### 其他技巧

- **关注有影响力的论文**：Semantic Scholar 的 `influentialCitationCount` 能帮你过滤真正重要的工作
- **不要忽视负面结果**：排除的论文记录原因，避免后续重复踩坑
- **善用 HTML 版**：arXiv 的 HTML 全文版比 PDF 加载快得多，适合快速筛选
- **批量下载**：调研后期可一次性下载所有高优先级 PDF 以便离线阅读

---

## 🏃 快查表

| 你要做什么 | 用这一步 |
|-----------|---------|
| 搜学术文献（专业） | Phase 1 → `paper-search search`（支持 20+ 源） |
| 搜最新预印本 | Phase 1 → `paper-search search --sources arxiv` |
| 查论文影响力/引用链 | Phase 1 → `paper-search search --sources semantic` 或 Semantic Scholar API |
| 找 survey/博客/教程 | Phase 1 → AnySearch 通用搜索 |
| 搜中文资料 | Phase 1 → AnySearch `"综述 研究进展"` |
| 从我已存的找 | Phase 2 → IMA 搜索 |
| 下载 PDF | Phase 1 → `paper-search download` |
| 快速判断值不值得读 | Phase 3 → 读摘要 |
| 记一篇论文笔记 | Phase 4 → 结构化模板 |
| 写 Related Work | Phase 5 → Related Work 格式 |
| 写调研报告 | Phase 5 → 调研报告模板 |

---

## ⚠️ 局限性

1. **arXiv 局限性**：arXiv 上的论文未经同行评审，且不覆盖已发表的期刊/会议论文中后期版本。重要论文应同时查 Semantic Scholar 确认最终发表版本。
2. **IMA 覆盖度**：IMA 中只有你**主动收集**的论文——搜索结果的完备性取决于你的日常积累。建议平时养成收藏论文的习惯。
3. **API 速率限制**：本工作流依赖公开 API 的可用性和响应速度。若 API 限制（如 arXiv 1 req/3s、Semantic Scholar 1 req/s），搜索阶段可能较慢。
4. **不替代系统性综述**：对于需要严格方法论的系统性文献综述（如 PRISMA 标准），本工作流的基础搜索覆盖度可能不足，应配合专业的文献数据库（Web of Science、Scopus 等）。

---

## 🔗 相关项目

- [research-ideation](https://github.com/zhonxia/research-ideation) — 研究点子生成与评估（互补工作流，建议在文献调研后使用）
- [paper-search-mcp](https://github.com/openags/paper-search-mcp) — 多源学术论文搜索 CLI
- [AnySearch](https://github.com/anysearch-ai/anysearch-skill) — 通用网页搜索 Hermes skill
- [short-mind](https://github.com/zhonxia/short-mind) — 个人知识库搜索（flomo 笔记替代方案）

---

## 📄 许可证

[MIT](./LICENSE)

---

<p align="center">
  <sub>Built with ❤️ by <a href="https://github.com/zhonxia">zhonxia</a></sub>
  <br>
  <sub>有问题或建议？<a href="https://github.com/zhonxia/personal-literature-survey/issues">提交 Issue</a></sub>
</p>

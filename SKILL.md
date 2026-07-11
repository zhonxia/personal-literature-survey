---
name: personal-literature-survey
description: "系统化个人文献调研工作流——结合学术数据库搜索（arXiv、Semantic Scholar）和个人知识库（IMA 腾讯知识库）进行文献检索、筛选、阅读、分析和综述写作。适合做研究前摸底、写论文 related work、竞赛技术调研、课程项目文献综述等场景。"
metadata:
  version: "1.0.0"
  requires:
    - env: IMA_OPENAPI_CLIENTID (optional, 腾讯 IMA 知识库 OpenAPI Client ID)
    - env: IMA_OPENAPI_APIKEY (optional, 腾讯 IMA 知识库 OpenAPI API Key)
    - env: IMA_BASE_URL (optional, 默认 https://ima.qq.com)
  related_skills:
    - arxiv
    - research-ideation
    - short-mind
    - anysearch
  requires_commands:
    - paper-search (pip install paper-search-mcp)
---

# Personal Literature Survey（个人文献调研）

系统化的个人文献调研方法论。在动笔写论文、做项目、或参加竞赛之前，用这个工作流摸清「这个方向已经有什么、差什么、我的贡献在哪里」。

## 核心理念

文献调研不是「读一堆论文然后总结一下」——它是一个**有目标的搜索-筛选-分析过程**：

1. **搜索**：既要搜公开学术数据库，也要搜你的个人知识库（IMA）
2. **筛选**：用 structured criteria 快速判断相关/不相关，不恋战
3. **分析**：不只「这篇做了什么」，更要「这个方向整体结构是什么」
4. **输出**：可消费的综述文档，不是笔记散片

## 调研前的准备工作

### 1. 定义调研范围

在开始之前，必须与用户确认：

```
**研究方向**: [一句话描述]
**核心问题**: [具体要回答的研究问题]
**关键词** (中文+英文):
  - 核心词: [3-5个]
  - 扩展词: [相关概念、同义词、上下位词]
**搜索范围**:
  - 时间窗口: 近3年/近5年/全部
  - 文献类型: 期刊论文/会议论文/预印本/报告
  - 学科限制: [如有]
**排除标准**: [明确排除哪些方向/方法]
**调研目标**: [摸底/找baseline/找方法/写related work/找合作者]
```

> 如果用户说「帮我看看这个方向」，你也应该帮他反向提问以上内容来缩小范围。

### 2. 检查 IMA 知识库配置

在每次调研开始时检查 IMA API 配置是否可用：

```bash
# 检查环境变量是否配置
echo "CLIENT_ID=${IMA_OPENAPI_CLIENTID:0:10}... (${IMA_OPENAPI_CLIENTID:+已配置}${IMA_OPENAPI_CLIENTID:-未配置})"
echo "API_KEY=${IMA_OPENAPI_APIKEY:0:10}... (${IMA_OPENAPI_APIKEY:+已配置}${IMA_OPENAPI_APIKEY:-未配置})"
```

未配置时走**降级方案**：只搜公开数据库，跳过 IMA。

---

## 调研工作流（分阶段执行）

```
┌─────────────────────────────────────────────┐
│ Phase 0: 范围定义 ← 用户确认                │
├─────────────────────────────────────────────┤
│ Phase 1: 公开学术数据库搜索                  │
│   ├── arXiv (最新预印本)                     │
│   ├── Semantic Scholar (引用/影响力)         │
│   └── 综合搜索 (web_search)                 │
├─────────────────────────────────────────────┤
│ Phase 2: 个人知识库搜索 (IMA)                │
│   └── 在 IMA 中搜索已收集的相关文献          │
├─────────────────────────────────────────────┤
│ Phase 3: 筛选与初步阅读                      │
│   └── 快速回填 relevance / 优先级            │
├─────────────────────────────────────────────┤
│ Phase 4: 深度阅读与分析                      │
│   └── 用结构化模板追踪每篇论文               │
├─────────────────────────────────────────────┤
│ Phase 5: 综述输出                            │
│   └── 调研报告 / related work / 文献综       │
└─────────────────────────────────────────────┘
```

---

## Phase 1：公开学术数据库搜索

使用两个搜索工具形成互补：
- **paper-search-mcp** → 专业文献搜索（arXiv, PubMed, Semantic Scholar 等 20+ 学术源）
- **AnySearch** → 通用网页搜索（survey 论文、技术博客、教程、中文资料）

### 1.1 paper-search-mcp：专业文献搜索（首选）

已安装 CLI：`paper-search`（`pip install paper-search-mcp`）

**覆盖 20+ 学术源：**

| 源 | 搜索 | 下载 | 特点 |
|----|------|------|------|
| arXiv | ✅ | ✅ | 预印本，最前沿 |
| Semantic Scholar | ✅ | ✅(OA) | 引用链+影响力，推荐 |
| PubMed | ✅ | ❌ | 生物医学 |
| bioRxiv/medRxiv | ✅ | ✅ | 生命科学预印本 |
| Crossref | ✅ | ❌ | DOI 元数据主干 |
| OpenAlex | ✅ | ❌ | 开放元数据 |
| dblp | ✅ | ❌ | 计算机科学文献 |
| CORE | ✅ | ✅ | 开放获取全文 |
| Europe PMC | ✅ | ✅ | 欧洲 PubMed 中心 |
| Google Scholar | ⚠️ | ❌ | 发现+DOI 恢复 |
| IACR | ✅ | ✅ | 密码学 |
| HAL | ✅ | ✅ | 法国开放存档 |
| Zenodo | ✅ | ✅ | 欧洲开放获取库 |

> **注意**：部分源（CORE、DOAJ）有免费 API key 可提升频率限制，无 key 也可以使用但较慢。

#### 基础搜索

```bash
# 搜索全部源（并发搜索，自动去重）
paper-search search "YOUR_TOPIC" --max-results 10

# 指定源（推荐：提速 + 减少噪音）
paper-search search "reinforcement learning from human feedback" \
  --sources arxiv,semantic,crossref,openalex \
  --max-results 10

# 搜索特定领域
paper-search search "RLHF in education" \
  --sources arxiv,semantic,dblp \
  --max-results 5
```

#### 结构化输出

每个搜索结果包含完整元数据：

```json
{
  "paper_id": "2402.03300",
  "title": "Paper Title",
  "authors": ["Author 1", "Author 2"],
  "abstract": "...",
  "doi": "10.xxxx/xxxxx",
  "published_date": "2024-02-05",
  "pdf_url": "https://arxiv.org/pdf/2402.03300",
  "url": "http://arxiv.org/abs/2402.03300",
  "source": "arxiv",
  "citations": 42,
  "categories": "cs.AI; cs.LG"
}
```

用 Python 解析：

```python
import json, subprocess
result = subprocess.run(
    ["paper-search", "search", "YOUR_TOPIC", "--sources", "arxiv,semantic", "--max-results", "10"],
    capture_output=True, text=True
)
data = json.loads(result.stdout)
for paper in data.get("papers", []):
    print(f"📄 {paper['title'][:80]}")
    print(f"   Authors: {', '.join(paper['authors'][:3])}...")
    print(f"   Year: {paper['published_date'][:4]} | Cited: {paper.get('citations', 0)}")
    print(f"   PDF: {paper.get('pdf_url', 'N/A')}")
    print()
```

#### 下载 PDF

```bash
# 按 ID 下载（arXiv ID、DOI 等）
paper-search download "2402.03300" --output ./papers/

# 多源回退下载链：源原生链接 → CORE/Europe PMC → Unpaywall → Sci-Hub(可选)
```

#### 多关键词搜索策略

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

### 1.2 Semantic Scholar（引用关系 + 影响力）

`paper-search` 的 Semantic Scholar 源已经包含引用数。如需更深引用链分析，直接用 API：

```bash
# 检查论文引用数
curl -s "https://api.semanticscholar.org/graph/v1/paper/arXiv:2402.03300?fields=title,citationCount,influentialCitationCount,year,abstract" \
  | python3 -m json.tool

# 谁引用了它（追踪后续工作）
curl -s "https://api.semanticscholar.org/graph/v1/paper/arXiv:2402.03300/citations?fields=title,authors,year&limit=10" \
  | python3 -m json.tool

# 它引用了谁（找基础工作）
curl -s "https://api.semanticscholar.org/graph/v1/paper/arXiv:2402.03300/references?fields=title,authors,year&limit=10" \
  | python3 -m json.tool
```

### 1.3 AnySearch：通用搜索补漏

用于找 survey 论文、技术博客、中文资料、技术报告——`paper-search` 不覆盖的内容。

```bash
# 准备好 CLI
AS_CLI="python3 ~/.hermes/skills/anysearch/scripts/anysearch_cli.py"

# survey 论文通常覆盖全面
$AS_CLI search "YOUR_TOPIC survey 2024 2025" --max_results 5

# 找最新进展追踪
$AS_CLI search "YOUR_TOPIC latest advances tutorial" --max_results 5

# 中文资料（有些方向中文学术资源更丰富）
$AS_CLI search "YOUR_TOPIC 综述 研究进展" --max_results 5

# 提取网页内容（读博客/tutorial）
$AS_CLI extract "https://example.com/blog"

# 批量并行搜索
$AS_CLI batch_search \
  --query "YOUR_TOPIC survey" \
  --query "YOUR_TOPIC 综述" \
  --query "YOUR_TOPIC latest progress" \
  --max_results 5
```

### 1.4 搜索策略说明

```text
层1（推荐优先）：paper-search     → 专业文献（元数据+PDF）
层2（补漏）：     AnySearch        → 通用内容（博客、教程、中文）
层3（深度）：     Semantic API     → 引用链追踪
```

调研过程中使用以下策略确保覆盖度：

1. **多角度**：核心词 + 扩展词 + 同义表达 + 中英文
2. **多源并发**：paper-search 自动并发搜索多个学术源，比单一 arXiv 更全面
3. **滚雪球**：从好论文的引用链（Semantic Scholar）找更多
4. **survey 优先**：先读 survey 可快速获得领域全景图
5. **时间分层**：同时搜近 1 年（最新）、近 3 年（主流）、5 年+（经典）
6. **遍历检查**：对于被排除的方向，简要记录排除理由，避免后续重复浪费时间

---

## Phase 2：个人知识库搜索（IMA 腾讯知识库）

### 2.1 配置（已完成）

```env
# ~/.hermes/.env（已配置）
IMA_BASE_URL=https://ima.qq.com
IMA_OPENAPI_CLIENTID=<你的 Client ID>
IMA_OPENAPI_APIKEY=<你的 API Key>
```

### 2.2 搜索 IMA — 核心方法

> **API 基础信息**：
> - Base URL: `https://ima.qq.com`
> - Auth: `ima-openapi-clientid`、`ima-openapi-apikey` headers（非 Bearer token）
> - Body: JSON，`Content-Type: application/json`

搜索你的个人文献知识库——这里已经存了你之前读过、标注过的论文，往往比从零搜索更高效。

#### 方法 A：搜索知识库列表（先找有哪些知识库）

找出你有哪些知识库（如"文献收集"、"BRB 论文"等），然后针对特定知识库搜索：

```bash
# 环境变量（已配置）
CLIENT_ID="${IMA_OPENAPI_CLIENTID:-}"
API_KEY="${IMA_OPENAPI_APIKEY:-}"
BASE="${IMA_BASE_URL:-https://ima.qq.com}"

# 搜索知识库
curl -s -X POST "$BASE/openapi/wiki/v1/search_knowledge_base" \
  -H "ima-openapi-clientid: $CLIENT_ID" \
  -H "ima-openapi-apikey: $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"query":"文献","cursor":"","limit":10}' \
  | python3 -m json.tool
```

**响应示例**（知识库列表）：
```json
{
  "code": 0,
  "data": {
    "info_list": [{
      "kb_id": "...",
      "kb_name": "文献收集",
      "content_count": "51",
      "description": "相关文献收集"
    }]
  }
}
```

#### 方法 B：搜索知识库内容（核心文献搜索）

在指定知识库中搜索文献标题和内容：

```bash
KB_ID="<从上一步获取的 kb_id>"

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

#### 方法 C：搜索笔记（找你的阅读笔记）

IMA 笔记中可能记录了你的论文精读、想法和总结：

```bash
# 搜索笔记标题或正文
curl -s -X POST "$BASE/openapi/note/v1/search_note" \
  -H "ima-openapi-clientid: $CLIENT_ID" \
  -H "ima-openapi-apikey: $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{
    "query_info": {
      "title": "KEYWORD",
      "content": "KEYWORD"
    },
    "search_type": 1,
    "sort_type": 0,
    "start": 0,
    "end": 20
  }' \
  | python3 -c "
import sys, json
data = json.load(sys.stdin)
if data.get('code') != 0:
    print('Error:', data.get('msg'))
    exit()
notes = data.get('data', {}).get('search_note_infos', [])
for n in notes:
    info = n.get('note_book_info', {})
    note_id = info.get('note_id', '')
    title = info.get('title', '无标题')
    summary = info.get('summary', '')[:100]
    hl = n.get('highlightInfo', {}).get('doc_title', '')
    print(f'  📝 {title}')
    print(f'     ID: {note_id}')
    if summary:
        print(f'     {summary}')
    if hl:
        print(f'     > {hl}')
    print()
"

# 获取笔记全文
curl -s -X POST "$BASE/openapi/note/v1/get_doc_content" \
  -H "ima-openapi-clientid: $CLIENT_ID" \
  -H "ima-openapi-apikey: $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"note_id":"NOTE_ID_FROM_SEARCH","target_content_format":0}' \
  | python3 -c "
import sys, json
data = json.load(sys.stdin)
if data.get('code') == 0:
    print(data.get('data', {}).get('content', ''))
"
```

#### 方法 D：浏览知识库目录结构

```bash
# 获取知识库信息
curl -s -X POST "$BASE/openapi/wiki/v1/get_knowledge_base" \
  -H "ima-openapi-clientid: $CLIENT_ID" \
  -H "ima-openapi-apikey: $API_KEY" \
  -H "Content-Type: application/json" \
  -d "{\"ids\":[\"$KB_ID\"]}"

# 浏览知识库内容（带游标翻页）
curl -s -X POST "$BASE/openapi/wiki/v1/get_knowledge_list" \
  -H "ima-openapi-clientid: $CLIENT_ID" \
  -H "ima-openapi-apikey: $API_KEY" \
  -H "Content-Type: application/json" \
  -d "{\"cursor\":\"\",\"limit\":20,\"knowledge_base_id\":\"$KB_ID\"}"
```

**搜索 IMA 时的技巧：**

- **多种表达**：IMA 是你的个人语料库，同一个概念的多种表述（中英文、缩写全称）都要试
- **搜索已标注论文**：你在 IMA 中可能已经标记了分类文件夹（如「基础BRB」、「应用研究」等），文件夹也是搜索结果的一部分（`media_type: 99`）
- **搜索笔记**：你写的阅读笔记、想法、评论也是宝贵资源
- **交叉引用**：如果 IMA 中有论文 A 和论文 B，但调研主题是 A+B 的交集，这也算重要发现
- **翻页**：搜索知识库结果使用 `cursor` 翻页（首次传空字符串，后续用返回的 `next_cursor`）

### 2.3 IMA 不可用时的降级

如果 IMA 未配置或 API 调用失败：

1. 向用户说明「IMA 未连接，仅搜索公开数据库」
2. 如果用户有 flomo 笔记（配置了 short-mind skill），可以用 `short-mind` 搜索 flomo 中的文献笔记
3. 提醒用户可配置 `~/.hermes/.env` 中的以下变量来启用 IMA：
   ```env
   IMA_BASE_URL=https://ima.qq.com
   IMA_OPENAPI_CLIENTID=<你的 Client ID>
   IMA_OPENAPI_APIKEY=<你的 API Key>
   ```

---

## Phase 3：筛选与初步阅读

### 3.1 快速筛选矩阵

对于 Phase 1+2 搜到的每篇论文，快速判断：

| 论文 | 是否相关 | 优先级 | 理由 | Action |
|------|---------|--------|------|--------|
| Paper A | ✅ 直接相关 | ⭐⭐⭐ | 核心方法，必须读 | 深度阅读 |
| Paper B | ✅ 间接相关 | ⭐⭐ | 方法变体，作为对比 | 快速浏览 |
| Paper C | ⚠️ 边缘相关 | ⭐ | 场景相似但方法不同 | 略读摘要 |
| Paper D | ❌ 不相关 | - | 关于不同问题 | 跳过 |

**执行方法：**

```bash
# 快速读摘要（走 arXiv → 快，纯文本）
web_extract(urls=["https://arxiv.org/abs/2402.03300"])

# 或用浏览器读 HTML 版（如果 arXiv 有 HTML）
web_extract(urls=["https://arxiv.org/html/2402.03300"])
```

### 3.2 论文登记

筛选出要读的论文后，临时登记到调研工作目录（不是长久保存，是调研过程中的暂存）：

```markdown
# 调研暂存：<topic>

## 📥 待读
- [ ] [论文标题](arXiv:ID) | ⭐⭐⭐ | 理由 |
- [ ] [论文标题](URL) | ⭐⭐ | 理由 |

## 📖 已读
- [x] [标题] | 核心结论 | 关键词 | date-read

## ❌ 已排除
- [标题] | 排除理由
```

---

## Phase 4：深度阅读与分析

### 4.1 结构化阅读模板

对每篇高优先级论文，用以下结构提取核心信息：

```markdown
## [论文标题] (arXiv:XXXX.XXXXX)

**基本信息**
- 作者 | 年份 | 会议/期刊
- DOI/链接

**要解决的问题**
- 研究问题是什么？
- 她们的动机/为什么重要？

**方法**
- 核心思路（一句话）
- 技术细节（关键公式/架构图）
- 与最相关工作的区别

**实验与结果**
- 数据集/设置
- 主要指标和结果（有数字就记数字）
- 消融实验结论

**局限与未来工作**

**对于本调研的意义**
- 直接相关 / 对比基线 / 背景参考
- 一句话: 这论文对我有什么用
```

### 4.2 关联分析

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
| 维度 | Paper 1 | Paper 2 | Paper 3 | Paper 4 |
|------|---------|---------|---------|---------|
| 方法核心 | ... | ... | ... | ... |
| 适用场景 | ... | ... | ... | ... |
| 关键假设 | ... | ... | ... | ... |
| 性能指标 | ... | ... | ... | ... |

### 未解决的问题（Research Gap）
1. ...
2. ...
```

> **关键判断：** 当同一对比维度在不同论文间出现 2 次以上，就说明你找到了领域的关键张力——这正是写综述的骨架。

---

## Phase 5：综述输出

根据调研目标选择输出格式：

### 5.1 调研报告（摸底/找方向）

适合「这个方向有什么、我能做什么」的场景：

```markdown
# <方向> 文献调研报告

## 1. 调研范围
- 关键词 | 时间窗口 | 数据库

## 2. 领域全景
- 主要研究方向分类
- 各方向核心工作（2-3篇代表论文）
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

### 5.2 Related Work 段落

适合写论文时用：

```markdown
## Related Work

### <子方向 A>
[相关工作1] 做了什么，[相关工作2] 在此基础上改进了什么，但它们在 [某方面] 有局限...
我们的工作与它们的关键区别：...

### <子方向 B>
...
```

### 5.3 文献笔记归档

调研结束后，把值得长期保存的论文笔记追加到你的 IDEA 工作区的 `05-文献库/`（如果已按 `research-ideation` skill 设置了 IDEA 系统），或追加到 IMA 知识库。

---

## 效率技巧

### 并行阅读

```bash
# 同时拉多篇论文的 PDF/摘要来加快初期筛选
web_extract(urls=[
    "https://arxiv.org/abs/2402.03300",
    "https://arxiv.org/abs/2401.12345",
    "https://arxiv.org/abs/2403.00001"
])
```

### 递减搜索法

```
第一轮：搜 "survey" / "review" → 拿到领域全景（1-2篇 survey）
第二轮：从 survey 的引用链抓关键论文
第三轮：搜近 1 年的最新成果（追截止日期）
第四轮：验证性搜索（确认没有遗漏重要方向）
```

### 时间盒

给每个阶段设定时间预算，防止在搜论文阶段无限发散：

| 阶段 | 建议耗时 |
|------|---------|
| Phase 0 范围定义 | 10-15 min |
| Phase 1 公开搜索 | 20-30 min |
| Phase 2 IMA 搜索 | 5-10 min |
| Phase 3 筛选+登记 | 15-20 min |
| Phase 4 深度阅读 | 30-60 min/篇 |
| Phase 5 综述输出 | 30-60 min |

---

## 局限性说明

1. **arXiv 局限性**：arXiv 上的论文未经同行评审，且不覆盖已发表的期刊/会议论文中后期版本。重要论文应同时查 Semantic Scholar 确认最终发表版本。
2. **IMA 覆盖度**：IMA 中只有你**主动收集**的论文——搜索结果的完备性取决于你的日常积累。
3. **时效性**：本工作流依赖公开 API 的可用性和响应速度。若 API 限制（如 arXiv 1 req/3s、Semantic Scholar 1 req/s），搜索阶段可能较慢。
4. **不替代系统性综述**：对于需要严格方法论的系统性文献综述（如 PRISMA 标准），本工作流的基础搜索覆盖度可能不足，应配合专业的文献数据库（Web of Science、Scopus 等）。

## 配置说明

### IMA API 配置（已配置）

已在 `~/.hermes/.env` 中配置：

```env
IMA_BASE_URL=https://ima.qq.com
IMA_OPENAPI_CLIENTID=你的ClientID
IMA_OPENAPI_APIKEY=你的APIKey
```

### 环境检查

每次使用本 skill 时，自动检查 IMA 配置：

```bash
# 检查 IMA 配置
CLIENT_ID="${IMA_OPENAPI_CLIENTID:-}"
API_KEY="${IMA_OPENAPI_APIKEY:-}"
if [ -n "$CLIENT_ID" ] && [ -n "$API_KEY" ]; then
    echo "[IMA] ✅ 已配置 — 将搜索个人知识库"
else
    echo "[IMA] ⚠️ 未配置 — 仅搜索公开数据库"
    echo "  配置方式: 在 ~/.hermes/.env 中添加 IMA_OPENAPI_CLIENTID 和 IMA_OPENAPI_APIKEY"
fi
```

### IMA API 参考

| 接口 | 路径 | 用途 |
|------|------|------|
| 搜索知识库列表 | `POST /openapi/wiki/v1/search_knowledge_base` | 找出有哪些知识库 |
| 搜索知识库内容 | `POST /openapi/wiki/v1/search_knowledge` | 在知识库中搜文献 |
| 浏览知识库 | `POST /openapi/wiki/v1/get_knowledge_list` | 按目录浏览知识库 |
| 获取知识库信息 | `POST /openapi/wiki/v1/get_knowledge_base` | 获取知识库元信息 |
| 搜索笔记 | `POST /openapi/note/v1/search_note` | 搜索笔记标题/正文 |
| 获取笔记内容 | `POST /openapi/note/v1/get_doc_content` | 读取笔记全文 |
| 笔记本列表 | `POST /openapi/note/v1/list_notebook` | 列出所有笔记本 |
```

---

## 快查表

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
| 写 related work | Phase 5 → Related Work 格式 |
| 写调研报告 | Phase 5 → 调研报告模板 |

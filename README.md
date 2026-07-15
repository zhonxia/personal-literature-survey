<p align="center">
  <picture>
    <source media="(prefers-color-scheme: dark)" srcset="https://img.shields.io/badge/status-active-success?style=for-the-badge&label=Personal%20Literature%20Survey">
    <img alt="Personal Literature Survey" src="https://img.shields.io/badge/status-active-success?style=for-the-badge&label=Personal%20Literature%20Survey">
  </picture>
</p>

<h1 align="center">📚 Personal Literature Survey</h1>

<p align="center">
  <em>A systematic workflow for personal literature review — before writing a paper, starting a project, or entering a competition, map out <strong>what exists, what's missing, and where your contribution belongs</strong>.</em>
</p>

<p align="center">
  <a href="README.zh.md">🇨🇳 中文版</a>
  ·
  <a href="https://github.com/zhonxia/personal-literature-survey">GitHub</a>
</p>

<p align="center">
  <img src="https://img.shields.io/badge/workflow-5--stage-blue?style=flat-square" alt="5-Stage Workflow">
  <img src="https://img.shields.io/badge/sources-20%2B%20academic%20databases-brightgreen?style=flat-square" alt="20+ Academic Sources">
  <img src="https://img.shields.io/badge/license-MIT-green?style=flat-square" alt="MIT License">
  <img src="https://img.shields.io/badge/python-3.9%2B-blue?style=flat-square" alt="Python 3.9+">
</p>

---

## 📋 Table of Contents

- [What Is This?](#-what-is-this)
- [Core Capabilities](#-core-capabilities)
- [Workflow Overview](#-workflow-overview)
- [Prerequisites](#-prerequisites)
- [Quick Start](#-quick-start)
- [Detailed Usage](#-detailed-usage)
  - [Phase 0: Scope Definition](#phase-0-scope-definition)
  - [Phase 1: Public Academic Search](#phase-1-public-academic-search)
  - [Phase 2: Personal Knowledge Base Search](#phase-2-personal-knowledge-base-search)
  - [Phase 3: Screening & Registration](#phase-3-screening--registration)
  - [Phase 4: Deep Reading & Analysis](#phase-4-deep-reading--analysis)
  - [Phase 5: Synthesis Report](#phase-5-synthesis-report)
- [Efficiency Tips](#-efficiency-tips)
- [Quick Reference](#-quick-reference)
- [Limitations](#-limitations)
- [Related Projects](#-related-projects)
- [License](#-license)

---

## 🎯 What Is This?

**Personal Literature Survey** is a structured, multi-source methodology for conducting personal literature reviews. It helps researchers, students, and engineers quickly map a research field before committing to a project.

Unlike "just read a bunch of papers and summarize," this workflow treats literature review as a **goal-driven search–filter–analyze process**:

1. **Search** — both public academic databases and your personal knowledge base
2. **Screen** — with structured criteria; don't dawdle on irrelevant papers
3. **Analyze** — not just "what each paper did," but "what's the field's landscape"
4. **Synthesize** — produce a consumable survey document, not scattered notes

---

## ✨ Core Capabilities

| Capability | Description |
|-----------|-------------|
| **Multi-source academic search** | Concurrent search across 20+ academic databases via `paper-search-mcp` (arXiv, PubMed, Semantic Scholar, CrossRef, OpenAlex, dblp, CORE, and more) |
| **General web search fallback** | Catch surveys, technical blogs, tutorials, and Chinese-language resources via AnySearch |
| **Personal knowledge base integration** | Search papers already collected in your IMA (Tencent Knowledge Base) or flomo notes |
| **Structured 5-stage workflow** | Scope definition → Search → Screening → Deep reading → Synthesis output |
| **PDF download chain** | Automatic multi-source fallback for downloading full-text papers |
| **Citation network analysis** | Track forward/backward citations via Semantic Scholar API |
| **Structured reading templates** | Consistent format for capturing paper insights |
| **Relationship analysis** | Identify paradigms, compare dimensions, and discover research gaps |

---

## 🔄 Workflow Overview

```
┌────────────────────────────────────────────────────────────┐
│                     Phase 0: Scope Definition              │
│  ┌─ Research question ─ Keywords ─ Time window ─ Goal ─┐  │
│  └─────────────────── User confirmation ───────────────┘  │
├────────────────────────────────────────────────────────────┤
│              Phase 1: Public Academic Search                │
│  ┌──────────────────────────────────────────────────────┐  │
│  │   paper-search-mcp (20+ academic sources)            │  │
│  │   ├── arXiv · Semantic Scholar · PubMed              │  │
│  │   ├── CrossRef · OpenAlex · dblp · CORE              │  │
│  │   ├── bioRxiv · medRxiv · Europe PMC · IACR          │  │
│  │   ├── HAL · Zenodo · Google Scholar                  │  │
│  │   └── DOAJ · Unpaywall · 3+ more                     │  │
│  ├──────────────────────────────────────────────────────┤  │
│  │   AnySearch (general web fallback)                   │  │
│  │   ├── Survey papers · Tech blogs · Tutorials         │  │
│  │   └── Chinese-language resources                     │  │
│  └──────────────────────────────────────────────────────┘  │
├────────────────────────────────────────────────────────────┤
│              Phase 2: Personal Knowledge Search             │
│  ┌──────────────────────────────────────────────────────┐  │
│  │   IMA (Tencent Knowledge Base)                       │  │
│  │   ├── Previously collected papers                    │  │
│  │   ├── Reading notes & annotations                    │  │
│  │   └── Categorized collections                        │  │
│  └──────────────────────────────────────────────────────┘  │
├────────────────────────────────────────────────────────────┤
│             Phase 3: Screening & Registration              │
│  ┌──────────────────────────────────────────────────────┐  │
│  │   Quick relevance assessment                        │  │
│  │   Priority matrix (direct / indirect / edge / skip) │  │
│  │   Paper registration (to-read / read / excluded)    │  │
│  └──────────────────────────────────────────────────────┘  │
├────────────────────────────────────────────────────────────┤
│              Phase 4: Deep Reading & Analysis               │
│  ┌──────────────────────────────────────────────────────┐  │
│  │   Structured reading per paper                       │  │
│  │   Cross-paper relationship analysis                  │  │
│  │   Paradigm identification & comparison               │  │
│  │   Research gap discovery                             │  │
│  └──────────────────────────────────────────────────────┘  │
├────────────────────────────────────────────────────────────┤
│                 Phase 5: Synthesis Output                   │
│  ┌──────────────────────────────────────────────────────┐  │
│  │   Survey report (scouting / direction-finding)       │  │
│  │   Related Work section (for papers)                  │  │
│  │   Archived reading notes                             │  │
│  └──────────────────────────────────────────────────────┘  │
└────────────────────────────────────────────────────────────┘
```

---

## 📦 Prerequisites

| Tool | Installation | Purpose |
|------|-------------|---------|
| [paper-search-mcp](https://github.com/openags/paper-search-mcp) | `pip install paper-search-mcp` | Professional academic search across 20+ sources |
| [AnySearch](https://github.com/anysearch-ai/anysearch-skill) | Hermes skill | General web search as fallback |
| IMA (Tencent Knowledge Base) | [ima.qq.com](https://ima.qq.com) (optional) | Personal paper knowledge base |
| Semantic Scholar API | Free, no key needed | Citation network analysis |
| flomo / short-mind | Optional | Alternative personal knowledge base |

---

## 🚀 Quick Start

### 1. Install paper-search-mcp

```bash
pip install paper-search-mcp
```

### 2. Define Your Research Scope

Before searching, clarify your target with this template:

```text
Research Direction: [one-line description]
Core Question: [specific research question]
Keywords (EN/CN):
  - Core: [3-5 terms]
  - Extended: [related concepts, synonyms]
Scope:
  - Time window: last 3 years / 5 years / all
  - Paper type: journal / conference / preprint / report
Exclusion criteria: [what to skip]
Goal: [scouting / baseline / method / related work / collaboration]
```

### 3. Run Your First Search

```bash
# Search all sources concurrently
paper-search search "YOUR_TOPIC" --max-results 10

# Or target specific sources (faster, less noise)
paper-search search "reinforcement learning from human feedback" \
  --sources arxiv,semantic,crossref,openalex \
  --max-results 10
```

### 4. Download Papers

```bash
# Download by arXiv ID or DOI
paper-search download "2402.03300" --output ./papers/
```

### 5. Read & Synthesize

Use the structured reading templates in [Phase 4](#phase-4-deep-reading--analysis) and output formats in [Phase 5](#phase-5-synthesis-report).

---

## 📖 Detailed Usage

### Phase 0: Scope Definition

> ⏱ Estimated time: 10-15 minutes

Before any search, confirm the scope with your user (or yourself). Key questions:

- **What exactly** are you researching?
- **Why does** this matter?
- **What already** exists in this space?
- **What is** your unique angle?
- **How broad/deep** does the survey need to be?

Document the scope in a structured format — this prevents rabbit-holing and makes your output measurable.

---

### Phase 1: Public Academic Search

> ⏱ Estimated time: 20-30 minutes

Uses two complementary tools:

#### 1.1 paper-search-mcp (Primary)

Concurrent search across **20+ academic sources** with automatic deduplication:

| Source | Search | Download | Notes |
|--------|--------|----------|-------|
| arXiv | ✅ | ✅ | Preprints, cutting edge |
| Semantic Scholar | ✅ | ✅ (OA) | Citation graph + impact, **recommended** |
| PubMed | ✅ | ❌ | Biomedical |
| bioRxiv / medRxiv | ✅ | ✅ | Life science preprints |
| Crossref | ✅ | ❌ | DOI metadata backbone |
| OpenAlex | ✅ | ❌ | Open scholarly metadata |
| dblp | ✅ | ❌ | Computer science |
| CORE | ✅ | ✅ | Open access full text |
| Europe PMC | ✅ | ✅ | European PubMed Central |
| IACR | ✅ | ✅ | Cryptography |
| HAL | ✅ | ✅ | French open archive |
| Zenodo | ✅ | ✅ | European open repository |
| Google Scholar | ⚠️ | ❌ | Discovery + DOI resolution |
| DOAJ | ✅ | ❌ | Open access journals |
| Unpaywall | ❌ | ✅ | PDF finding |
| + more... | ✅ | varies | |

> **Note**: Some sources (CORE, DOAJ) offer free API keys for higher rate limits — usable without keys but slower.

**Basic search:**

```bash
# Search specific sources (recommended for speed)
paper-search search "YOUR_TOPIC" \
  --sources arxiv,semantic,crossref,openalex \
  --max-results 10
```

**Structured JSON output:**

```bash
paper-search search "YOUR_TOPIC" --sources arxiv,semantic --max-results 10 | python3 -c "
import sys, json
data = json.load(sys.stdin)
for paper in data.get('papers', []):
    print(f\"📄 {paper['title'][:80]}\")
    print(f\"   Authors: {', '.join(paper['authors'][:3])}...\")
    print(f\"   Year: {paper['published_date'][:4]} | Cited: {paper.get('citations', 0)}\")
    print(f\"   PDF: {paper.get('pdf_url', 'N/A')}\")
    print()
"
```

**Multi-keyword strategy:** Run at least 4–6 keyword combinations:

```bash
# Core keywords
paper-search search "YOUR_TOPIC" --sources arxiv,semantic --max-results 10

# Core + application domain
paper-search search "YOUR_TOPIC YOUR_DOMAIN" --sources arxiv --max-results 10

# Related method
paper-search search "related_method" --sources arxiv --max-results 10

# Survey paper
paper-search search "YOUR_TOPIC survey" --sources semantic,crossref --max-results 5
```

#### 1.2 Semantic Scholar — Citation Analysis

Beyond the citation count included in `paper-search`, use the API directly for deeper analysis:

```bash
# Check citations
curl -s "https://api.semanticscholar.org/graph/v1/paper/arXiv:2402.03300?fields=title,citationCount,influentialCitationCount,year,abstract" \
  | python3 -m json.tool

# Who cited it (forward tracing)
curl -s "https://api.semanticscholar.org/graph/v1/paper/arXiv:2402.03300/citations?fields=title,authors,year&limit=10"

# What it cites (backward tracing)
curl -s "https://api.semanticscholar.org/graph/v1/paper/arXiv:2402.03300/references?fields=title,authors,year&limit=10"
```

#### 1.3 AnySearch — General Web Fallback

For content `paper-search` doesn't cover — surveys, technical blogs, Chinese-language resources:

```bash
# Find survey papers
python3 ~/.hermes/skills/anysearch/scripts/anysearch_cli.py search \
  "YOUR_TOPIC survey 2024 2025" --max_results 5

# Chinese resources
python3 ~/.hermes/skills/anysearch/scripts/anysearch_cli.py search \
  "YOUR_TOPIC 综述 研究进展" --max_results 5
```

#### Search Strategy Summary

```
Layer 1 (Priority):  paper-search      → Academic literature (metadata + PDF)
Layer 2 (Fallback):  AnySearch         → General content (blogs, tutorials, Chinese)
Layer 3 (Deep):      Semantic Scholar  → Citation network tracing
```

**Research-tested strategies:**

1. **Multi-angle**: Core terms + extensions + synonyms + bilingual
2. **Multi-source**: Automatic concurrent search across 20+ sources
3. **Snowballing**: From good papers' citation chains (Semantic Scholar)
4. **Survey-first**: Read 1–2 surveys first for the big picture
5. **Temporal layering**: Last year (frontier) + 3 years (mainstream) + 5+ years (classics)
6. **Exhaustive check**: Log exclusion reasons to avoid revisiting dead ends

---

### Phase 2: Personal Knowledge Base Search

> ⏱ Estimated time: 5-10 minutes

Search papers you've **already collected** in your personal knowledge base (IMA).

#### Step A: Find your knowledge bases

```bash
CLIENT_ID="${IMA_OPENAPI_CLIENTID}"
API_KEY="${IMA_OPENAPI_APIKEY}"
BASE="${IMA_BASE_URL:-https://ima.qq.com}"

curl -s -X POST "$BASE/openapi/wiki/v1/search_knowledge_base" \
  -H "ima-openapi-clientid: $CLIENT_ID" \
  -H "ima-openapi-apikey: $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"query":"文献","cursor":"","limit":10}'
```

#### Step B: Search contents of a knowledge base

```bash
KB_ID="<kb_id_from_step_a>"

curl -s -X POST "$BASE/openapi/wiki/v1/search_knowledge" \
  -H "ima-openapi-clientid: $CLIENT_ID" \
  -H "ima-openapi-apikey: $API_KEY" \
  -H "Content-Type: application/json" \
  -d "{\"query\":\"YOUR_KEYWORDS\",\"cursor\":\"\",\"knowledge_base_id\":\"$KB_ID\"}"
```

#### Step C: Search reading notes

```bash
curl -s -X POST "$BASE/openapi/note/v1/search_note" \
  -H "ima-openapi-clientid: $CLIENT_ID" \
  -H "ima-openapi-apikey: $API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"query_info":{"title":"KEYWORD","content":"KEYWORD"},"search_type":1,"sort_type":0,"start":0,"end":20}'
```

> **No IMA configured?** The workflow gracefully degrades — it searches public databases only and optionally falls back to flomo (via `short-mind` skill) for personal notes.

---

### Phase 3: Screening & Registration

> ⏱ Estimated time: 15-20 minutes

#### Quick Screening Matrix

For every paper found, quickly categorize:

| Paper | Relevant? | Priority | Why | Action |
|-------|-----------|----------|-----|--------|
| Paper A | ✅ Direct | ⭐⭐⭐ | Core method, must read | Deep read |
| Paper B | ✅ Indirect | ⭐⭐ | Method variant, compare | Quick skim |
| Paper C | ⚠️ Edge | ⭐ | Similar scenario, diff method | Abstract only |
| Paper D | ❌ No | — | Different problem | Skip |

Read abstracts quickly:

```bash
web_extract(urls=["https://arxiv.org/abs/2402.03300"])
```

#### Paper Registration

Temporarily register papers in a working doc:

```markdown
# Survey Working: <topic>

## 📥 To Read
- [ ] [Paper Title](arXiv:ID) | ⭐⭐⭐ | Why |

## 📖 Read
- [x] [Title] | Core finding | keywords | 2024-06-01

## ❌ Excluded
- [Title] | Reason for exclusion
```

---

### Phase 4: Deep Reading & Analysis

> ⏱ Estimated time: 30-60 minutes per paper

#### 4.1 Structured Reading Template

```markdown
## [Paper Title] (arXiv:XXXX.XXXXX)

**Basic Info**
- Authors | Year | Venue
- DOI / Link

**Problem**
- Research question
- Motivation / Why important?

**Method**
- Core idea (one sentence)
- Technical details
- Key difference from closest work

**Experiments & Results**
- Datasets / Setup
- Main metrics and results
- Ablation conclusions

**Limitations & Future Work**

**Significance for This Survey**
- Direct / Baseline / Background
- One line: What this paper means for my work
```

#### 4.2 Cross-Paper Analysis

After reading a few papers, stop and do **relationship analysis** — this is more important than reading more papers:

```markdown
## Field Structure

### Main Paradigms
1. Paradigm A (Papers 1, 2, 3)
   - Shared assumptions: ...
   - Conditions: ...
2. Paradigm B (Papers 4, 5)
   - Key differences from A: ...

### Comparison Dimensions
| Dimension | Paper 1 | Paper 2 | Paper 3 |
|-----------|---------|---------|---------|
| Core method | ... | ... | ... |
| Assumptions | ... | ... | ... |
| Performance | ... | ... | ... |

### Research Gaps (Unresolved Problems)
1. ...
2. ...
```

> 🔑 **Key insight:** When the same comparison dimension appears across 2+ different papers, you've found a structural tension in the field — this is the backbone of your survey.

---

### Phase 5: Synthesis Report

> ⏱ Estimated time: 30-60 minutes

Choose your output format:

#### 5.1 Survey Report (Scouting / Direction-Finding)

```markdown
# <Direction> Literature Survey Report

## 1. Scope
- Keywords | Time window | Databases

## 2. Field Overview
- Main research directions
- Core papers per direction (2-3 representative)
- Timeline / evolution

## 3. Key Method Comparison
- Comparison table (method / dataset / performance / scenario)

## 4. Unresolved Problems (Research Gaps)
- Gap 1: Evidence
- Gap 2: Evidence

## 5. Implications for This Project
- Directly adoptable methods
- Improvement opportunities
- Pitfalls to avoid

## 6. References
```

#### 5.2 Related Work Section (Paper-Ready)

```markdown
## Related Work

### <Sub-direction A>
[Work 1] did X. [Work 2] improved it by Y, but they share limitation Z.
**Our key difference**: ...

### <Sub-direction B>
...
```

#### 5.3 Archiving Notes

After the survey, append valuable notes to your long-term archive (e.g., IMA knowledge base or IDEA workspace `05-Literature/`).

---

## ⚡ Efficiency Tips

### Parallel Reading

Accelerate screening by fetching multiple abstracts at once:

```bash
web_extract(urls=[
    "https://arxiv.org/abs/2402.03300",
    "https://arxiv.org/abs/2401.12345",
    "https://arxiv.org/abs/2403.00001"
])
```

### Funnel Approach

```
Round 1: Search "survey" / "review" → get landscape (1-2 surveys)
Round 2: Follow citation chains from surveys
Round 3: Latest 1 year (cutoff chase)
Round 4: Verification search (no important direction missed)
```

### Time Budgeting

Prevent rabbit-holing with time boxes:

| Phase | Suggested Time |
|-------|---------------|
| Phase 0: Scope | 10-15 min |
| Phase 1: Public search | 20-30 min |
| Phase 2: Personal search | 5-10 min |
| Phase 3: Screening | 15-20 min |
| Phase 4: Deep reading | 30-60 min/paper |
| Phase 5: Synthesis | 30-60 min |

### IMA Search Tips

- **Vary expressions**: Try different terms (EN/CN, acronym/full name)
- **Search folders**: IMA folders (`media_type: 99`) may hold categorized collections
- **Search notes**: Your reading notes, thoughts, and comments are valuable
- **Cross-references**: If IMA has paper A and paper B, their intersection might be your niche
- **Pagination**: Use the `cursor` parameter for paginated IMA results

---

## 🏃 Quick Reference

| What You Need | Use This |
|--------------|----------|
| Search academic literature (professional) | Phase 1 → `paper-search search` (20+ sources) |
| Latest preprints | Phase 1 → `paper-search search --sources arxiv` |
| Paper impact / citation chain | Phase 1 → `paper-search search --sources semantic` or Semantic Scholar API |
| Surveys / blogs / tutorials | Phase 1 → AnySearch |
| Chinese-language resources | Phase 1 → AnySearch `"综述 研究进展"` |
| Papers you already saved | Phase 2 → IMA search |
| Download PDF | Phase 1 → `paper-search download` |
| Quick relevance check | Phase 3 → Read abstract |
| Take paper notes | Phase 4 → Structured reading template |
| Write Related Work | Phase 5 → Related Work format |
| Write survey report | Phase 5 → Survey report template |

---

## ⚠️ Limitations

1. **arXiv coverage**: Papers on arXiv are not peer-reviewed. Always check Semantic Scholar for final published versions.
2. **IMA completeness**: IMA only contains papers you **actively collected** — completeness depends on your daily accumulation.
3. **API rate limits**: Public APIs have rate limits (e.g., arXiv: 1 req/3s, Semantic Scholar: 1 req/s) — search may be slow with many queries.
4. **Not a replacement for systematic reviews**: For rigorous systematic literature reviews (e.g., PRISMA standard), this workflow's coverage may be insufficient. Supplement with Web of Science or Scopus.

---

## 🔗 Related Projects

- [research-ideation](https://github.com/zhonxia/research-ideation) — Research idea generation and evaluation (complementary workflow; use after literature survey)
- [paper-search-mcp](https://github.com/openags/paper-search-mcp) — Multi-source academic paper search CLI
- [AnySearch](https://github.com/anysearch-ai/anysearch-skill) — General web search skill for Hermes

---

## 📄 License

[MIT](./LICENSE)

---

<p align="center">
  <sub>Built with ❤️ by <a href="https://github.com/zhonxia">zhonxia</a></sub>
  <br>
  <sub>Have questions? <a href="https://github.com/zhonxia/personal-literature-survey/issues">Open an issue</a></sub>
</p>

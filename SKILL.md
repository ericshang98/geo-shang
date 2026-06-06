---
name: geo-shang
description: Use when optimizing a website for AI search engines (GEO) and traditional search engines (SEO). Starts by checking for a positioning document (geo-shang.html), then audits, researches keywords, optimizes, and records changes. Triggers on "geo", "seo", "geo-shang", "AI search optimization", "why can't AI find my site", or any request to improve search visibility. Consumes significant resources — deep research, parallel subagents, exhaustive analysis.
---

# GEO Shang — Generative Engine Optimization

与用户对话使用中文。geo-shang.html 定位文档使用中文（给用户审阅的）。面向外部的内容（llms.txt、meta 标签、页面正文、JSON-LD 等搜索引擎和用户看到的）使用英文。

## 文档结构：两区制（CRITICAL）

`geo-shang.html` 里有两种生命周期完全不同的内容，**必须用一条醒目的护栏分隔，绝不混排**：

- **✅ 创始人确认区（顶部）** — 定位内容：核心身份、核心信息、价值主张、功能排序、创始人身份标签、目标搜索词、Tone。**一经创始人确认，即为对外营销的唯一真源，长期稳定，可直接照做。** 写这区时假设"读者要拿去做内容营销"。
- **⚠️ 审计区（底部）** — 当前状态诊断：虚假声明必删表、7 维优先级工单表、可见度快照、归因表。**这是一份活的工单看板，不是一次性报告**——它实时反映"此刻网站与确认定位之间的差距"。每次运行、每轮优化都要就地更新：修掉的删、状态变的改、新发现/新页面/新文案重新过一遍。它不是营销内容，是给"来修 bug 的 agent"看的；对应问题修完即从本区销账。详见 A.3。

两区之间放一条视觉护栏（如 `<hr>` + 醒目标题 + 一句说明）。审计区每个标题必须自带"临时 / 非营销 / 修完即删"的字样，让任何人扫一眼就知道这不是确认的定位内容。

判断归属：**"创始人确认即真理、可直接做营销"的进确认区；"当前现状有问题、待修、改完作废"的进审计区。** 拿不准时问自己：这条修好之后还留着吗？留着 → 确认区；删掉 → 审计区。

## First Step: Check for Positioning Document

Everything depends on `geo-shang.html`. Start by checking if it exists:

```
Glob: **/geo-shang.html
Glob: **/geo-shang.md
```

- **Not found** → go to "When No Document Exists" below (full research + draft)
- **Found** → read it (including Change History), understand what changed and what's been done before, then decide your own scope and depth based on the content and history

---

## When No Document Exists

Tell the user: "没有找到定位文档，我先调研你的项目，然后起草一份给你审阅。"

### A.1 Project Research

Do all research yourself — don't ask the user questions one by one.

**Read everything in the project:**
- README.md, CLAUDE.md, package.json
- Website pages — homepage, about, pricing, features, blog, news
- llms.txt if it exists
- GitHub description / repo metadata

**Search externally (10-15+ searches):**
- Brand name — what does the internet say?
- Competitor products — how do they position themselves?
- Category queries — what language do customers use?
- AI engine results — what does Perplexity/ChatGPT say about this product?

**Analyze competitors (fetch 3+ competitor pages):**
- What content structure do they use?
- What claims do they make?
- Do they have llms.txt? What schema?
- What are they doing that this project isn't?

### A.2 Draft geo-shang.html

Write `geo-shang.html` in the project root. HTML format so the user can open in browser and edit directly. Each section uses `contenteditable="true"`。

文档按"两区制"组织（见上文）。本节起草的是 **✅ 创始人确认区** 的所有定位 section；审计区在 A.3 才生成，放在护栏下方。

**创始人确认区 — Required sections：**

| Section | Content |
|---|---|
| Core Identity | 一段话：这是什么、给谁用、做什么 |
| Key Message | 最重要的一句话。AI 只引用一句的话，就是这句 |
| Differentiation | 跟竞品有什么不同。具体的、事实的 |
| Value Proposition | 解决什么问题。用之前 vs 用之后 |
| Features to Highlight | 按用户重要性排序，不按技术复杂度 |
| Features to De-emphasize | 存在但不应该成为重点的功能 |
| Pricing | 具体数字 |
| Founder / Team | 背景、资历、为什么做这个。**只写创始人确认属实的，绝不编造资历/头衔/经历** |
| Target Queries | 5-10 个用户真实会搜的词 |
| Tone & Voice | 描述的风格 |
| Change History | 空的，后续每次运行追加 |

确认区结尾放一条护栏（`<hr>` + 标题如「⚠️ 以下为审计区 — 当前状态问题，临时，修完即删，非营销内容」），A.3 的审计产物全部落在护栏下方。

**Present to user:**
1. 在终端里把每个 section 内容复述给用户看
2. 给出文件的完整绝对路径，让用户可以直接点击或复制打开（例如 `file:///Users/xxx/project/geo-shang.html`），也可以用 `open` 命令帮用户在浏览器中打开
3. 等用户确认后继续

### A.3 Full Audit + Diagnosis（穷尽式）

文档确认后，做一次**穷尽式审计**——不是抽查几项，而是逐维度逐页跑完下面 7 个面，每一条都给出"现状 → 差距 → 行动"。**所有审计产物（虚假声明必删表、各维度发现、优先级表、归因表）一律写进 geo-shang.html 护栏下方的「⚠️ 审计区」，绝不混进确认区。**

> **审计区是活的，不是一次性快照。** 它反映的是"此刻网站与确认定位之间的真实差距"。每次跑 `/geo-shang`、每做完一轮优化，都要**重新核对并就地更新这张审计**：修掉的删、状态变的改、新发现的加、新建的页面/新写的文案重新过一遍可引用性。把它当成一份持续维护的 GEO 工单看板，而不是写完就不动的报告。审计区永远要能回答："如果现在有人问'网站还差什么才能被 AI 引用'，看这里就够了。"

并行铺开，能用 subagent 就并行跑：

**① 抓取与可访问性（Crawlability）— AI 爬虫能不能拿到内容**
- robots.txt：逐个 AI 爬虫 UA 核对放行情况——`GPTBot`、`OAI-SearchBot`、`ClaudeBot`、`anthropic-ai`、`PerplexityBot`、`Google-Extended`、`CCBot`、`Bytespider`、`Amazonbot`、`Applebot-Extended`。哪个被 Disallow 写明
- Cloudflare / CDN / WAF：是否开了 "Block AI Bots" 开关、是否有 Bot Fight Mode 误伤、是否对爬虫返 403/验证码
- 渲染方式：SSR/SSG vs CSR。**多数 AI 爬虫（GPTBot、ClaudeBot、PerplexityBot）不执行 JavaScript** → CSR-only 的内容对它们等于不存在。逐页判断关键内容是否在首字节 HTML 里
- HTTP 层：状态码、重定向链（有没有多跳/链路坏）、canonical 是否自指且正确、http→https、www 归一
- 速度 / Core Web Vitals（LCP/CLS/INP）— 影响 Google 排名与抓取预算

**② AI 入口文件 — 专门喂给 LLM 的**
- `llms.txt` / `llms-full.txt`：是否存在、是否对齐确认定位、是否覆盖核心页面与一句话定位、链接是否有效
- `sitemap.xml`：是否覆盖所有页面、`lastmod` 是否新鲜（3 个月断崖）、是否在 robots 里声明、是否提交搜索引擎
- favicon / OG 图 / 品牌图等机器可读资产是否齐全

**③ 结构化数据（Schema / JSON-LD）— 被引用概率 ×2.5**
- 逐页核对该有的 schema：`Organization`、`Product`/`Offer`、`Person`（创始人）、`Article`/`BlogPosting`、`FAQPage`、`BreadcrumbList`、`AggregateRating`
- 每个字段是否齐全、是否**对齐确认定位的事实**（价格、名字、状态不能和确认区打架）
- 是否能通过 Schema 校验（无语法/类型错误）

**④ Meta / 页面头（逐页）**
- 每页：`title`（长度 ≤60、含关键词+品牌、唯一不重复）、`description`（120-160、含目标词、有召唤）、`canonical`、`lang`、`viewport`
- OG（`og:title/description/image/url/type`）+ Twitter Card 是否齐全、预览是否好看
- 多语言站：`hreflang` 是否成对正确

**⑤ 内容质量与可引用性（GEO 核心，对照 Research Foundation 的硬指标）**
- **前 100 字直答**：90% 高引用页在前 100 字就给出直接答案——逐页检查 hero/首段是否直接回答"这是什么、给谁、解决什么"
- **前 30% 放关键事实**：44.2% 的 AI 引用来自页面前 30%——最关键的事实/数字有没有沉到底部
- **可引用三杀**（Princeton：Quotation +41%、Statistics +33%、Cite Sources +30%）：有没有具体数字、引用、可信来源；标语越多越不被引
- **段落长度**：>300 字注意力降 31%——揪出超长段
- **列表/表格占比**：25-35% 最佳，比纯文字提取准确率高 43%
- **标题层级**：3-5 层，H1 唯一，逻辑递进
- **单主题聚焦**：Perplexity 偏好单主题页，一页塞太多主题信号分散
- **新鲜度**：每页最后更新时间，3 个月没动的标出来
- **内部链接密度**：孤岛页、锚文本是否含义化
- **与确认定位对齐**：逐页比对——该强调的（确认区"要突出"）强调了吗？该弱化的（"要弱化"）真弱化了吗？**有没有与硬件/事实矛盾的虚假声明**（这是审计区第一张"必删表"的来源）？口径有没有和确认区冲突？

**⑥ 真实搜索表现（≥10 次实搜 + AI 实测）**
- 品牌词（3+）：搜得到吗？排第几？**有没有同名污染**（如撞了别的产品/品牌）
- 品类词（5+，从确认区 Target Queries 出发）：进没进结果、谁占了位
- 竞品对比词：竞品怎么被描述、我方缺位在哪
- **AI 引擎实测**：Perplexity / ChatGPT / Google AI Overview / Gemini 实际问一遍——会不会提到本品牌、提了什么、准不准、引用了哪些源
- SERP 特性：featured snippet / People Also Ask / knowledge panel 有没有机会

**⑦ 站外权威与跨平台共识（AI 要多源一致才敢引用）**
- 第三方评测、"best X 2026"榜单：有没有覆盖
- Product Hunt / Reddit / HackerNews / **YouTube（与 AI 可见度相关性 0.737，最高）**
- G2 / Trustpilot 等评价平台（被引用概率 ×3）
- 维基百科 / 知识图谱 / 权威目录是否收录
- 跨平台信息一致性：各处对品牌的描述是否和确认定位一致（不一致 = AI 不敢引）
- 反向链接 / 域名权威概况

**审计区落盘格式** — 至少包含：
1. **🔴 虚假声明必删表**（与已验证事实矛盾的对外声明，最高优先级）：`声称 | 真实情况 | 位置`
2. **优先级工单表**（覆盖以上 7 维的所有发现）：

```
| # | 问题 | 维度① 抓取 / ② 入口 / ③ Schema / ④ Meta / ⑤ 内容 / ⑥ 搜索 / ⑦ 权威 | 层级（技术>内容>权威） | 影响 | 成本 | 状态（待办/进行/已修） | 行动 |
|---|------|------|------|------|------|------|------|
```

3. **当前可见度快照**（⑥⑦ 的实搜结果）：`渠道 | 有无 | 说明`

**修复顺序：技术 > 内容 > 权威。** 先把爬虫拿不到内容、Schema 缺失这类技术硬伤修掉，再修内容可引用性，权威层（站外覆盖）多为给用户的建议。

### A.4 Keyword Research

从定位文档的 Target Queries 出发：

- 用 WebSearch 验证每个目标词的搜索结果和竞争程度
- 分析哪些词有机会排上去、哪些竞争太激烈
- 发现新的长尾词机会
- 如果用户配了 Ahrefs/SEMrush/Google Trends 的 MCP 或 API，调用获取搜索量和竞争度数据；没有就跳过
- 输出推荐关键词列表，按优先级排序，回写到定位文档的 Target Queries 区域

### A.5 Attribution Map + Optimization

**先建归因表** — 搜索引擎看到的每条信息追溯到哪个源文件：

```
| 搜索引擎看到的 | 来自哪个文件 | 怎么产生的 |
|----------------|-------------|-----------|
```

按搜索面展开归因链：
- Google 搜索结果 ← title/description ← page.tsx metadata
- AI 搜索引用 ← llms.txt（主）← SSR 页面正文（次）← JSON-LD
- 社交分享预览 ← OG tags ← metadata.openGraph

**然后系统性优化** — agent 盘点自己能做的所有事：

| 能力 | 具体操作 |
|------|---------|
| 改 sitemap.xml | 补全所有页面、更新日期 |
| 改 robots.txt | 确保 AI 爬虫放行 |
| 改/重写 llms.txt | 对齐定位文档 |
| 改 JSON-LD | 对齐定位文档的事实 |
| 改 meta 标签 | 每个页面的 title/description/OG |
| 改页面内容 | Hero 文案、功能描述、FAQ 答案 |
| 创建新页面 | 对比文章、缺失的 landing page |
| 改内容结构 | 标题层级、段落长度、列表比例 |

不能直接做但给建议的：
- 社交媒体发布（YouTube、Reddit、Product Hunt）
- 第三方评测覆盖
- 跨平台消息一致性

**用多个 subagent 交叉验证优化方案** — 一个 agent 提方案，另一个 agent 挑战，确保改动经得起推敲。

按优先级执行所有改动，能改的直接改，需要用户确认的先展示方案。

### A.6 Verify + Record

**验证：**
- 重新读改过的文件，确认内容跟定位文档一致
- 重新搜索品牌词，看即时变化
- 检查 JSON-LD、sitemap 结构完整性

**清理审计区：**
本次修掉的问题，从护栏下方的「⚠️ 审计区」里删掉对应条目（修完即销账，别让审计表越积越长）。确认区不动——那是营销真源，只有创始人改定位时才动。

**记录变更到 geo-shang.html：**
在确认区的 Change History 区域追加（Change History 属于确认区，记录定位/优化的演进；与审计区的"待修问题"分开）：

```
[日期] — [本次运行摘要]
- 改了什么：[文件列表]
- 为什么改：[对应的问题]
- 关键词变化：[新增/调整的目标词]
- 待解决：[需要用户手动做的事]
```

**Commit 代码：**
commit message 写清楚 GEO 变更内容。

---

## When Document Exists

读完 geo-shang.html（**确认区 + 审计区 + Change History** 都要读）后，根据内容和历史自行判断该做什么、做多深。不需要固定模式 — 你了解上下文后自然知道哪些需要重新审视、哪些已经做过了。

**每次运行必做：刷新审计区。** 审计区是活的（见 A.3）——别把上次的审计当现状。这次进来要重新核对：上次列的问题修了吗（修了就删）？做过的优化有没有引入新问题？有没有新页面/新文案要过一遍 7 维？品牌词/AI 引擎实搜结果变了吗？把审计区更新成"此刻的真实差距"，再据此决定这轮优化什么。

**Change History 管理：**
- 每次运行在 Change History 追加本次记录
- 已解决的旧条目压缩成一行摘要，只保留最近 3-5 次的详细记录
- 目标是历史不丢失但不膨胀 — 类似 git squash

这样无论什么时候开新 session 跑 `/geo-shang`，agent 读 html 就能看到完整的 GEO 历史，知道之前做了什么、还有什么没做。

---

## Research Foundation

以下研究数据支撑审计和优化中的具体判断标准：

**Princeton GEO Paper (KDD 2024):**
- 9 种优化方法中最有效的三种：Quotation Addition (+41%), Statistics Addition (+33%), Cite Sources (+30%)
- Keyword Stuffing 在 AI 搜索中几乎无效
- 多种方法组合使用额外提升 5.5%

**Structural Citation Research (2026):**
- 内容结构贡献 44.9%（宏观）+ 39.7%（中观）+ 15.4%（微观）
- 段落超过 300 字注意力下降 31%
- 列表/表格比纯文字提取准确率高 43%
- 44.2% 的 AI 引用来自页面前 30% 的内容
- 90% 的高引用页面在前 100 字内给出直接答案

**Perplexity Source Selection:**
- 5 步流水线：Query Interpretation → Retrieval → Answer Construction → Citation Assignment → Trust Filtering
- 引用准确率 39-77%，深度越深准确率越低
- 偏好单主题聚焦页面，多主题页面信号分散

**Platform Data (2026):**
- YouTube 提及与 AI 可见度相关性 0.737（最高）
- 有 Schema markup 的内容被引用概率高 2.5 倍
- AI 推荐的访客转化率 14.2% vs Google organic 2.8%
- 内容 3 个月未更新引用率断崖下跌
- G2/Trustpilot 等平台让品牌被引用概率提升 3 倍

**Key Principles:**
1. 定位文档是一切的基础 — 没有用户认可的定位，不动任何代码
2. 可引用 > 花哨 — AI 引用事实，不引用标语
3. 具体 > 模糊 — "$129 clip-on, 3 秒派发" 会被引用，"affordable AI wearable" 不会
4. 结构占 44.9% — 标题层级、段落长度、列表比例直接影响引用率
5. 新鲜度是硬指标 — 3 个月是断崖，每次运行更新时间戳
6. 多平台共识 — AI 需要在多个独立来源看到一致的品牌信息才会引用
7. 前 30% 最重要 — 把最关键的事实放在页面最前面

---

## Source References

- [GEO: Generative Engine Optimization](https://arxiv.org/abs/2311.09735) — Princeton, KDD 2024
- [Structural Feature Engineering for GEO](https://arxiv.org/html/2603.29979) — 2026
- [Perplexity Source Selection](https://authoritytech.io/blog/how-perplexity-selects-sources-algorithm-2026)
- [LLMrefs GEO Guide](https://llmrefs.com/generative-engine-optimization)
- [Sapt.ai AI Search Guide](https://sapt.ai/insights/ai-search-optimization-complete-guide-chatgpt-perplexity-citations)
- [llms.txt Specification](https://searchengineland.com/llms-txt-proposed-standard-453676)

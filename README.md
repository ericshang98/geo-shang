<div align="center">

# 🔎 GEO Shang

### Generative Engine Optimization — get your site **cited by AI**, not just ranked by Google

<br>

[![License: MIT](https://img.shields.io/badge/License-MIT-2563eb.svg?style=flat-square)](./LICENSE)
[![Skill](https://img.shields.io/badge/type-agent%20skill-dc2626?style=flat-square)](./SKILL.md)
[![Made for Claude Code](https://img.shields.io/badge/made%20for-Claude%20Code-8b5cf6?style=flat-square)](https://claude.com/claude-code)
[![PRs welcome](https://img.shields.io/badge/PRs-welcome-16a34a?style=flat-square)](https://github.com/ericshang98/geo-shang/pulls)

<br>

> **Traditional SEO optimizes for _humans clicking a link_.**
> **GEO optimizes for _models quoting you_.**
> The audience changed — so the method changes with it.

</div>

<br>

```
定位锁真相  →  两区分死活  →  为 AI 入口铺事实  →  可引用且诚实  →  技术内容权威按序攻坚  →  多源共识封口
```

> **一句话内核：** 先让创始人锁定「我是谁、想被怎么引用」，再把这个唯一真相，**诚实、可引用地**，铺满 AI 引擎能读到的每一个入口。

<br>

## 🆚 SEO vs. GEO

| | Traditional SEO | **GEO Shang** |
|---|---|---|
| **Audience** | A human scanning a results page | An LLM constructing an answer |
| **Goal** | Rank #1, win the click | Be the source the model **quotes** |
| **Wins on** | Backlinks, keywords, page speed | Citable facts, `llms.txt`, JSON-LD, multi-source consensus |
| **Fatal flaw it kills** | Thin content | **Split narrative** (homepage ≠ schema ≠ `llms.txt`) |
| **Unit of success** | A ranking | A citation |

<br>

## 🧭 Core idea / 核心思想

Five pillars hold the whole method up.

<table>
<tr>
<td width="40"><h3>1️⃣</h3></td>
<td>
<b>Positioning first — founder-confirmed is the single source of truth.</b><br>
No code changes until there's a positioning document the founder approved. Every line of copy, schema, and <code>llms.txt</code> aligns to it. This kills the most common disease: a <b>split narrative</b> — homepage says A, JSON-LD says B, <code>llms.txt</code> says C → the AI ingests three contradictory stories and cites none.
</td>
</tr>
<tr>
<td><h3>2️⃣</h3></td>
<td>
<b>Two zones — marketing source-of-truth vs. a living worklog.</b><br>
One document, two lifecycles, one hard divider:<br>
&nbsp;&nbsp;✅ <b>Confirmed zone</b> — the stable marketing single-source-of-truth; approved = use it directly.<br>
&nbsp;&nbsp;⚠️ <b>Audit zone</b> — a temporary, continuously-updated GEO worklog of "what the site still lacks vs. positioning"; items are deleted as fixed.<br>
Marketing content and open bugs <b>never mix</b>.
</td>
</tr>
<tr>
<td><h3>3️⃣</h3></td>
<td>
<b>Build for how AI <i>reads</i>, not just how Google <i>ranks</i>.</b><br>
Weight lands where AI actually ingests: can the crawler even get the content (<b>most AI crawlers don't run JavaScript</b> — CSR content is invisible), the LLM-facing <code>llms.txt</code>, and structured <code>JSON-LD</code>. What the AI really reads is the <b>server-rendered schema</b>, not the homepage copy you think it reads — so fixes hit the <i>source</i> of the attribution chain.
</td>
</tr>
<tr>
<td><h3>4️⃣</h3></td>
<td>
<b>Citable &gt; flashy. Concrete &gt; vague. Facts &gt; slogans. Honesty is a hard constraint.</b><br>
AI quotes facts, not taglines. "$129, clip on, dispatch in 3 seconds" gets cited; "affordable AI wearable" doesn't. Answer in the first 100 words; use real numbers, quotes, sources.<br>
And honesty is <b>both ethics and strategy</b>: AI cross-checks sources, so false claims collapse — so <b>never fabricate</b>, and the <b>same truth-bar applies to what you WRITE as to what you DELETE</b> (don't scrub an old false claim only to write a new aspirational one).
</td>
</tr>
<tr>
<td><h3>5️⃣</h3></td>
<td>
<b>Fix in order; authority is won by consensus → Technical &gt; Content &gt; Authority.</b><br>
First make the crawler get the right content (robots / render / sitemap / schema), then make content citable, then the authority layer — <b>AI only cites you once it sees a consistent story across multiple independent sources</b>. Off-site consensus (reviews, YouTube, Product Hunt, Wikipedia) is the real moat, and usually the ceiling you can't reach by editing your own site alone.
</td>
</tr>
</table>

Two principles run throughout: **exhaustive + parallel** (all 7 dimensions, page-by-page, fanned out across subagents) and **living + recurring** (freshness is a hard metric — a cliff at ~3 months; the audit zone refreshes every run).

<br>

## 🔬 The 7-dimension audit

Every run is an exhaustive sweep — each finding written as **`current → gap → action`**.

| # | Dimension | What it checks |
|:-:|---|---|
| ① | **Crawlability** | per-UA `robots.txt` for AI crawlers · Cloudflare/WAF blocks · SSR vs CSR (AI crawlers don't run JS) · redirects/canonical · Core Web Vitals |
| ② | **AI entry files** | `llms.txt` / `llms-full.txt` · `sitemap.xml` coverage & freshness |
| ③ | **Structured data** | Organization / Product / Person / FAQPage / Article / Breadcrumb / AggregateRating — fields must match the confirmed positioning |
| ④ | **Meta** | per-page title · description · canonical · OG · Twitter · hreflang |
| ⑤ | **Content citability** | first-100-words answer · top-30% facts · Quotation/Statistics/Cite-Sources · paragraph length · list ratio · heading hierarchy · **false-claim detection** |
| ⑥ | **Live search** | brand terms (+ name-collision pollution) · category terms · competitor comparisons · real AI-engine citation tests |
| ⑦ | **Off-site authority** | reviews · listicles · Product Hunt / Reddit / HN / **YouTube** · G2 / Trustpilot · Wikipedia / knowledge graph · cross-platform consistency |

<br>

## 📊 Research foundation

The thresholds aren't vibes — they're grounded in published research.

| Source | Key finding |
|---|---|
| **Princeton GEO** (KDD 2024) | Most effective: Quotation **+41%**, Statistics **+33%**, Cite Sources **+30%**. Keyword stuffing ≈ useless for AI search. |
| **Structural citation research** (2026) | Content structure ≈ **45%** of the signal · **44.2%** of citations come from the top 30% of a page · **90%** of high-citation pages answer in the first 100 words · lists/tables extract **43%** more accurately than prose. |
| **Platform data** (2026) | Schema → **2.5×** citation odds · YouTube ↔ AI-visibility correlation **0.737** (highest) · G2/Trustpilot → **3×** odds · 3 months stale = citation cliff. |

<sub>Full references in <a href="./SKILL.md"><code>SKILL.md</code></a>.</sub>

<br>

## 🚀 Install

A single-file agent skill (`SKILL.md`). Drop it where your agent looks for skills.

```bash
# Claude Code (and compatible agents)
git clone https://github.com/ericshang98/geo-shang.git ~/.claude/skills/geo-shang

# …or via a skill manager
npx skills add github:ericshang98/geo-shang
```

Then invoke it:

```
/geo-shang
```

- **First run** (no positioning doc found) → it researches your project and drafts a `geo-shang.html` for you to review and confirm.
- **Later runs** → it reads the doc, refreshes the audit zone, and optimizes — **technical first**.

<br>

## 🔒 Privacy

> The positioning document this skill produces (`geo-shang.html` / `geo-shang-cn.html`) is **your private, per-project content** — confirmed positioning **plus an internal audit zone** (a "false claims to delete" table, founder facts, GEO strategy).
>
> It belongs in *your* project, **never** in this skill repo. The bundled [`.gitignore`](./.gitignore) excludes `geo-shang*.html` / `geo-shang*.md` as a safeguard. Keep those docs out of any repo that could go public.

<br>

---

<div align="center">

**MIT** © 2026 Eric Shang（尚奕勇） · built with [Claude Code](https://claude.com/claude-code)

<sub>If GEO Shang helps your site get cited, a ⭐ is appreciated.</sub>

</div>

<a name="readme-top"></a>

<div align="center">

<h1>GEO Shang</h1>

<p>
  <b>Generative Engine Optimization</b><br>
  Get your site <b>cited by AI</b> — not just ranked by Google.
</p>

[![MIT License][license-shield]][license-url]
[![Agent Skill][skill-shield]][skill-url]
[![Claude Code][claude-shield]][claude-url]
[![PRs Welcome][prs-shield]][prs-url]

<p>
  <a href="./SKILL.md"><b>Explore the skill »</b></a>
  &nbsp;·&nbsp;
  <a href="https://github.com/ericshang98/geo-shang/issues">Report Bug</a>
  &nbsp;·&nbsp;
  <a href="https://github.com/ericshang98/geo-shang/issues">Request Feature</a>
</p>

<br>

<i>Traditional SEO optimizes for humans clicking a link.<br>
GEO optimizes for models quoting you.<br>
The audience changed — so the method changes with it.</i>

</div>

<br>

<!-- TABLE OF CONTENTS -->
<details>
  <summary><b>Table of Contents</b></summary>
  <ol>
    <li><a href="#about">About</a></li>
    <li><a href="#seo-vs-geo">SEO vs. GEO</a></li>
    <li><a href="#core-idea--核心思想">Core idea / 核心思想</a></li>
    <li><a href="#the-7-dimension-audit">The 7-dimension audit</a></li>
    <li><a href="#measuring-citations-cloudflare--sql">Measuring citations (Cloudflare → SQL)</a></li>
    <li><a href="#research-foundation">Research foundation</a></li>
    <li><a href="#getting-started">Getting started</a></li>
    <li><a href="#usage">Usage</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
    <li><a href="#privacy">Privacy</a></li>
    <li><a href="#license">License</a></li>
  </ol>
</details>

<br>

<!-- ABOUT -->
## About

**GEO Shang** is a single-file [agent skill](./SKILL.md) for **Claude Code** that optimizes a website to be **cited by AI search engines** — Perplexity, ChatGPT, Google AI Overview, Gemini.

It doesn't chase keywords. It starts from a founder-confirmed **positioning document**, runs an exhaustive **8-dimension audit**, fixes the site in the right order (technical → content → authority), and closes the loop by **measuring whether AI actually cites you**.

> **一句话内核：** 先让创始人锁定「我是谁、想被怎么引用」，再把这个唯一真相，**诚实、可引用地**，铺满 AI 引擎能读到的每一个入口。

```
定位锁真相 → 两区分死活 → 为 AI 入口铺事实 → 可引用且诚实 → 技术内容权威按序攻坚 → 多源共识封口
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- SEO VS GEO -->
## SEO vs. GEO

|  | Traditional SEO | **GEO Shang** |
| --- | --- | --- |
| **Audience** | A human scanning a results page | An LLM constructing an answer |
| **Goal** | Rank #1, win the click | Be the source the model **quotes** |
| **Wins on** | Backlinks, keywords, page speed | Citable facts, `llms.txt`, JSON-LD, multi-source consensus |
| **Kills** | Thin content | **Split narrative** (homepage ≠ schema ≠ `llms.txt`) |
| **Unit of success** | A ranking | A **citation** |

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- CORE IDEA -->
## Core idea / 核心思想

Five pillars hold the whole method up.

**1 · Positioning first — founder-confirmed is the single source of truth.**
No code changes until there's a positioning document the founder approved. Every line of copy, schema, and `llms.txt` aligns to it. This kills the most common disease — a **split narrative**: homepage says A, JSON-LD says B, `llms.txt` says C, and the AI cites none of them.

**2 · Two zones — marketing truth vs. a living worklog.**
One document, two lifecycles, one hard divider. The **confirmed zone** is the stable marketing single-source-of-truth; the **audit zone** is a temporary, continuously-updated GEO worklog of what the site still lacks. Marketing content and open bugs never mix.

**3 · Build for how AI _reads_, not just how Google _ranks_.**
Most AI crawlers don't run JavaScript, so CSR content is invisible to them. What the AI actually reads is the **server-rendered schema and `llms.txt`** — not the homepage copy you think it reads. So fixes hit the *source* of the attribution chain.

**4 · Citable > flashy. Concrete > vague. Facts > slogans. Honesty is a hard constraint.**
AI quotes facts, not taglines. "$129, clip on, dispatch in 3 seconds" gets cited; "affordable AI wearable" doesn't. And the **same truth-bar applies to what you write as to what you delete** — never scrub an old false claim only to write a new aspirational one.

**5 · Fix in order; authority is won by consensus → Technical > Content > Authority.**
First make the crawler get the right content, then make it citable, then build off-site consensus — because **AI only cites you once it sees a consistent story across multiple independent sources**. That consensus (reviews, YouTube, Product Hunt, Wikipedia) is the real moat.

<sub>Two principles run throughout: **exhaustive + parallel** (all dimensions, page-by-page, fanned across subagents) and **living + recurring** (freshness is a hard metric — a cliff at ~3 months).</sub>

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- AUDIT -->
## The 7-dimension audit

Every run is an exhaustive sweep — each finding written as **`current → gap → action`**.

| # | Dimension | Checks |
| :-: | --- | --- |
| ① | **Crawlability** | per-UA `robots.txt` · Cloudflare/WAF blocks · SSR vs CSR · redirects/canonical · Core Web Vitals |
| ② | **AI entry files** | `llms.txt` / `llms-full.txt` · `sitemap.xml` coverage & freshness |
| ③ | **Structured data** | Organization / Product / Person / FAQPage / Article / Breadcrumb — fields must match positioning |
| ④ | **Meta** | per-page title · description · canonical · OG · Twitter · hreflang |
| ⑤ | **Content citability** | first-100-words answer · top-30% facts · Quotation/Statistics/Cite-Sources · structure · **false-claim detection** |
| ⑥ | **Live search** | brand terms (+ name collision) · category terms · competitor comparisons · real AI-engine citation tests |
| ⑦ | **Off-site authority** | reviews · Product Hunt / Reddit / HN / **YouTube** · G2 / Trustpilot · Wikipedia · cross-platform consistency |
| ⑧ | **Observability** | is an AI-crawler logging layer + canary tokens in place? (see below) |

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- OBSERVABILITY -->
## Measuring citations (Cloudflare → SQL)

GEO's hardest question: *after optimizing, are we actually being cited?* If the site is on **Cloudflare**, the whole loop can live in **SQL**.

- **Crawl logging** — a Pages `functions/_middleware.ts` detects AI-bot user-agents and writes each hit into **D1 (SQLite)**. Classify the UA: `training` (GPTBot, ClaudeBot, PerplexityBot…) vs **`realtime`** (OAI-SearchBot, ChatGPT-User, Perplexity-User…) — a realtime hit means **you're being used as a citation source right now**.
- **Canary tokens** — embed a unique fingerprint per key page (in `llms.txt`, SSR body, JSON-LD). Ask Perplexity/ChatGPT your brand term and watch for the canary in the answer — proof of *which page* got cited. Probe results go into SQL too.
- **Dashboard = a few SQL queries** — "which bot read which page", "which pages are realtime-cited", "which pages AI has never crawled".

> The skill ships the D1 schema, the `_middleware.ts` skeleton, and the dashboard queries. See [`SKILL.md`](./SKILL.md).

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- RESEARCH -->
## Research foundation

The thresholds aren't vibes — they're grounded in published research.

| Source | Key finding |
| --- | --- |
| **Princeton GEO** (KDD 2024) | Quotation **+41%**, Statistics **+33%**, Cite Sources **+30%**. Keyword stuffing ≈ useless. |
| **Structural citation research** (2026) | Structure ≈ **45%** of the signal · **44.2%** of citations from the top 30% · **90%** answer in the first 100 words · lists/tables **+43%** extraction accuracy. |
| **Platform data** (2026) | Schema → **2.5×** citation odds · YouTube ↔ AI-visibility correlation **0.737** · G2/Trustpilot → **3×** · 3 months stale = citation cliff. |

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- GETTING STARTED -->
## Getting started

A single-file skill (`SKILL.md`). Drop it where your agent looks for skills.

```bash
# Claude Code (and compatible agents)
git clone https://github.com/ericshang98/geo-shang.git ~/.claude/skills/geo-shang

# …or via a skill manager
npx skills add github:ericshang98/geo-shang
```

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- USAGE -->
## Usage

```
/geo-shang
```

- **First run** (no positioning doc) → it researches your project and drafts a `geo-shang.html` for you to review and confirm.
- **Later runs** → it reads the doc, refreshes the audit zone, and optimizes — technical first.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- ROADMAP -->
## Roadmap

- [x] Two-zone positioning document model
- [x] Exhaustive 8-dimension audit
- [x] Research-grounded citability thresholds
- [x] Cloudflare → D1 citation observability + canary tokens
- [ ] Reusable `_middleware.ts` + D1 starter kit as a drop-in template
- [ ] Optional integrations for keyword-volume APIs (Ahrefs / SEMrush)
- [ ] Non-Cloudflare observability recipes (Vercel / Netlify / nginx)

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- PRIVACY -->
## Privacy

> The positioning document this skill produces (`geo-shang.html` / `geo-shang-cn.html`) is **your private, per-project content** — confirmed positioning **plus an internal audit zone** (a "false claims to delete" table, founder facts, GEO strategy).
>
> It belongs in *your* project, **never** in this repo. The bundled [`.gitignore`](./.gitignore) excludes `geo-shang*.html` / `geo-shang*.md` as a safeguard. Keep those docs out of any repo that could go public.

<p align="right">(<a href="#readme-top">back to top</a>)</p>

<!-- LICENSE -->
## License

Distributed under the MIT License. See [`LICENSE`](./LICENSE).

<br>

<div align="center">
<sub>© 2026 Eric Shang（尚奕勇） · built with <a href="https://claude.com/claude-code">Claude Code</a><br>
If GEO Shang helps your site get cited, a ⭐ is appreciated.</sub>
</div>

<!-- REFERENCE LINKS -->
[license-shield]: https://img.shields.io/badge/License-MIT-2563eb?style=for-the-badge
[license-url]: ./LICENSE
[skill-shield]: https://img.shields.io/badge/Type-Agent_Skill-dc2626?style=for-the-badge
[skill-url]: ./SKILL.md
[claude-shield]: https://img.shields.io/badge/Made_for-Claude_Code-8b5cf6?style=for-the-badge
[claude-url]: https://claude.com/claude-code
[prs-shield]: https://img.shields.io/badge/PRs-welcome-16a34a?style=for-the-badge
[prs-url]: https://github.com/ericshang98/geo-shang/pulls

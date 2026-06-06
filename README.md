# GEO Shang — Generative Engine Optimization

A Claude Code / agent **skill** for optimizing a website to be **cited by AI search engines** (Perplexity, ChatGPT, Google AI Overview, Gemini) — not just ranked by Google.

Traditional SEO optimizes for *humans clicking a link*. GEO optimizes for *models quoting you*. The audience changed, so the method changes with it.

> 一句话内核：**先让创始人锁定"我是谁、想被怎么引用"，再把这个唯一真相，诚实、可引用地，铺满 AI 引擎能读到的每一个入口。**

---

## Core idea / 核心思想

GEO Shang is built on five pillars:

1. **Positioning first; founder-confirmed is the single source of truth.**
   No code changes until there's a positioning document the founder has approved. Every line of copy, schema, and `llms.txt` aligns to it — instead of each drifting its own way. This kills the most common disease: **a split narrative** (homepage says A, JSON-LD says B, `llms.txt` says C → the AI ingests three contradictory stories and cites none).

2. **Two zones: marketing source-of-truth vs. a living worklog.**
   One document holds two things with completely different lifecycles, separated by a hard divider:
   - **✅ Confirmed zone** — the long-stable marketing single-source-of-truth; once approved, use it directly.
   - **⚠️ Audit zone** — a temporary, continuously-updated GEO worklog of "what the site is still missing vs. the positioning"; items are deleted as they're fixed.
   Marketing content and open bugs never mix.

3. **Build for how AI *reads*, not just how Google *ranks*.**
   Weight lands on the channels AI actually ingests: can the crawler even get the content (**most AI crawlers don't run JavaScript** — CSR content is invisible to them), the LLM-facing `llms.txt`, and structured `JSON-LD`. **What the AI actually reads is the server-rendered schema, not the homepage copy you think it reads** — so fixes hit the *source* of the attribution chain.

4. **Citable > flashy, concrete > vague, facts > slogans, and honesty is a hard constraint.**
   AI quotes facts, not taglines. "$129, clip on, dispatch in 3 seconds" gets cited; "affordable AI wearable" doesn't. Put the answer in the first 100 words; use concrete numbers, quotes, sources.
   And **honesty is both ethics and strategy**: AI cross-checks multiple sources, so false claims eventually collapse — therefore **never fabricate**, and **the same truth-bar applies to what you WRITE as to what you DELETE** (don't scrub an old false claim only to write a new aspirational one).

5. **Fix in order; authority is won by consensus. Technical > Content > Authority.**
   First make the crawler get the right content (robots / render mode / sitemap / schema), then make the content citable (structure / citability / alignment), then the authority layer — **AI only cites you once it sees a consistent story across multiple independent sources**, so off-site consensus (reviews, YouTube, Product Hunt, Wikipedia, ecosystem directories) is the real moat, and usually the ceiling you can't reach by editing your own site alone.

Two implicit principles run throughout:
- **Exhaustive + parallel** — the audit isn't spot-checking; it runs all 7 dimensions page-by-page, fanned out across subagents.
- **Living and recurring** — GEO is not a one-off. Freshness is a hard metric (a cliff at ~3 months); the audit zone is refreshed every run; positioning evolves with the product.

**口诀**：定位锁真相 → 两区分死活 → 为 AI 入口铺事实 → 可引用且诚实 → 技术内容权威按序攻坚 → 多源共识封口。

---

## The 7-dimension audit

Every run does an exhaustive audit, each finding written as "current → gap → action":

1. **Crawlability** — per-UA robots.txt for AI crawlers, Cloudflare/WAF blocking, SSR vs CSR (most AI crawlers don't run JS), redirects/canonical, Core Web Vitals.
2. **AI entry files** — `llms.txt` / `llms-full.txt`, `sitemap.xml` freshness & coverage.
3. **Structured data** — Organization / Product / Person / FAQPage / Article / BreadcrumbList / AggregateRating; fields must match the confirmed positioning.
4. **Meta** — per-page title / description / canonical / OG / Twitter / hreflang.
5. **Content citability** — first-100-words direct answer, top-30% key facts, Princeton's Quotation/Statistics/Cite-Sources, paragraph length, list ratio, heading hierarchy, single-topic focus, freshness, alignment with positioning, **false-claims detection**.
6. **Live search** — brand terms (+ name-collision pollution), category terms, competitor comparisons, real AI-engine citation tests.
7. **Off-site authority** — reviews, listicles, Product Hunt / Reddit / HN / **YouTube** (highest AI-visibility correlation), G2 / Trustpilot, Wikipedia / knowledge graph, cross-platform consistency.

---

## Research foundation

The thresholds above are grounded in published research:

- **Princeton GEO (KDD 2024)** — most effective methods: Quotation +41%, Statistics +33%, Cite Sources +30%; keyword stuffing is near-useless for AI search.
- **Structural citation research (2026)** — content structure contributes ~45%; 44.2% of AI citations come from the top 30% of a page; 90% of high-citation pages give a direct answer in the first 100 words; lists/tables extract 43% more accurately than prose.
- **Platform data (2026)** — Schema markup → 2.5× citation odds; YouTube mention ↔ AI visibility correlation 0.737 (highest); G2/Trustpilot → 3× citation odds; content untouched for 3 months falls off a cliff.

See `SKILL.md` for full references.

---

## Install

This is a single-file agent skill (`SKILL.md`). Drop it where your agent looks for skills.

**Claude Code** (and compatible agents):

```bash
git clone https://github.com/ericshang98/geo-shang.git ~/.claude/skills/geo-shang
```

Or, if you use a skill manager:

```bash
npx skills add github:ericshang98/geo-shang
```

Then invoke it:

```
/geo-shang
```

On first run (no positioning document found) it researches your project and drafts a `geo-shang.html` for you to review and confirm. On later runs it reads the doc, refreshes the audit zone, and optimizes — technical first.

---

## Privacy

The positioning document this skill produces (`geo-shang.html` / `geo-shang-cn.html`) is **your private, per-project content** — it holds your confirmed positioning **and an internal audit zone** (a "false claims to delete" table, founder facts, GEO strategy). It belongs in *your* project, never in this skill repo. The bundled `.gitignore` excludes `geo-shang*.html` / `geo-shang*.md` as a safeguard. Keep those docs out of any repo that could go public.

---

## License

MIT © 2026 Eric Shang (尚奕勇). See `LICENSE`.

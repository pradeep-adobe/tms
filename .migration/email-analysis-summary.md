# Email: Thermo Fisher AEM → EDS Migration — Block & Template Analysis Summary

---

**Subject:** Thermo Fisher AEM → EDS Migration: Complete Block & Template Analysis — Functional Docs, Template Mapping & Block Inventory Ready for Confluence

**To:** [Project Manager]
**CC:** [Tech Lead], [Architecture Team]
**From:** [Your Name]

---

Hi [PM Name],

I've completed a comprehensive analysis of the Thermo Fisher Scientific website (thermofisher.com) to support our AEM → Edge Delivery Services migration. This covers **81,753 pages** across three coexisting AEM platforms. Below is the complete summary — I've also generated **12 detailed HTML reports** (attached / in Git) that need to be published to Confluence. Could you please align someone from the team to upload these?

---

## KEY HIGHLIGHTS

**1. Complete Functional Documentation Created for All 35 Blocks (88 Variations)**
We now have developer-ready functional documentation covering every identified block and its variations. Each variation is documented with: DOM structure, acceptance criteria (QA-ready checklists), user interactions (click/hover/animations/keyboard), responsive behavior across 3 breakpoints (mobile/tablet/desktop), WCAG accessibility requirements (ARIA roles, keyboard nav), and authoring field specifications. This is ready for **LLD creation, developer handoff, QA test case writing, and Jira story breakdown**.

**2. Full Template → Block Mapping Matrix (21 Templates × 35 Blocks)**
Every page template has been mapped to its exact block usage — showing which block variations appear on which template. This mapping reveals that **the top 5 templates cover 82% of all 81,753 pages** and that **10 cross-cutting blocks appear on virtually every template**, making them the highest-priority development targets.

**3. 87 Block Variations Identified Across 3 AEM Platforms with Visual Evidence**
Deep DOM analysis of 22 live pages uncovered **35 blocks with 87 distinct variations** spanning Modern AEM Core, Legacy AEM Classic (Parsys/CQ5), and Corporate TFC platforms. 8 entirely new blocks and 15 new variations were discovered that weren't visible from surface scans. **59 screenshots** provide visual evidence of each variation.

**4. Actionable Consolidation Plan: 35 Blocks → ~30 EDS Blocks (85–165 Dev Days)**
A concrete consolidation strategy recommends which blocks to merge (11), keep standalone (15), split (2→5), or absorb (3). This reduces implementation scope while preserving all functionality. The **Cards block alone has 11 variations** but can be consolidated into a single EDS block with CSS modifiers.

**5. Three Coexisting AEM Platforms Create Significant Migration Complexity**
51% of pages use **mixed Modern + Legacy markup** where the same conceptual block (e.g., sidebar-nav) has completely different DOM structures. Forms integrate with **two different backend systems** (Pragma + Eloqua). The corporate subdomain uses an entirely separate component library (`cmp-tfc-*`). This fragmentation is the #1 technical risk.

**6. Template Consolidation Opportunity: 21 AEM Templates → 12 EDS Templates**
Analysis identified that many AEM templates share 80%+ block overlap. By merging L1/L2 category templates, standardizing form pages, and creating a "Hub" super-template, we can reduce from 21 to 12 EDS templates — significantly reducing development and maintenance overhead.

---

## 1. Scope of Analysis

| Dimension | Count |
|-----------|-------|
| Total URLs analyzed | **81,753** |
| AEM platforms detected | **3** (Modern AEM Core Components, Legacy AEM Classic/Parsys, Corporate TFC) |
| Blocks identified | **35** |
| Block variations documented | **87** |
| Page templates identified | **21** |
| Template variations | **43** |
| Live pages inspected (deep DOM analysis) | **22** |
| Block screenshots captured | **59** |
| Functional doc sections per variation | **9** (structure, criteria, interactions, responsive, a11y, authoring, etc.) |

---

## 2. What Was Analyzed & How

### Phase 1: URL Classification & Block Discovery
- Ingested and deduplicated **81,753 URLs** from the sitemap
- Classified every URL into template groups using path pattern analysis
- Identified 3 distinct AEM platforms coexisting on the site by analyzing DOM class patterns:
  - **Modern** (`.cmp-p-*` prefix) — ~38% of pages
  - **Legacy Classic** (`.parsys`, `.cq-colctrl-lt*`) — ~6% of pages
  - **Mixed Modern+Legacy** — ~51% of pages
  - **Corporate TFC** (`.cmp-tfc-*`) — ~4% of pages (corporate.thermofisher.com)

### Phase 2: Block Inventory & Variation Analysis
- Performed deep DOM inspection of **22 representative live pages** using browser automation
- Identified **35 unique blocks** with **87 total variations** across the three platforms
- For each block: cataloged DOM structure, CSS classes, behavioral patterns, and platform origin
- Discovered **8 new blocks** and **15 new variations** not visible from initial surface scans (e.g., workflow-stepper, chapter-toc, video-playlist, handbook-search, support-hub)
- Captured **59 full-page screenshots** of block variations from live thermofisher.com pages

### Phase 3: Template → Block Mapping
- Mapped all 35 blocks to their usage across 21 templates with exact variation tracking
- Identified **10 cross-cutting blocks** appearing on 5+ templates (hero, cards, columns, teaser, sidebar-nav, accordion, form, section-metadata, resources-grid, anchor-nav)
- Identified **16 template-specific blocks** unique to 1–2 templates (mondrian, event-table, workflow-stepper, chapter-toc, etc.)
- Created a full matrix: Template × Block × Variation with reference URLs for every combination

### Phase 4: Functional Documentation (Developer & QA Ready)
- Documented **every block variation** with 9 comprehensive sections:
  1. **Description** — What it is and where it's used
  2. **Structure / Fields** — DOM elements, CSS classes, tag hierarchy
  3. **Visual/Functional Differences** — How it differs from other variants of the same block
  4. **Acceptance Criteria** — 5–8 testable checkboxes per variation (ready for QA/Jira)
  5. **Interactions** — Click behaviors, hover effects, animations, dynamic loading, lazy loading
  6. **Responsive Behavior** — Mobile (<768px), Tablet (768–1024px), Desktop (>1024px) layouts
  7. **Accessibility** — ARIA roles/labels, keyboard navigation, screen reader behavior, focus management
  8. **Authoring Requirements** — Required/optional fields, validation rules, content guidelines
  9. **Reference URLs** — Live thermofisher.com links where each variation can be observed

---

## 3. Block Inventory Summary (35 Blocks, 87 Variations)

### Core Blocks (highest impact — used across most templates)

| # | Block | Variations | Complexity | Recommended Action | Est. Dev Days |
|---|-------|-----------|------------|-------------------|---------------|
| 1 | **Hero** | 7 | Medium | Split into 3: hero, hero-legacy, hero-corporate | 6–10 |
| 2 | **Cards** | 11 | Medium-High | Consolidate: single block with variant CSS classes | 5–8 |
| 3 | **Columns** | 7 | Medium | Consolidate: 2/3/4-col + asymmetric variants | 3–4 |
| 4 | **Teaser** | 5 | Medium | Consolidate: bar, full-image, split, promo, gradient | 3–5 |
| 5 | **Form** | 4 | Complex | Split into 2: form + form-complex (Eloqua/XF) | 8–12 |

**Hero details:** 7 variations spanning standard page heading (V1), foreground product image (V2), gradient overlay (V3), CTA buttons (V4), legacy thinbanner (V5), Mondrian hero (V6), and corporate hero (V7). Each has different DOM structure, responsive breakpoints, and authoring fields documented.

**Cards details:** 11 variations including 3-up/4-up/2-up image cards, text overlay on dark image, text-only, product showcase, legacy 4-column category cards, icon value props, promotional cards with badges, tech reference cards, and decorative icon cards. All can be served by a single EDS block with CSS class modifiers.

### Navigation & Interactive Blocks

| # | Block | Variations | Complexity | Est. Dev Days |
|---|-------|-----------|------------|---------------|
| 6 | Sidebar Nav | 3 | Medium | 3–5 |
| 7 | Video | 4 (inline, YouTube, transcript, playlist) | Medium | 4–6 |
| 8 | Accordion | 2 (AEM Core + Bootstrap) | Medium | 2–3 |
| 9 | Tabs | 3 (horizontal, vertical, workflow stepper) | Medium | 3–5 |
| 10 | Anchor Nav | 3 | Simple | 1–2 |
| 11 | Product Sub-Nav | 2 | Complex | 5–8 |
| 12 | Event Table | 1 (filterable: 3 filter groups, 17 checkboxes, text search) | Complex | 5–8 |
| 13 | Carousel | 2 (tabbed rotator + filmstrip) | Complex | 5–7 |
| 14 | Embed | 3 (social, widget, PDF) | Medium | 2–4 |
| 15 | Table | 2 (data table + comparison) | Simple | 1–2 |

**Event Table detail:** Complex filterable event listing with 18+ event rows, text search with debounce, and 3 checkbox filter groups (Event Type: 9 options, Region: 3, Month: 5 = 17 total checkboxes). Each event row is a full-width card with title, date/location, description, thumbnail, and 2 CTA links.

**Video detail:** 4 distinct patterns — Brightcove inline player, YouTube embed, video with expandable transcript, and a playlist player (Brightcove left + scrollable playlist panel right). All Brightcove instances use `bc-player-*` IDs.

### Specialized & Layout Blocks

| # | Block | Variations | Complexity | Est. Dev Days |
|---|-------|-----------|------------|---------------|
| 16 | Mondrian | 4 (module-d, module-f, 3-tile, 2-tile) | Complex | 5–8 |
| 17 | Highlights | 1 (stats slider with dots) | Medium | 2–3 |
| 18 | Quote | 2 (CEO blockquote, testimonial) | Simple | 1–2 |
| 19 | Resources Grid/List | 2 | Simple | 1–2 |
| 20 | Section Metadata | 8 (light, dark, grey, accent, navy, beige, brand, gradient) | Simple | 1–2 |
| 21 | Chapter TOC | 1 (handbook with 16 chapters, 7 parts) | Medium | 2–3 |
| 22 | Workflow Stepper | 1 (5-step tabbed workflow) | Complex | 4–6 |
| 23 | Support Hub | 1 (6 categories, accordion, modal, Material Design icons) | Complex | 4–6 |
| 24 | Video Teaser + Modal | 2 (thumbnail trigger + lightbox player) | Medium | 3–4 |
| 25–35 | CSR Pillars, Blog Cards, Featured Grid, Pipeline, Social Share, Download Card, Quick Menu, Handbook Search, CSR Report | 1–2 each | Simple–Medium | 1–3 each |

### Consolidation Recommendation Summary

| Action | Count | Blocks |
|--------|-------|--------|
| **CONSOLIDATE** | 11 blocks | cards, columns, teaser, sidebar-nav, video, anchor-nav, tabs, accordion, embed, table, quote |
| **STANDALONE** | 15 blocks | product-sub-nav, event-table, mondrian, carousel, highlights, workflow-stepper, chapter-toc, support-hub, video-teaser, video-modal, video-playlist, featured-grid, pipeline, handbook-search, quick-menu |
| **SPLIT** | 2 → 5 blocks | Hero (→ hero, hero-legacy, hero-corporate), Form (→ form, form-complex) |
| **MERGE/DEFAULT** | 3 blocks | download-card (→ cards), csr-report (→ cards), social-share (→ default content) |
| **MAP** | 1 block | section-metadata (from legacy "wells") |

**Final recommended EDS block count: ~30 custom blocks**
**Estimated total development: 85–165 dev days**

---

## 4. Template → Block Mapping Summary (21 Templates)

### Top Templates by Page Count (82% of site)

| Rank | Template | Est. Pages | % of Site | Blocks Used | Key Variations |
|------|----------|-----------|-----------|-------------|----------------|
| 1 | **T05: Form Page** | 18,521 | 22.7% | 3 blocks | hero (V1, V5), form (V1-Pragma, V2-Eloqua), teaser (V1) |
| 2 | **T03: Category Deep** | 16,758 | 20.5% | 12 blocks | hero, sidebar-nav, cards (V1, V2, V6), columns (V1, V4-V6), video, mondrian (V2-V4), table, form (V3-V4), resources-grid |
| 3 | **T06: Promotion** | 13,813 | 16.9% | 5 blocks | hero (V1, V3), cards-V9 (promo badge), teaser (V1, V2, V4), form (V1) |
| 4 | **T07: Tech Resources** | 6,871 | 8.4% | 5 blocks | hero (V1), cards-V10 (tech ref), anchor-nav (V1), section-metadata (V8) |
| 5 | **T15: PAS/Services** | 6,676 | 8.2% | 8 blocks | hero, accordion (V1-V2), anchor-nav, video-teaser (V1), video-modal (V1), cards (V1) |

### Cross-Cutting vs. Template-Specific Blocks

| Category | Count | Blocks | Significance |
|----------|-------|--------|-------------|
| **Cross-cutting** (5+ templates) | 10 | hero, cards, columns, teaser, sidebar-nav, accordion, form, section-metadata, resources-grid, anchor-nav | These 10 blocks appear on 90%+ of pages. **Build these first.** |
| **Template-specific** (1–2 templates) | 16 | mondrian, event-table, workflow-stepper, chapter-toc, video-playlist, csr-pillars, highlights, support-hub, etc. | Unique to specific page types. Can be built later or in parallel workstreams. |

### Template Consolidation: 21 → 12 EDS Templates

| Consolidation | AEM Templates | EDS Target |
|--------------|--------------|------------|
| Merge L1 + L2 category | T01 (L1) + T02 (L2) | → 1 "Category Hub" template |
| Standardize forms | T05-Modern + T05-Legacy | → 1 "Form" template |
| Merge deep pages | T03 + T04 variant | → 1 "Content Deep" template |
| Create hub super-template | T08 (Events) + T15 (Services) + T20 (Support) | → 1 "Hub" template |
| Keep as-is | Remaining 8 templates | → 8 individual templates |

---

## 5. Detailed Findings & Risks

### Critical Technical Findings

1. **Platform Fragmentation (HIGH RISK)** — 51% of pages use mixed Modern+Legacy markup. The same block (e.g., sidebar-nav) has completely different DOM structures across platforms. EDS blocks will need platform-aware transformation logic during content import.

2. **Form Backend Diversity (HIGH RISK)** — 4 form variations across 2 backend systems: Modern Pragma (AEM Core Forms) and Legacy Eloqua (Oracle marketing automation). Form migration must maintain lead capture continuity. Eloqua forms include hidden tracking fields, elqFormName, elqSiteId, and redirect-to-thank-you-page flows that must be preserved.

3. **Brightcove Video Dependency (MEDIUM RISK)** — All video blocks (4 variations) use Brightcove video.js player with `bc-player-*` IDs. EDS integration requires Brightcove account configuration, player ID mapping, and playlist API access.

4. **Adobe Target Personalization on Teasers (MEDIUM RISK)** — Teaser blocks use `dm-dynamic-offer` class indicating server-side personalization via Adobe Target. Migrating personalized content requires a strategy for Target integration in EDS or fallback static content.

5. **jQuery + Migrate 3.4.1 Dependency on Legacy Pages** — Legacy pages depend on jQuery with Migrate plugin. EDS migration must replace all jQuery-dependent behaviors with vanilla JS implementations.

6. **Corporate Site Isolation (LOW RISK)** — corporate.thermofisher.com is a separate AEM instance with distinct `cmp-tfc-*` component library and unique blocks (CSR pillars, highlights, quote, social-share). Can be treated as an independent workstream with 4–5 custom blocks.

### Key Complexity Drivers

| Factor | Impact | Affected Blocks |
|--------|--------|-----------------|
| Event Table filtering (17 checkboxes, 3 groups, text search) | 5–8 dev days alone | event-table |
| Mondrian grid with multiple slot layouts | 5–8 dev days | mondrian (4 variants) |
| Workflow stepper with 5-step tabbed content (78 h3s, 108 images) | 4–6 dev days | workflow-stepper |
| Video playlist with Brightcove + sidebar panel | 3–5 dev days | video-playlist |
| Support hub with accordion + modal + Material Design icons + chat | 4–6 dev days | support-hub |

---

## 6. Deliverables (12 HTML Reports + Data Files)

All reports are in the Git repo on branch **`migration/block-template-analysis`**. Each HTML file is self-contained with embedded CSS — ready for direct paste into Confluence.

### Reports for Confluence Upload

| Report | File | What It Contains |
|--------|------|-----------------|
| **Report 1** | report-1-block-summary.html | Master block inventory table with screenshots, complexity ratings, and consolidation actions for all 35 blocks |
| **Report 2** | report-2-detailed-breakdown.html | All 87 variations with per-variation screenshots, reference URLs, platform tags, and [NEW] markers |
| **Report 3** | report-3-coverage.html | Block coverage analysis across URL categories showing which blocks serve which page types |
| **Report 4** | report-4-complexity.html | Complexity assessment with effort estimates (dev days) per block, prioritized by impact |
| **Report 7** | report-7-template-list.html | 21 templates with 43 variations, page counts, sample URLs, and platform distribution |
| **Report 8** | report-8-template-block-mapping.html | Full template → block mapping matrix with color-coded block tags by category |
| **Report 9** | report-9-consolidated-insights.html | Consolidated template→block list sorted by page count + 6 optimization recommendations |
| **Report 10** | report-10-block-functional-docs-core.html | **Functional docs:** Hero (7v), Cards (11v), Columns (7v), Teaser (5v), Form (4v) — 34 variations with full 9-section documentation each |
| **Report 11** | report-11-block-functional-docs-nav-interactive.html | **Functional docs:** Sidebar Nav, Accordion, Tabs, Video, Carousel, Event Table, Anchor Nav, Embed, Table — 25 variations |
| **Report 12** | report-12-block-functional-docs-specialized.html | **Functional docs:** Mondrian, Highlights, Quote, CSR, Support Hub, Chapter TOC, Video Modal, and 13 more — 29 variations |

### Supporting Data Files (Machine-Readable)

| File | Purpose |
|------|---------|
| `master-block-inventory.json` | Complete block catalog — parseable for tooling integration |
| `template-block-mapping.json` | Template→block mapping with cross-cutting and template-specific block lists |
| `thermo-fisher-block-analysis.json` | Deep DOM behavioral analysis data from 22 live pages |
| `screenshot-plan.json` | Screenshot metadata mapping files to block variations |
| `screenshots/` (59 files) | Visual evidence of each block variation from live pages |

---

## 7. Suggested Next Steps

| Priority | Action | Owner | Notes |
|----------|--------|-------|-------|
| **P0** | Publish all 12 HTML reports to Confluence | Content/Ops | HTML files are self-contained — paste directly into Confluence pages |
| **P0** | Review block consolidation recommendations (35→30) | Architecture | Validate split/merge/consolidate decisions with tech lead |
| **P1** | Create Jira epics from functional docs (Reports 10-12) | PM | Each block = 1 epic, each variation = 1 story. Acceptance criteria are pre-written. |
| **P1** | Begin EDS development: 10 cross-cutting blocks | Dev Team | Hero, cards, columns, teaser, form, sidebar-nav, accordion, tabs, anchor-nav, section-metadata |
| **P2** | Plan form migration separately | Dev + Marketing Ops | Requires Eloqua/Pragma backend coordination. Estimated 8–12 dev days. |
| **P2** | Confirm Brightcove account/player config for EDS | Video/Media Team | All video blocks depend on Brightcove player IDs |
| **P3** | Plan corporate site migration as separate workstream | PM | ~4% of pages, isolated component library, 4–5 unique blocks |

---

Please let me know if you need any clarification on the analysis, or if you'd like me to walk through any specific section in a call. Happy to also help with the Jira story breakdown once the functional docs are reviewed.

Best regards,
[Your Name]

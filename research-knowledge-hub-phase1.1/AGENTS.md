# AGENTS.md — Research Knowledge Hub

## 1. Project Purpose
Research Knowledge Hub is a personal academic research knowledge base.
It organizes:
- Paper reading notes using a consistent six-section structure.
- Standalone knowledge notes about algorithms, models, methods, and concepts.
- Research topic pages that connect papers and knowledge notes.

The site is a static, read-only publishing site. It is not an online editor or database.

## 2. Audience and Language
- Primary language: Traditional Chinese (繁體中文).
- Keep established technical terms in English on first mention, e.g. 時間序列異常偵測 (Time Series Anomaly Detection, TSAD).
- Use concise, academically appropriate wording.
- Preserve paper titles, author names, publication names, DOI, URLs, and reported metrics accurately.
- Do not translate proper nouns, model names, dataset names, or metric names inconsistently.

## 3. Technology Constraints
- Site generator: MkDocs.
- Theme: Material for MkDocs.
- Content format: Markdown with YAML front matter where applicable.
- Search: Material for MkDocs built-in search.
- Deployment: GitHub Pages through GitHub Actions.
- No backend, database, login, paid API, or AI API is required for v1.
- Do not introduce a JavaScript framework or a second site generator without explicit approval.

## 4. Directory Structure
- `docs/index.md`: homepage.
- `docs/papers/`: one Markdown file per paper; `index.md` is the paper directory.
- `docs/knowledge/`: standalone concept notes; group them into subfolders by broad domain.
- `docs/topics/`: research topic landing pages that link to relevant papers and knowledge notes.
- `docs/assets/images/`: images used by the site.
- `templates/`: reusable Markdown templates; these are not published as site pages.
- `mkdocs.yml`: site configuration and navigation.
- `requirements.txt`: Python dependencies.
- `.github/workflows/deploy.yml`: Pages deployment workflow.

Do not put source PDFs, copyrighted full-text papers, private course files, or personal information in the public `docs/` directory. Link to a lawful publisher page or DOI instead.

## 5. Paper Note Rules
Every paper note must:
1. Use one Markdown file in `docs/papers/`.
2. Use a stable, lowercase, hyphen-separated English slug as its filename.
3. Include YAML front matter with at least `title`, `year`, `publication`, `research_area`, `tags`, and `status`.
4. Include these six sections in this exact order:
   - `## 1. 概述`
   - `## 2. 研究背景`
   - `## 3. 相關工作`
   - `## 4. 解決方案`
   - `## 5. 實驗設計`
   - `## 6. 結論`
5. Include source links (DOI, publisher page, or official project page) when available.
6. Distinguish the paper's claims/results from the writer's interpretation.
7. Never invent authors, publication details, dataset sizes, metrics, or experimental results.
8. If information is unavailable, write `待補充` or omit an optional field; do not guess.
9. Avoid reproducing long passages from copyrighted papers. Summarize in original wording.

Recommended front matter:
```yaml
---
title: "Paper title"
authors: []
year: 2026
publication: "Journal or conference"
paper_url: "https://doi.org/..."
research_area:
  - "Deep Learning"
tags:
  - "Anomaly Detection"
status: completed
---
```

Allowed `status` values: `to-read`, `reading`, `completed`.

## 6. Knowledge Note Rules
Each knowledge note must:
- Be stored under `docs/knowledge/<domain>/`.
- Use a lowercase, hyphen-separated English filename.
- Explain one primary concept per page.
- Use this structure:
  - `## 1. 基本概念`
  - `## 2. 核心原理`
  - `## 3. 主要特色`
  - `## 4. 應用情境`
  - `## 5. 優點與限制`
  - `## 6. 相關論文`
  - `## 7. 相關知識`
- Link to relevant paper notes with relative Markdown links.
- Clearly mark uncertain or paper-specific interpretations.
- Avoid creating duplicate pages for synonyms; update the existing concept page where appropriate.

## 7. Research Topic Rules
- Store topic pages in `docs/topics/`.
- A topic page introduces the scope of the topic and links to relevant paper notes and knowledge notes.
- Do not duplicate full paper summaries on topic pages.
- Keep topic names consistent across front matter, tags, and navigation.
- A topic may link to multiple papers and knowledge pages.

## 8. Naming and Linking
- Use lowercase English slugs with hyphens, e.g. `time-series-anomaly-detection.md`.
- Use descriptive titles in page content; filenames should remain stable after publication.
- Prefer relative Markdown links between local pages.
- When renaming a page, update all inbound links and `mkdocs.yml` navigation.
- Avoid spaces and non-ASCII characters in filenames.

## 9. Design and UX
- Academic research style: clean, restrained, readable.
- Primary palette: navy/blue, white, and light gray.
- Prioritize typography, whitespace, clear hierarchy, and long-form reading.
- Keep the left navigation and page hierarchy consistent.
- Ensure desktop and mobile layouts remain usable.
- Avoid decorative animations, excessive gradients, oversized dashboard widgets, and unnecessary card effects.
- Use tables only when they improve comparison or scanning.

## 10. AI Change Workflow
Before changing files:
1. Read this `AGENTS.md`.
2. Inspect the relevant existing files and links.
3. Reuse existing templates and conventions.
4. Make the smallest coherent change.

When adding a paper:
1. Create its paper note from `templates/paper-template.md`.
2. Populate only facts supported by the supplied paper or reliable source.
3. Add it to `docs/papers/index.md` and `mkdocs.yml`.
4. Identify concepts worth documenting; do not create knowledge pages automatically if the concept is trivial or duplicates an existing page.
5. Update relevant topic pages and cross-links.

When adding a knowledge note:
1. Check whether the concept already exists.
2. Create it from `templates/knowledge-template.md`.
3. Add links to relevant papers and related concepts.
4. Update the appropriate topic page if relevant.

When editing:
- Preserve existing content unless the user asks for restructuring.
- Do not silently remove sections, references, or caveats.
- Do not rewrite the user's personal reflections as if they were claims made by the paper.
- Do not fabricate content to make a page look complete.

## 11. Validation
Before considering a change complete:
- Check Markdown headings and YAML front matter.
- Check local links and image paths.
- Check that every paper note has the six required sections in order.
- Check that navigation includes newly added published pages.
- Run `mkdocs build --strict` when the environment permits.
- Report any validation that could not be run; never claim a successful build without running it.

## 12. Scope Control
For v1, prioritize:
- Homepage
- Paper library
- Knowledge base
- Research topics
- Full-text keyword search

Do not add user accounts, editing forms, database storage, AI summarization, graph visualization, or complex analytics in v1 unless explicitly requested.

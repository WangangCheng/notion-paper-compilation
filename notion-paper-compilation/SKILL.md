---
name: notion-paper-compilation
description: Compile English academic papers into structured Chinese Notion research notes. Use when the user uploads or provides an English paper and specifies a Notion page, database, or workspace location where Codex should fill publication metadata, translate the paper body into Chinese, render formulas, add Notion callout explanations, mark figure/table insertion points, create method overviews, generate excerpts, and create or link journals, conferences, tags, and related Notion records.
---

# Notion Paper Compilation

## Overview

Turn an English academic paper into a complete Chinese Notion paper-management entry: metadata, method-focused summary, translated body, formula rendering, figure/table insertion callouts, beginner-friendly explanatory callouts, excerpts, and tags.

## Required Inputs

- Require the original English paper file or accessible full-text source.
- Require the target Notion location from the user, such as a page name, page URL, paper database entry, or workspace/page that contains the paper-management databases.
- If either input is missing, ask only for the missing item before writing to Notion.

## Tool Use

- Use Notion tools to search/fetch the specified target first. Do not assume property names, relation names, database IDs, or templates.
- Fetch the target page and database schema before updating any properties.
- Use document/PDF extraction tools for uploaded papers. If extraction quality is poor, inspect rendered pages or use the paper's official full-text page when available to correct reading order.
- Before creating or updating Notion page content, fetch the Notion enhanced Markdown specification if the available Notion tools require it.
- Fetch existing Notion pages before updating them. Do not replace existing page content destructively unless the user explicitly asks.

## Workflow

Read [references/paper-workflow.md](references/paper-workflow.md) before executing a paper-compilation task.

1. Resolve the target Notion structure: identify the paper page/database, journal or conference database, tag library, excerpt database, relation fields, and available button-equivalent workflows.
2. Extract paper metadata, section structure, equations, figure/table captions, GitHub or code links, method details, results, limitations, and future-work statements.
3. Create or update the paper record and fill publication fields using the target database schema.
4. Translate only the paper body into Chinese, preserving headings, citations, and formulas; skip references, acknowledgements, author contributions, funding, conflicts, and pure figure/table content.
5. Insert Notion callouts for original figures and tables at the closest relevant locations instead of recreating them.
6. Add all beginner-friendly explanations as Notion callouts, not ordinary loose paragraphs.
7. Add a method overview callout before the translated method section, with model-training details when relevant or statistical-analysis details when not.
8. Create or update excerpt records and generated tags, creating missing related database entries when needed.
9. Verify the updated page by fetching it again and report what was filled, created, skipped, and left blank.

## Output Standards

- Write Chinese content for the Notion page body.
- Keep technical terms precise; on first mention, include the English term when helpful.
- The metadata field named `概括` should emphasize the method: problem, existing gap, proposed approach, core modules, input/output, main conclusion, and significance.
- Leave unavailable metadata blank rather than inventing it.
- Treat Notion buttons as UI shortcuts. If the workflow needs excerpts or tags, create/update the underlying records directly with Notion tools.
- Never include the reference list in the Notion body unless the user explicitly asks.

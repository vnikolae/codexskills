---
name: chapter-summary-skill
description: Convert a set of numbered PDF book chapters into two Obsidian-friendly Markdown outputs per chapter: concise summaries and detailed lecture notes. Use when the user asks to summarize book chapters, create chapter notes, produce MBA-style learning notes, or process chapter PDFs one by one into structured Markdown.
---

# Chapter Summary Skill

Use this skill to process numbered chapter PDFs into paired Markdown outputs:

- Concise summaries.
- Detailed lecture notes.

The workflow is designed for book chapter folders where the directory may also contain a full-book PDF, front matter, appendices, indexes, part pages, or other non-chapter files.

## Inputs

Default assumptions:

- Chapter PDFs are named with a visible chapter number, such as `ch01_...pdf`, `chapter_01_...pdf`, or `01_...pdf`.
- Non-chapter PDFs should be ignored unless the user explicitly asks for them.
- Existing output folders should be reused.

If no output folders exist, create:

- `summaries`
- `lecture_notes`

## Processing Rules

1. Identify chapter PDFs only.
2. Sort chapters by chapter number.
3. Process in order, starting with the lowest chapter number.
4. Work one chapter at a time. For efficiency, up to three chapters may be handled as a small batch, but do not process many chapters at once.
5. Save both outputs for each chapter before moving to later chapters.
6. Inspect exhibits, tables, formulas, or figures when they appear important to the chapter’s argument.
7. If PDF text extraction loses formula or table layout, reconstruct the meaning carefully from surrounding text.
8. Do not invent unsupported concepts. Keep summaries faithful to the chapter.

## Extraction Guidance

Use available PDF tools in this order:

1. Prefer text extraction tools already available in the environment.
2. If needed, use Python libraries such as `pypdf` or other installed PDF readers.
3. For important visual exhibits that text extraction does not capture, render or inspect the relevant pages visually.

Temporary extraction folders should be clearly named, such as `.chapter-summary-text`, and cleaned up after final verification.

## Output Naming

Use readable, sortable filenames:

```text
summaries/Chapter_01_Title.md
lecture_notes/Chapter_01_Title.md
```

Normalize titles by removing unsafe filename characters and replacing spaces with underscores.

## YAML Header

Every output file must start with YAML frontmatter.

For concise summaries:

```yaml
---
chapter: 1
title: "Chapter Title"
type: concise_summary
tags:
  - valuation
  - strategy
key_concepts:
  - concept one
  - concept two
source: "ch01_source_file.pdf"
---
```

For detailed notes:

```yaml
---
chapter: 1
title: "Chapter Title"
type: lecture_notes
tags:
  - valuation
  - strategy
key_concepts:
  - concept one
  - concept two
source: "ch01_source_file.pdf"
---
```

Choose tags and key concepts from the chapter content.

## Concise Summary Structure

Use this structure unless the user asks for a different one:

```markdown
# Chapter 01: Chapter Title

## Concise Summary

Write several focused paragraphs explaining the core argument, main frameworks, and important conclusions.

## Key Takeaways

- Takeaway one.
- Takeaway two.
- Takeaway three.
```

The concise summary should be short but substantive. Capture the chapter’s logic, not just a list of topics.

## Detailed Lecture Notes Structure

Use this structure unless the chapter clearly calls for a different organization:

```markdown
# Chapter 01: Chapter Title

## Core Thesis

State the central claim of the chapter.

## Major Concepts

Explain the key ideas, definitions, and frameworks.

## Frameworks and Formulas

Include important formulas, valuation relationships, decision rules, or conceptual models.

## Practical Implications

Explain what managers, investors, or MBA students should do with the chapter’s ideas.

## Common Mistakes

List pitfalls, misinterpretations, or warnings from the chapter.

## MBA Takeaways

Summarize the durable lessons.
```

Adapt headings to fit the chapter, but keep the notes lecture-like and useful for studying.

## Quality Checks

After all requested chapters are complete:

1. Count concise summary files.
2. Count lecture-note files.
3. Verify chapter numbers are continuous or match the requested set.
4. Flag missing chapters.
5. Check for empty or unusually short files.
6. Clean temporary extraction files.
7. Report the number of chapters processed and the output folders.

## Final Response

Keep the final response concise. Include:

- Number of chapters processed.
- Output folder paths.
- Whether any files were skipped and why.
- Any caveats, such as formulas reconstructed from imperfect PDF extraction.

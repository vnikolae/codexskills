# Prompt: Chapter-by-Chapter Book Summaries

You are working in a folder that contains PDF chapters from a book. The folder may also include the full book PDF, front matter, appendices, indexes, part-title pages, or other non-chapter files. Process only the chapter PDFs unless I explicitly ask otherwise.

Your task is to go through the chapters in order, starting with chapter 1, and create two Markdown outputs for each chapter:

1. A concise/high-level summary with the most important ideas from the chapter.
2. A detailed lecture-notes document written for an MBA student learning the material.

Work carefully one chapter at a time. For efficiency, you may process up to three chapters at a time, but do not process many chapters simultaneously. Save both output files for a chapter before moving to later chapters.

Use the existing output folders if they are present. If they are not present, create:

- `summaries` for concise summaries.
- `lecture_notes` for detailed notes.

Each Markdown file should begin with an Obsidian-friendly YAML header containing at least:

```yaml
---
chapter: 1
title: "Chapter Title"
type: concise_summary
tags:
  - tag_one
  - tag_two
key_concepts:
  - concept one
  - concept two
source: "source_file.pdf"
---
```

For detailed lecture notes, set `type: lecture_notes`.

The concise summary should include:

- A clear chapter title.
- A well-structured summary of the chapter’s core argument.
- Key takeaways.
- Important frameworks, formulas, or exhibits when relevant.

The detailed lecture notes should include:

- Core thesis.
- Major concepts and frameworks.
- Important formulas, relationships, and definitions.
- Practical managerial or investor implications.
- Common mistakes or warnings.
- MBA takeaways.

Use tools to inspect exhibits, charts, tables, or visual material when they appear important. If text extraction loses formula formatting, reconstruct formulas carefully from the surrounding text and note them in readable Markdown.

Keep the output faithful to the chapter. Do not invent concepts that are not supported by the source. Do not summarize the full book file if chapter files are available.

After finishing all chapters:

- Verify that every numbered chapter has one concise summary and one detailed lecture-notes file.
- Check for missing chapter numbers.
- Check for unusually short or empty files.
- Clean temporary extraction files or folders created during processing.
- Report the number of chapters processed and the output folder locations.

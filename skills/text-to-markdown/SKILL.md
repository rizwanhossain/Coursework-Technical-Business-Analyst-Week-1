---
name: formatted-text-to-markdown
description: 'Convert formatted or structured text into a clean Markdown (.md) file. Use when turning pasted text, notes, or a workspace text document into formatted Markdown while preserving its meaning and organization.'
argument-hint: 'Provide the source text or file and, optionally, the output path'
---

# Formatted Text to Markdown

Convert user-provided formatted text into a readable, valid Markdown file. Inputs may be pasted text or a text-based workspace file. Preserve the source's content and intent; do not add unsupported facts or silently omit material.

## Procedure

1. Identify the source text and any requested output path. If the user provides neither usable text nor a readable source file, ask them to provide it.
2. Read the entire source before transforming it. Infer its existing structure from title lines, labels, indentation, numbering, spacing, and repeated fields.
3. Convert the structure to appropriate Markdown:
   - Use `#` headings in a logical hierarchy, with one top-level heading where the source has a clear title.
   - Use `-` for unordered lists and numbered Markdown lists for ordered steps; preserve nesting where meaningful.
   - Use Markdown tables for clearly tabular content, keeping headers and row relationships intact.
   - Use fenced code blocks for code or preformatted text, adding a language identifier only when known.
   - Preserve links, emphasis, quoted material, and other meaningful formatting where their intent is clear.
4. Retain wording, facts, names, dates, values, and ordering unless the user asks for editing or correction. Fix only obvious formatting artifacts needed to make the Markdown render cleanly. Do not guess at ambiguous hierarchy or change the substance; ask a concise question if the ambiguity would materially affect the result.
5. Write the result as a new `.md` file. Use the user-specified path when provided. Otherwise, for a workspace file, place the Markdown beside the source using the same base name and a `.md` extension; for pasted text, use a descriptive filename in the most relevant workspace folder, or ask for a location if none is clear. Never overwrite the source or an existing destination without permission.
6. Review the generated file for valid Markdown structure, complete content, and accidental duplication or omission. Report the output path and any meaningful conversion assumptions.

## Output Standards

- Keep the document easy to scan and consistent in heading levels, spacing, and list style.
- Prefer plain Markdown supported by common renderers; avoid unnecessary HTML or custom syntax.
- Preserve meaningful blank lines and separate adjacent sections.
- Do not add an introduction, summary, or commentary that was not in the source unless requested.
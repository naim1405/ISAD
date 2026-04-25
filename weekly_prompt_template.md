# Weekly LaTeX Agent Prompt Template

Use this prompt each week with any AI agent.

## Full Prompt

TARGET_TEX_FILE = isad_report.tex
WEEK_INPUT_TEXT = input.txt

You are generating LaTeX for an academic report that is written incrementally over multiple weeks.

Context:
1. Rules file: text_instructions.md
2. Target LaTeX file: TARGET_TEX_FILE
3. New weekly content: WEEK_INPUT_TEXT

Task:
1. Read and follow text_instructions.md exactly.
2. Decide mode:
	- Initialize Mode if TARGET_TEX_FILE does not exist.
	- Update Mode if TARGET_TEX_FILE already exists.
3. In Update Mode:
	- Read existing TARGET_TEX_FILE first.
	- Preserve preamble, front matter, formatting style, and unchanged chapters.
	- Update only the chapters/sections covered by WEEK_INPUT_TEXT.
	- Keep chapter titles/order unless WEEK_INPUT_TEXT clearly changes them.
4. Use only allowed class/packages/rules from text_instructions.md.
5. Do not add placeholder figures or fake image filenames.
6. Ensure output is compile-ready.

Output requirements:
1. If file editing is available, write directly to TARGET_TEX_FILE.
2. Return the full updated LaTeX document content (not partial snippets).
3. After the LaTeX, provide a short change log with:
	- Mode used (Initialize or Update)
	- Chapters/sections changed this week
	- Confirmation that unchanged chapters were preserved
	- Confirmation that only allowed packages were used

Quality checks before final output:
1. Complete document from begin document to end document.
2. Table of contents and list of figures present.
3. Valid hierarchy (chapter, section, subsection).
4. No custom commands or style deviations from text_instructions.md.

## Fast Weekly Version

Update TARGET_TEX_FILE using WEEK_INPUT_TEXT under strict rules from text_instructions.md. Auto-select Initialize or Update mode. In Update mode, preserve unchanged chapters and existing formatting/preamble/front matter; modify only relevant chapters/sections. No extra packages, no placeholder figures. Return full compile-ready LaTeX and a short change log.

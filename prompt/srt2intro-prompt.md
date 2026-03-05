# SRT to Video Introduction Prompt

## Task

Given an SRT subtitle file, generate a concise video introduction with three parts:

1. **Video Title** — Provide two versions of the title for the same video:
   - Chinese title
   - English title
2. **Summary** — One or more paragraphs describing the overall content of the video, not exceeding 2000 words in total.
3. **Chapter List** — A list of major sections, each on its own line as: `HH:MM  SectionTitle`

---

## Format

```
中文标题：<Chinese title>
English Title: <English title>

<Summary paragraph describing the whole video>

HH:MM  SectionTitle
HH:MM  SectionTitle
HH:MM  SectionTitle
...
```

Rules:
- The summary can be multiple paragraphs but must not exceed 2000 words in total. It describes the full video content, not individual chapters.
- Each chapter entry is exactly two parts on one line: **Timestamp** and **Section Title** (prefer 1–2 words, max 3 words). No context sentence per chapter.
- **The chapter list must contain no more than 10 entries.** This is an upper bound, not a target. Use fewer entries when possible and merge minor topic shifts.
- Timestamp format: MM:SS or HH:MM:SS, no milliseconds.
- Use the same language as the SRT subtitles for the summary and section titles (e.g. Chinese if the subtitles are in Chinese).
- Keep chapter titles short and compact; avoid long phrasing.

---

## Instructions

1. Read through the entire SRT file.
2. Generate two video titles for the same content: one in Chinese and one in English.
3. Write a summary (one or more paragraphs, max 2000 words) describing the overall video content in depth.
4. Identify the major topic shifts or chapter boundaries.
5. For each chapter, output one line: timestamp + very short title.
6. Do not force 10 chapters; choose only the major sections (up to 10 total).
7. Use the same language as the SRT subtitles for summary and chapter titles.
8. Output only titles + summary paragraph(s) + chapter list — no preamble, no extra commentary.
9. Save the output to a file with the same name as the input SRT file but with a `.txt` extension (e.g. `foo.srt` → `foo.txt`), in the same directory.

---

## Example Output

Using the video `agent-bench.srt` (an AI model benchmark for Claude Code workflows):

```
中文标题：Claude Code 实测对比
English Title: Claude Code Agent Benchmark

This video benchmarks multiple LLMs inside real agent workflows using Claude Code, comparing response speed and task completion across domestic and international models. The host runs identical prompts and environments for each model, then presents side-by-side results. Models tested include DeepSeek, Kimi, GLM/BigModel, and Claude.

00:00  back
01:03  intro
02:46  ark
04:59  kimi
06:18  SOTA
07:21  glm
```

---

## Input

Paste the full content of the `.srt` file below, then run this prompt.

```
<INSERT SRT CONTENT HERE>
```

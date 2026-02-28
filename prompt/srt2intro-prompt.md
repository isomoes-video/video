# SRT to Video Introduction Prompt

## Task

Given an SRT subtitle file, generate a concise video introduction with two parts:

1. **Summary** — One or more paragraphs describing the overall content of the video, not exceeding 2000 words in total.
2. **Chapter List** — A list of major sections, each on its own line as: `HH:MM  SectionTitle`

---

## Format

```
<Summary paragraph describing the whole video>

HH:MM  SectionTitle
HH:MM  SectionTitle
HH:MM  SectionTitle
...
```

Rules:
- The summary can be multiple paragraphs but must not exceed 2000 words in total. It describes the full video content, not individual chapters.
- Each chapter entry is exactly two parts on one line: **Timestamp** and **Section Title** (1–3 words). No context sentence per chapter.
- **The chapter list must contain no more than 10 entries.** Merge minor topic shifts and only mark the most significant transitions.
- Timestamp format: MM:SS or HH:MM:SS, no milliseconds.
- Use the same language as the SRT subtitles for both the summary and section titles (e.g. Chinese if the subtitles are in Chinese).

---

## Instructions

1. Read through the entire SRT file.
2. Write a summary (one or more paragraphs, max 2000 words) describing the overall video content in depth.
3. Identify the major topic shifts or chapter boundaries.
4. For each chapter, output one line: timestamp + short title.
5. Use the same language as the SRT subtitles throughout.
6. Output only the summary paragraph(s) and chapter list — no preamble, no extra commentary.
7. Save the output to a file with the same name as the input SRT file but with a `.txt` extension (e.g. `foo.srt` → `foo.txt`), in the same directory.

---

## Example Output

Using the video `agent-bench.srt` (an AI model benchmark for Claude Code workflows):

```
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

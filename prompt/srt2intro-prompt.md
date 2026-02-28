# SRT to Video Introduction Prompt

## Task

Given an SRT subtitle file, generate a concise video introduction.

The introduction must list each chapter section in the following format:

```
HH:MM  SectionTitle  Concise one-sentence context describing what this section covers.
```

Each section entry must have exactly three parts on one line:
1. **Timestamp** — the start time of the section (MM:SS or HH:MM:SS, no milliseconds)
2. **Section Title** — a short name for this segment (1–3 words), written in the same language as the source SRT (e.g. Chinese if the subtitles are in Chinese)
3. **Context** — one concise sentence summarizing what happens in this section, written in the same language as the source SRT

---

## Instructions

1. Read through the entire SRT file.
2. Identify the major topic shifts or chapter boundaries.
3. For each chapter, determine:
   - The timestamp where it begins
   - A short title that captures the topic
   - A single sentence summarizing the content
4. Use the same language as the SRT subtitles for both the section title and context (e.g. write in Chinese if the subtitles are in Chinese).
5. Output only the chapter list — no preamble, no extra commentary.

---

## Example Output

Using the video `agent-bench.srt` (an AI model benchmark for Claude Code workflows):

```
00:00  back     Why benchmark LLMs in real agent workflows instead of relying on public leaderboards.
01:03  intro    Introducing the agent-bench project: testing models inside a Claude Code engine with identical prompts and environments.
02:46  ark      How DeepSeek performed in the benchmark — notably slow API response times despite domestic server access.
04:59  kimi     Kimi's benchmark results and speed comparison against Claude and other models.
06:18  SOTA     Side-by-side SOTA comparison: Claude leads at ~40s, BigModel (GLM) close behind, DeepSeek at 160s+.
07:21  glm      GLM/BigModel from Tsinghua's lab shows the most competitive speed among domestic models.
```

---

## Input

Paste the full content of the `.srt` file below, then run this prompt.

```
<INSERT SRT CONTENT HERE>
```

# Intro to Figure Generation Prompt

## Task

Given a video intro (output from `srt2intro-prompt.md`), generate a 4:3 figure image using the Images API.

The image should visually represent the video's core topic — striking, cinematic, and suitable as a video figure.

---

## Input Format

Paste the intro text below (the output from the intro prompt):

```
<INSERT INTRO TEXT HERE>
```

---

## Instructions

1. Read the intro: titles, summary, and chapter list.
2. Identify the single most important visual concept from the content.
3. Compose a detailed, vivid image generation prompt (in English) that:
   - Captures the core topic in one striking scene
   - Is cinematic and visually bold — suitable for a video figure
   - **Includes bold overlay text** showing the key title or topic (use the English title or a short punchy phrase derived from it), rendered as large, high-contrast typography on the image
   - Uses concrete visual elements (subjects, lighting, environment, mood)
4. Call the Images API to generate the image at `1024x768` (4:3 landscape).
5. Save the result image as `<video-name>.png` in the same directory as the intro file.

---

## API Call

**Endpoint:** `POST https://aiapi.isomoes.site/v1/images/generations`

**Headers:**
```http
Authorization: Bearer $AIAPI_AUTH_KEY
Content-Type: application/json
Cache-Control: no-store, no-cache, max-age=0
Pragma: no-cache
```

**Body:**
```json
{
  "model": "gpt-image-2",
  "prompt": "Use the following text as the complete prompt. Do not rewrite it:\n<YOUR COMPOSED IMAGE PROMPT>",
  "size": "1024x768",
  "output_format": "png",
  "moderation": "auto"
}
```

Replace `<YOUR COMPOSED IMAGE PROMPT>` with the prompt composed in step 3.

---

## Image Prompt Guidelines

- Describe the scene AND the text overlay to include.
- Think: what would make the figure instantly understandable? One powerful visual + a short bold title.
- The text overlay should be the English title or a punchy short phrase (3–6 words max), placed prominently (e.g. center or lower-third).
- Good: `"Three glowing orbs racing through a dark digital tunnel, speed lines, dramatic neon lighting, photorealistic. Bold white text overlay reading 'Claude vs DeepSeek vs GPT' in large sans-serif font, center of image"`
- Good: `"A developer surrounded by floating holographic code panels, dramatic blue light. Large bold text 'Agent Benchmark V1' overlaid in the upper portion"`
- Avoid: vague prompts like "a photo related to AI"
- Avoid: long sentences as the overlay text — keep it 3–6 words, punchy

---

## Output

- The generated image file saved as `<video-name>.png` alongside the intro `.txt` file.
- No additional text output required.

---

## Example

Given intro for `agent-bench.txt`:

```
中文标题：Claude Code 实测对比
English Title: Claude Code Agent Benchmark

This video benchmarks multiple LLMs inside real agent workflows...

00:00  back
01:03  intro
...
```

Composed image prompt:
```
Multiple glowing AI model logos represented as luminous orbs racing side by side through a dark digital tunnel, speed lines, cinematic, photorealistic, dramatic lighting. Bold white text overlay reading "Agent Benchmark" in large sans-serif font centered on the image
```

API call with `size: "1024x768"`, result saved as `agent-bench.png`.

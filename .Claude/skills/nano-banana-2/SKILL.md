---
name: "nano-banana-2"
description: "Generate images using the Google Nano Banana 2 model via MCP. Use this skill when an agent or user requests image generation or visual content creation. Sends a prompt to the model and returns the generated image."
---

# Nano Banana 2 — Image Generation Skill

## Overview

This skill connects to the **Google Nano Banana 2** image generation model via an MCP (Model Context Protocol) server. It handles the full generation cycle: sending a prompt to the model and receiving the resulting image.

> ⚠️ **Configuration required:** The MCP server details in `.claude/settings.json` are placeholders. Replace `command`, `args`, and environment variables with the actual Nano Banana 2 MCP endpoint details before use.

---

## MCP Server

The model is accessed via the `nano-banana-2` MCP server, registered in `.claude/settings.json`:

```json
{
  "mcpServers": {
    "nano-banana-2": {
      "command": "uvx",
      "args": ["nano-banana-2-mcp"],
      "env": {
        "GOOGLE_API_KEY": "${GOOGLE_API_KEY}"
      }
    }
  }
}
```

---

## How to Use This Skill

### Step 1 — Prepare the Prompt

Write a detailed, descriptive image generation prompt. Include:
- Subject and composition
- Style, mood, and tone
- Color palette
- Lighting
- Any specific visual elements required

The richer the prompt, the better the output.

### Step 2 — Call the MCP Tool

Use the MCP tool to generate the image:

```
Tool: mcp__nano-banana-2__generate_image
Parameters:
  prompt: "<your full image generation prompt>"
  output_path: "<path where the image should be saved>"   # optional
```

If `output_path` is not provided, the model returns the image as a URL or base64-encoded data depending on the MCP implementation.

### Step 3 — Handle the Response

The tool returns one of:
- **File path** — if `output_path` was specified and the MCP server saved the file
- **URL** — a hosted link to the generated image
- **Base64 data** — raw image data to be written to disk manually

If the response is base64, save it:

```bash
python3 -c "
import base64, sys
data = '<base64_string>'
with open('<output_path>', 'wb') as f:
    f.write(base64.b64decode(data))
"
```

---

## Error Handling

| Error | Action |
|-------|--------|
| MCP server not connected | Check `.claude/settings.json` and restart Claude Code |
| `GOOGLE_API_KEY` missing | Set the env var and restart |
| Generation failed | Retry once with a simplified prompt |
| Output path not writable | Use `outputs/` directory which is always present |

---

## Output Naming Convention

When saving to `outputs/`, use descriptive filenames:

```
outputs/<YYYY-MM-DD>_<short-description>.png
```

Example: `outputs/2026-04-27_sunset-cityscape-reference-style.png`

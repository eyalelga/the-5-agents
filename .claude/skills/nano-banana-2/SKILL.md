---
name: nano-banana-2
description: Generate images using Google Nano Banana 2 (Gemini 2.5 Flash Image API) via MCP. Use when the user asks to create, generate, or produce an image, or when an agent needs to invoke image generation.
---

# Nano Banana 2 — Image Generation Skill

Generates images via the `nano-banana-2` MCP server, powered by Google Gemini 2.5 Flash Image API.

## How to Use

### Generate an image

```
mcp__nano-banana-2__generate_image(
  prompt: "<your image prompt>"
)
```

The server saves the image automatically and returns the file path.

### Edit an existing image

```
mcp__nano-banana-2__edit_image(
  image_path: "outputs/<filename>.png",
  prompt: "<edit instructions>"
)
```

### Available tools

| Tool | Description |
|------|-------------|
| `mcp__nano-banana-2__generate_image` | Generate a new image from a text prompt |
| `mcp__nano-banana-2__edit_image` | Edit an existing image with a prompt |
| `mcp__nano-banana-2__continue_editing` | Refine the last generated/edited image |
| `mcp__nano-banana-2__get_last_image_info` | Get metadata about the last image |

## MCP Server Configuration (settings.json)

```json
"mcpServers": {
  "nano-banana-2": {
    "command": "npx",
    "args": ["nano-banana-mcp"],
    "env": {
      "GEMINI_API_KEY": "${GEMINI_API_KEY}"
    }
  }
}
```

Requires `GEMINI_API_KEY` in `.env` (obtain from Google AI Studio).

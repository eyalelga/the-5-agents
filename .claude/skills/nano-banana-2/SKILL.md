---
name: nano-banana-2
description: Generate images using the Google Nano Banana 2 model via MCP. Use when the user asks to create, generate, or produce an image, or when an agent needs to invoke image generation. Sends a text prompt to the model and returns the generated image.
---

# Nano Banana 2 — Image Generation Skill

Generates images by sending prompts to the Google Nano Banana 2 model through the `nano-banana-2` MCP server.

## Prerequisites

The `nano-banana-2` MCP server must be configured in `.claude/settings.json` (see below). The server handles authentication and communication with the model endpoint.

## How to Use

### Basic call

Invoke the MCP tool with a prompt:

```
mcp__nano-banana-2__generate_image(
  prompt: "<your image prompt>",
  output_path: "outputs/<filename>.png"
)
```

### Parameters

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| `prompt` | string | yes | Text description of the image to generate |
| `output_path` | string | yes | Where to save the resulting image |
| `width` | number | no | Image width in pixels (default: 1024) |
| `height` | number | no | Image height in pixels (default: 1024) |
| `style` | string | no | Style hint passed to the model |

### Workflow

1. Receive the prompt (already crafted by the calling agent)
2. Call `mcp__nano-banana-2__generate_image` with the prompt and output path
3. Verify the file was written to `output_path`
4. Return the path of the saved image to the caller

### Error handling

- If the MCP server is unreachable → report the connection error and stop
- If the model returns an error → report the model error verbatim and stop
- If the output file is not created → report that the image was not saved

## MCP Server Configuration

The following must be present in `.claude/settings.json` under `mcpServers`:

```json
"nano-banana-2": {
  "command": "npx",
  "args": ["-y", "@google/nano-banana-mcp"],
  "env": {
    "GOOGLE_API_KEY": "<your-api-key>",
    "MODEL_ID": "nano-banana-2"
  }
}
```

> **Note:** Replace `@google/nano-banana-mcp` and the env vars with the actual MCP package and credentials once confirmed.

---
title: Free AI Tools
author: Tyler Angelier
pubDatetime: 2025-07-26T22:59:39Z
slug: free-ai-tools
featured: true
draft: false
tags:
  - ai
  - ollama
  - aider
  - openrouter
description: Free AI tools that I use
---

This will be a quick one—I wanted to document some of the AI tools I'm using. Most are free, though I do have a ChatGPT Plus subscription. I might switch to Anthropic’s offering one day, but for now, I like having ChatGPT as a reliable assistant, especially for coding tasks.

### OpenRouter

The first thing to mention is [OpenRouter](https://openrouter.ai/). This fantastic service routes your API requests to providers of nearly every major model you can think of. The best part? Their free tier is _really, really_ good. If you upload $10 (just once), you get 1,000 requests per day to any free models. Some notable ones:

- [Qwen3 Coder](https://openrouter.ai/qwen/qwen3-coder:free) – a 480B model
- [Kimi K2](https://openrouter.ai/moonshotai/kimi-k2:free) – a 1 trillion parameter model
- [Deepseek V3 0324](https://openrouter.ai/deepseek/deepseek-chat-v3-0324:free)

If you want access to premium models, OpenRouter's pricing is also quite reasonable.

### Ollama

Next is [Ollama](https://ollama.com/), a simple CLI that works on Linux, macOS, and Windows, allowing you to run a wide range of models locally. You probably have a machine capable of running _some_ model.

I run Ollama on two systems:

- **Proxmox server**
  - Nvidia 2070 Super (8GB VRAM)
  - 16GB DDR4 RAM
  - Intel i7-9700K

- **Gaming PC**
  - Nvidia 5080
  - 32GB DDR5 RAM
  - Ryzen 7 9800X3D

I can fit a 4B model with a 16k context on the Proxmox server. It’s okay for some tasks, but limited. I get decent speed running `deepseek-r1:8b` with small context sizes (50+ tokens/sec). On the gaming PC, I can comfortably run coding models in the 7B–14B range. Ollama automatically handles CPU offloading when VRAM isn’t sufficient.

> So what’s the point?

The key reason I use these locally is because they're _absolutely free_. I’ve probably burned through $100 or more in tokens on experiments that didn’t go anywhere—but they helped me learn how the tools work. For example, when testing [OpenCode](https://opencode.ai/), instead of spending tokens or burning through OpenRouter’s free credits, I connected it to Ollama and tested things locally.

### Open WebUI

I use [Open WebUI](https://github.com/open-webui/open-webui) as the interface for all my local and remote models. It’s a self-hostable, ChatGPT-style front end that lets you aggregate your LLMs in one place.

I was initially mesmerized by chatting with local models in such a polished interface. It supports agents, MCP servers, RAG, and much more. But the real power is this: _you can integrate nearly all your AI tools into this one interface_.

- Add your OpenRouter API key and use any of their free models.
- Connect Ollama and chat with local models.
- Use the built-in OpenAI-compatible REST API to integrate other tools that expect a standard OpenAI endpoint.

### Coding Tools

Finally, here are some tools I use for coding:

- I primarily use [Aider](https://aider.chat/) because it fits perfectly into my terminal-focused workflow. It supports multiple backends and is easy to use.
- I’ve also tried Cline, RooCode, and OpenCode—solid options, but I prefer Neovim and the terminal.
- _And of course, there's [gemini-cli](https://github.com/google-gemini/gemini-cli)_, Google's agentic CLI tool (a direct competitor to Claude Code). Its free tier is impressive.

---

That wraps up the AI tools I use—most of which are free. I’ll admit, we get access to some excellent models at Oracle with _near-unlimited_ usage, although the tooling is still catching up to state-of-the-art things in the open-source world.

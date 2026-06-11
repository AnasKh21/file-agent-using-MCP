# Enhanced MCP Server

A small project to learn how AI agents actually work — not just calling an API, but building the full loop where Claude can decide to use tools, chain actions, and interact with the user mid-task.

## What it does

You run it from the terminal, pick an option from the menu, and Claude handles the rest. It can read and write files, review your code, or generate documentation — all by itself, calling the tools it needs along the way.

```bash
python client.py server.py
```

## How it works

There's a server (`server.py`) that exposes tools and prompts over MCP, and a client (`client.py`) that connects to it, sends your requests to Claude, and handles everything Claude wants to do — tool calls, progress updates, asking you for input when needed.

The core mechanic is the **agentic loop**: Claude keeps calling tools until it has everything it needs to answer. No hardcoded steps, it figures out the sequence on its own.

One thing I found interesting to implement: **elicitation** — the server can pause and ask the user for input in the middle of a task, through a typed Pydantic schema. So it's not just one-shot, there's real back-and-forth.

## Setup

```bash
pip install -r requirements.txt
```

Add your Anthropic API key in a `.env` file:

```
ANTHROPIC_API_KEY=your_key_here
```

Then run:

```bash
python client.py server.py
```

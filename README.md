# Self-Hosted AI Agent

A small Python project for experimenting with a self-hosted open-weight language model running on a private cloud VM.

The current version includes a lightweight Python client that sends prompts to a locally hosted Ollama API and returns the model response.

## Current Architecture

```text
Local Python Client
        |
        | HTTP over SSH tunnel
        v
Oracle Linux VM
        |
        v
Ollama
        |
        v
Qwen3 1.7B
```

Ollama is bound to `127.0.0.1:11434` on the VM and is not exposed directly to the public internet.

## Current Features

- Python client for Ollama's `/api/chat` endpoint
- Configurable model and base URL
- HTTP error handling
- Request timeout handling
- Self-hosted Qwen3 1.7B model

## Planned

- Interactive terminal chat
- Conversation history
- Model evaluation scripts
- SQLite persistence
- Tool/function calling
- Agent loop

## Security

This repository intentionally excludes:

- Cloud credentials
- SSH private keys
- Public server IP addresses
- API tokens
- `.env` files
- Private logs or data

## Setup

Install dependencies:

```bash
pip install -r requirements.txt
```

Make sure Ollama is running and the configured model is available.

By default, the client connects to:

```text
http://127.0.0.1:11434
```

If Ollama is running on a remote VM, an SSH tunnel can be used to forward the local port securely.

## Status

Early development. Version 0.1 currently focuses on reliable model communication before adding agent features.
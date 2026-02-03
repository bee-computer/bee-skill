---
name: bee-cli
description: "Interact with Bee wearable AI data using the bee CLI tool. Use this skill when the user wants to: (1) Access or export their Bee data (facts, todos, conversations, daily summaries), (2) Sync Bee data to local markdown files, (3) Manage personal facts or todos from Bee, (4) Search through captured conversations, (5) Work with data from the Bee wearable device."
---

# Bee CLI

CLI client for Bee - the wearable AI that captures conversations and learns about you.

## Installation

Check if `bee` CLI is installed:
```bash
bee --version
```

If not installed, download from https://github.com/bluush-co/bee-cli/releases/latest

Select the binary for the current platform:
- macOS ARM: `bee-darwin-arm64`
- macOS Intel: `bee-darwin-amd64`
- Linux: `bee-linux-amd64`
- Windows: `bee-windows-amd64.exe`

Download and make executable:
```bash
# Example for macOS ARM
curl -L -o bee https://github.com/bluush-co/bee-cli/releases/latest/download/bee-darwin-arm64
chmod +x bee
sudo mv bee /usr/local/bin/
```

The binary can be used directly without additional installation steps.

## Authentication

Check authentication status:
```bash
bee status
```

If not authenticated, initiate login:
```bash
bee login --agent
```

This returns a URL. Provide the URL to the user and instruct them to open it in their browser to complete authentication. Wait for confirmation before proceeding with other commands.

## Commands

### Sync Data to Markdown

Export all Bee data to local markdown files:
```bash
bee sync
```

Options:
- `--output <dir>` - Output directory (default: ./bee-data)
- `--depth <n>` - How far back to sync

### Facts

List personal facts:
```bash
bee facts list
```

Create a fact:
```bash
bee facts create --text "I prefer morning meetings"
```

Update a fact:
```bash
bee facts update <id> --text "Updated fact text"
```

Delete a fact:
```bash
bee facts delete <id>
```

### Todos

List todos:
```bash
bee todos list
```

Create a todo:
```bash
bee todos create --text "Buy groceries"
```

Update a todo:
```bash
bee todos update <id> --text "Updated todo" --completed
```

Delete a todo:
```bash
bee todos delete <id>
```

### Conversations

List conversations:
```bash
bee conversations list
```

View a specific conversation:
```bash
bee conversations show <id>
```

### Daily Summaries

View daily activity summaries:
```bash
bee daily
```

Options:
- `--date <YYYY-MM-DD>` - View specific date

## Common Workflows

### Export All Data for AI Context

Sync everything to markdown for use with other AI tools:
```bash
bee sync --output ./my-bee-data
```

This creates markdown files for facts, todos, daily summaries, and conversation transcripts.

### Quick Personal Data Check

```bash
bee facts list
bee todos list
bee daily
```

### Search Through Conversations

List recent conversations and view details:
```bash
bee conversations list
bee conversations show <conversation-id>
```

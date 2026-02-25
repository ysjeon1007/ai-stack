# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

ai-stack is a Claude Code integration hub that connects AI tools and automation services. Currently integrates with n8n workflow automation via MCP (Model Context Protocol) and provides n8n-specific skills for Claude Code.

## Stack Components

- **n8n-mcp**: MCP server that connects Claude Code to an n8n instance (installed via npx)
- **n8n-skills**: Git submodule with 7 Claude Code skills for n8n workflow development
  - Expression Syntax, MCP Tools Expert, Workflow Patterns, Validation Expert
  - Node Configuration, Code JS, Code Python

## Environment Setup

### Required
- Node.js v18+
- n8n instance with API access

### Environment Variables
The `.mcp.json` uses `${VAR}` syntax which reads from **shell environment variables** (not `.env` file).

Add to `~/.zshrc`:
```bash
export N8N_API_URL="https://your-n8n-instance.com/api/v1"
export N8N_API_KEY="your-api-key"
```

Then run `source ~/.zshrc` and restart Claude Code.

### After Cloning
```bash
git submodule update --init
```

## MCP Tools (n8n-mcp)

When the n8n-mcp server is connected, the following tools become available:
- Workflow management (list, create, update, delete, activate/deactivate)
- Execution management (list, get, run workflows)
- Node/credential discovery

Verify connection: run `/mcp` in Claude Code to check n8n-mcp server status.

## Important Notes

- `.env` is gitignored — use `.env.example` as reference
- n8n-skills is a git submodule — use `git submodule update --init` after clone
- First `npx n8n-mcp` run may take 10-30s to download the package

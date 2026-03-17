# Code-Graph-RAG — Graph-Based RAG for Codebases

**Repo:** https://github.com/vitali87/code-graph-rag
**License:** MIT
**Status:** Bookmarked — install when codebase complexity warrants it

## Overview

Graph-based RAG system that parses multi-language codebases using Tree-sitter, builds knowledge graphs in Memgraph, and enables natural language querying of code structure and relationships.

## Key Features

- Tree-sitter AST parsing → Memgraph knowledge graph
- Natural language queries ("what functions call UserService.create_user?")
- Semantic code search via UniXcoder embeddings
- Multi-language: Python, TypeScript, JS, Rust, Go, Java, C++, and more
- MCP server for Claude Code integration
- Real-time graph updates (watches repo for changes)
- Code editing capabilities with AST-based targeting
- Runs locally (Docker + Memgraph)

## Requirements

- Docker & Docker Compose (Memgraph)
- Python 3.12+, uv package manager
- cmake, ripgrep
- LLM for Cypher generation: Ollama (local), Google Gemini, or OpenAI

## Install

```bash
git clone https://github.com/vitali87/code-graph-rag.git
cd code-graph-rag
uv sync --extra treesitter-full
docker-compose up -d
```

## Claude Code MCP Setup

```bash
claude mcp add --transport stdio code-graph-rag \
  --env TARGET_REPO_PATH=/path/to/project \
  --env CYPHER_PROVIDER=ollama \
  --env CYPHER_MODEL=codellama \
  -- uv run --directory /path/to/code-graph-rag code-graph-rag mcp-server
```

## Why It Fits

- Complements 5-tier memory (memory = decisions/notes, this = code structure)
- MCP server means Claude Code gets a structured map of code relationships
- M4 Max can run Memgraph + Ollama locally
- Real value on larger codebases (DealLens, future projects)

## When to Install

When DealLens or another project gets complex enough that grep/file reads aren't cutting it for navigating code relationships.

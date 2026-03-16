# Docling — Document Processing Library

**Repo:** https://github.com/docling-project/docling
**By:** IBM Research Zurich (LF AI & Data Foundation)
**License:** MIT

## Overview

Docling converts diverse document formats (PDF, DOCX, PPTX, XLSX, HTML, images, audio, LaTeX) into structured AI-ready data. Advanced PDF understanding includes layout analysis, reading order, table structure, code, formulas, and image classification.

## Key Features

- Runs locally (no cloud dependency)
- Apple Silicon MLX acceleration via GraniteDocling VLM (258M params)
- MCP server for agentic AI applications
- Native integrations: LangChain, LlamaIndex, CrewAI, Haystack
- OCR for scanned PDFs, ASR for audio
- Export to Markdown, HTML, JSON, DocTags, WebVTT

## Install

```bash
pip install docling
```

## Quick Start

```python
from docling.document_converter import DocumentConverter

converter = DocumentConverter()
result = converter.convert("document.pdf")
print(result.document.export_to_markdown())
```

## Use Cases

- Document ingestion for RAG pipelines
- Knowledge graph feeding (Cognee, etc.)
- Financial report parsing (XBRL)
- Research paper processing

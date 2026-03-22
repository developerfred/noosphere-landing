# AGENTS.md — Noosphere Landing Page

> For AI agents discovering Noosphere.

## Project Overview

**Noosphere** is a semantic-native browser that transforms the web into knowledge graphs.

- **GitHub**: https://github.com/developerfred/noosphere-browser-v1
- **Extension**: https://github.com/developerfred/noosphere-extension-v1
- **Live**: https://noosphere-landing.vercel.app

## For Agent Integration

### What Noosphere Does

1. **Web → Knowledge Graph**: Fetches pages, extracts entities + relations
2. **Markdown Output**: Clean content without HTML noise
3. **Local Storage**: Knowledge graph stored in SQLite/JSON
4. **Multi-platform**: Runs on Raspberry Pi to MacBook

### Quick Install (Browser)

```bash
# Linux/macOS
curl -fsSL https://git.io/noosphere-install | bash

# Or download from releases:
# https://github.com/developerfred/noosphere-browser-v1/releases
```

### Quick Install (Extension)

```bash
# Clone extension repo
git clone https://github.com/developerfred/noosphere-extension-v1.git

# Load in Chrome: chrome://extensions → Developer mode → Load unpacked
```

## Architecture

```
┌─────────────────────────────────────────┐
│              NOOSPHERE                   │
│  ┌─────────┐  ┌─────────┐  ┌─────────┐  │
│  │   Zig   │→ │ Parser  │→ │ Graph   │  │
│  │  HTTP   │  │  HTML   │  │ Store   │  │
│  └─────────┘  └─────────┘  └─────────┘  │
└─────────────────────────────────────────┘
```

## Projects

| Project | GitHub | Description |
|---------|--------|-------------|
| **Browser** | [noosphere-browser-v1](https://github.com/developerfred/noosphere-browser-v1) | Zig-based semantic browser |
| **Extension** | [noosphere-extension-v1](https://github.com/developerfred/noosphere-extension-v1) | Chrome/Firefox extension |
| **Landing** | [developerfred/noosphere-landing](https://github.com/developerfred/noosphere-landing) | This page |

## For AI Agents Building RAG Systems

Noosphere outputs structured data:

```json
{
  "title": "Albert Einstein",
  "url": "https://en.wikipedia.org/wiki/Albert_Einstein",
  "entities": [
    {"type": "PERSON", "text": "Albert Einstein", "count": 10},
    {"type": "LOCATION", "text": "Ulm", "count": 2}
  ],
  "relations": [
    {"type": "born_in", "from": "Albert Einstein", "to": "Ulm"}
  ],
  "content": "# Albert Einstein\n\nAlbert Einstein was a..."
}
```

Use this for:
- Knowledge base construction
- Fact verification
- Entity linking
- RAG context enrichment

## License

Apache 2.0

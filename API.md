# Google Drive MCP Tool Reference

Reviewed against `index.ts` on 2026-03-20.

## Snapshot

- Transport: MCP over stdio
- Runtime: Node.js + `@modelcontextprotocol/sdk`
- Backing API: Google Drive v3
- Auth: OAuth desktop flow using Drive read-only scope

## Tools

| Tool | Input | Purpose |
|---|---|---|
| `gdrive_search` | `{ "query": string }` | Full-text search Google Drive |
| `gdrive_read_file` | `{ "file_id": string }` | Read file contents by file id |

## Resource Contract

| Operation | Contract |
|---|---|
| List resources | Returns `gdrive:///{fileId}` resources with `mimeType` and `name` |
| Read resource | Accepts `gdrive:///{fileId}` and returns converted file contents |

## File Conversion Rules

| Drive type | Output |
|---|---|
| Google Docs | Markdown |
| Google Sheets | CSV |
| Google Slides | Plain text |
| Google Drawings | PNG |
| Text / JSON files | UTF-8 text |
| Other binary files | Base64 |

## Accuracy Notes

- The README was already broadly accurate.
- This file exists to provide a shorter canonical tool/resource contract without the setup tutorial.

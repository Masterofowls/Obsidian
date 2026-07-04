---
aliases: [file-editing, text-editor, how-editing-works]
tags: [software, file-editing, editor, text]
cssclass: wiki
---
# How File Editing Works

## Overview
File editing is the process of **modifying data stored on a disk**.

## How It Works
1. Editor opens a file → reads data into **RAM**
2. User makes changes in the editor's **buffer** (memory)
3. On save → editor writes modified buffer back to disk
4. File system updates the file's metadata (size, timestamp)

## Text Editors vs Word Processors
| Type | Stores | Example |
|------|--------|---------|
| Text editor | Plain text | Notepad, VS Code, Vim |
| Word processor | Rich text + formatting | Word, Google Docs |

## Encoding
- **ASCII**: 7-bit, 128 characters
- **UTF-8**: Variable-length, supports all Unicode characters
- **UTF-16**: 2 or 4 bytes per character

## Related
- [[Wiki\Hardware\Storage|Storage]]

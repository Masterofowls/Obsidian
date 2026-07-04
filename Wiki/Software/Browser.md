---
aliases: [browser, web-browser, how-browser-works]
tags: [software, browser, web, rendering]
cssclass: wiki
---
# How Browsers Work

## Overview
A web browser **fetches, parses, and renders** web pages from the internet.

## How It Works

### 1. DNS Resolution
- URL → IP address lookup
- `example.com` → `93.184.216.34`

### 2. Connection
- TCP three-way handshake with the server
- TLS handshake for HTTPS

### 3. HTTP Request
- Browser sends GET request for the page

### 4. Parse HTML
- Browser builds the **DOM** (Document Object Model) tree
- Encounters `<link>`, `<script>`, `<img>` tags → fetches those too

### 5. Parse CSS
- Builds the **CSSOM** (CSS Object Model)

### 6. Render Tree
- Combines DOM + CSSOM
- Determines what's visible and where

### 7. Layout
- Calculates exact positions and sizes of every element

### 8. Paint
- Draws pixels to the screen

### 9. Composite
- Layers are combined and displayed

## Related
- [[Wiki\Software\CSS|CSS]]
- [[Wiki\Software\Rendering|Rendering]]

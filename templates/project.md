<!--
  Reference template for a tool / project.
  Copy this into content/projects/<slug>.md and edit.
  URL will be /projects/<slug>/
-->

---
title: "tool-name"                         # required — keep lowercase/kebab-case; shown on /projects/ and home
date: 2026-04-20                           # required — date of initial publish
draft: true                                # set false when ready
tags: ["go", "recon"]                      # optional — language + category
summary: >                                 # required for home page display
  Single-line description: what the tool is and what it does. Shown on
  /projects/ and on the home page. Keep under ~200 chars.
repo: "https://github.com/you/tool-name"   # optional — link to source
---

One-paragraph intro. What the tool does, who it's for, why it exists in
one breath.

## What it does

- Main capability one
- Main capability two
- Something it explicitly does not do (manages expectations)

## Usage

```bash
tool-name -d target.com -o results.json
tool-name --help
```

Describe flags briefly:

- `-d` target domain
- `-o` output file (JSON)
- `-c` concurrency (default: 50)

## Why this exists

A short paragraph on the problem it solves. If it replaces a workflow
that used five other tools, say so. If it's a re-implementation of
something that did too much, say that too.

## Install

```bash
go install github.com/you/tool-name@latest
```

Or grab a pre-built binary from the [releases page](https://github.com/you/tool-name/releases).

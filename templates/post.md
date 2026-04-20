<!--
  Reference template for a note / article / write-up.
  Copy this into content/posts/<slug>.md and edit.
  URL will be /posts/<slug>/
-->

---
title: "Title of the post"       # required
date: 2026-04-20                  # required — YYYY-MM-DD or full RFC 3339
draft: true                       # set false (or remove) when ready to publish
tags: ["tag-one", "tag-two"]      # optional — used for /tags/ and related
summary: >                        # optional but recommended
  One-line description used on the home page, in the RSS feed, and as the
  og:description meta tag. Keep it around 140–200 characters.
---

Opening paragraph. This is the lead. State the claim or the question
upfront — one idea per sentence, nothing held in reserve.

## First section

Regular prose paragraphs. **Bold** for key terms the first time you
introduce them, *italic* for titles or soft emphasis, `inline code`
for identifiers, commands, and flags.

### A subsection

Lists work as expected:

- First item
- Second item, with `--some-flag` in the middle
- Third

Ordered lists when order matters:

1. Step one
2. Step two
3. Step three

Fenced code blocks — add a language tag for syntax highlighting:

```bash
nmap -sC -sV -oA recon target.example.com
```

```go
func main() {
    fmt.Println("hello")
}
```

> Blockquotes pull out a single sentence worth remembering. Use sparingly
> or they lose their weight.

Tables if you need them:

| column a  | column b      | column c |
|-----------|---------------|----------|
| value 1   | something     | `flag`   |
| value 2   | something else| `flag`   |

---

Horizontal rules separate major sections when another H2 would feel too
heavy.

## Wrapping up

A short paragraph saying what you learned or what comes next. Link out
to anything worth following: another [post]({{< ref "other-post" >}}),
an [external resource](https://example.com/), a repo.

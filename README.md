# Cantonese Wiki

An LLM-maintained wiki of spoken Cantonese for daily life, built on the pattern in
[llm-wiki.md](llm-wiki.md). The LLM writes and maintains every page; I supply the phrases,
the sources, the questions and the judgment.

Jyutping, traditional characters, spoken Hong Kong Cantonese.

## How to drive it

Open Claude Code in this directory. The conventions live in
[CLAUDE.md](CLAUDE.md) — that file is what makes the agent a disciplined wiki maintainer
rather than a chatbot.

**Capture** — the main one. Type a phrase you heard. That's the whole interface:

```
搞掂
```

It gets verified, filed into the right page in the canonical format, cross-linked, and
logged.

**Other operations** — just ask:

- *"what are my options for softening a request?"* → a **query**, answered with citations
  and offered back as a page
- *"ingest the article in raw/"* → an **ingest**
- *"regenerate review"* → a **review** pass over `review.md`
- *"lint the wiki"* → contradictions, duplicates, orphans, unverified entries

Say *"I used 囉 today"* or *"that one's solid now"* to move an entry's status along.

## Layout

| Path | |
|---|---|
| `index.md` | Catalog of every page. Read first. |
| `log.md` | Append-only timeline. |
| `me.md` | Level, goals, weak spots. |
| `review.md` | What's stalled, in flight, never used. Regenerated, not edited. |
| `raw/` | Immutable sources. The LLM reads, never modifies. |
| `wiki/` | Everything the LLM writes. |

## Obsidian

Open this folder as a vault. Set Settings → Files and links → Attachment folder path to
`raw/assets/` so clipped images land somewhere stable.

Pages use `[[wikilinks]]` and YAML frontmatter, so graph view and Dataview both work.

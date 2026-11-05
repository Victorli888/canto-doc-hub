# Cantonese Wiki

An LLM-maintained wiki of spoken Cantonese for daily life, built on the pattern in
[llm-wiki.md](llm-wiki.md). The LLM writes and maintains every page; I supply the phrases,
the sources, the questions and the judgment.

Jyutping, traditional characters, spoken Hong Kong Cantonese.

## How to drive it

Open Claude Code in this directory. The conventions live in
[CLAUDE.md](CLAUDE.md) — that file is what makes the agent a disciplined wiki maintainer
rather than a chatbot.

**Wish** — the main one. Dump a moment where you didn't have the phrase. No format:

```
wanted to tell the waiter the soup was too salty
coworker asked if I'd finished, I said 我已經完成咗 — felt stiff
```

You get the natural version back. It's verified, filed by situation with the moment
attached, and logged.

**Capture** — a phrase you heard. Just type it: `搞掂`.

**Away from the desk** — add a line to `inbox.md` (Obsidian mobile works). Next session:
*"process inbox"*.

**Practice** — *"practise"* or *"practise taxis"*. Claude replays your saved moments as
short role-plays. This is what moves entries from `new` toward `active`.

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

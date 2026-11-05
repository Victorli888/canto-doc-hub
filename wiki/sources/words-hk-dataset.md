---
type: source
tags: [cantonese, meta/tooling, source]
raw: raw/words-hk/
created: 2026-11-04
updated: 2026-11-04
---

# Source — the local words.hk and rime-cantonese datasets

Raw files: `raw/words-hk/` · Lookup tool: `bin/canto`

Not a source of phrases. This is the **reference layer** — the thing hard rule 1 checks
against. Before this existed, verifying one reading meant booting a headless browser and
loading a dictionary page, about fifteen seconds a word once the browser was warm and two
minutes before that. The first ingest ([[describing-my-job-dump]]) needed roughly twenty
lookups and spent almost all of its time on transport rather than on judgment.

Now:

```
$ bin/canto 軟件 訂單
軟件
  jyun5 gin2  (primary)   [rime/words]
  jyun5 gin6   [rime/words]
  [名詞]
  電腦運行嘅程式（量詞：個／隻） // software; a piece of software
訂單
  deng6 daan1   [rime/words]
  [名詞 · unpublished]
  訂購貨物嘅申請 （量詞：張／份） // purchasing order
```

Instant, offline, and it answers the two questions that actually come up: *what is the
reading* and *is this word real*.

## What's in it

| File | What | Licence |
|---|---|---|
| `jyut6ping3.chars.dict.yaml` | single characters → Jyutping, with weights | CC BY 4.0 |
| `jyut6ping3.words.dict.yaml` | ~100k words → Jyutping | CC BY 4.0 |
| `jyut6ping3.phrase.dict.yaml` | multi-word phrases → Jyutping | CC BY 4.0 |
| `dict.json` | 51,899 words.hk entries: definitions, part of speech, register labels, example sentences | Non-Commercial Open Data License |

The rime tables are [rime-cantonese](https://github.com/rime/rime-cantonese), maintained
by CanCLID, version 2026.08.10. `dict.json` is the words.hk database as parsed and
redistributed by [wordshk-tools](https://github.com/AlienKevin/wordshk-tools).

## The two things that make it better than the website

**1. It has the entries the website withholds.** words.hk hides unpublished entries behind
"「X」is not ready yet — you will have to log into words.hk". During the first ingest that
blocked 落單, 訂單, 工地, 沙井, 擋土牆, 化糞池, 程式 and 㗎 — eight of about fifteen
lookups, every one of which is present in `dict.json` with a full definition. `bin/canto`
marks them `unpublished` so the lower confidence is visible rather than silent.

**2. Register labels are a field.** `dict.json` carries words.hk's own labels — 俚語
(slang), 粗俗 (vulgar), 書面語 (written) and so on. Register is the second thing this wiki
weights ([[me]]), and until now it was being argued from feel. It is now queryable.

## Caveats that matter

**Absence is not evidence.** 渠管, 預製 and 平台 are all real, all verified elsewhere, and
all missing from the rime tables. A blank result means look it up on the web, not that the
word is wrong. `bin/canto` says so rather than printing nothing.

**The chars table puts reduced particle forms first.** 㗎 lists `ga3` ahead of `gaa3`, 啦
lists `la1` ahead of `laa1`. Both are genuinely said — Cantonese particles do shorten in
running speech — but this wiki writes the citation form, and taking the first line blindly
would have put `ga3` into the 㗎 entry on [[final-particles]]. `bin/canto` prints a warning
when it sees the pair. For anything longer than one character, prefer the words and phrase
tables.

**A character lookup can answer about a different word entirely.** The second ingest
needed 解釋吓. Looking up the character 吓 gives `haa1` / `haa2` — which is right, for the
interjection "huh?". The verb suffix is `haa5`, filed by words.hk under 下 but written 吓
in its own word entries (試吓 si3 haa5, 郁吓 juk1 haa5). Same shape as the particle trap
above and more dangerous, because the reading returned is not wrong, it just belongs to
another word. For a suffix or a particle, look up a whole word that contains it.

The same pair-of-characters problem runs the other way with 咁 / 噉: words.hk writes the
manner word (好似…咁) as 噉 gam2 and keeps 咁 for the degree word gam3 (得咁少), while
everyday Hong Kong writing uses 咁 for both.

**This replaces the easy half of verification, not the hard half.** It answers "what is the
reading of this word". It does not answer "would a Hong Kong speaker say this whole
sentence", which is where [[describing-my-job-dump]]'s three register calls sat and where
rule 1 still bites. Composed Cantonese still gets `⚠️ unverified`.

**Not current forever.** `bin/canto --fetch` re-downloads everything. Worth doing every few
months; the correction trail in [[describing-my-job-dump]] shows the kind of thing that
moves.

## Licence and why the blobs are gitignored

The four data files total about 42MB and are not committed — `.gitignore` excludes them and
`bin/canto --fetch` restores them in under a minute. Reasoning: a 34MB JSON blob in git
history is permanent and unprunable, the data is one command away, and the
Non-Commercial Open Data License attaches notice obligations to *distribution* that are
better not triggered by a notes repo. The licence texts themselves are committed.

- rime-cantonese: **CC BY 4.0** — © CanCLID, https://github.com/rime/rime-cantonese
  (`jyut6ping3.maps` is ODbL-1.0 and was not downloaded.)
- words.hk: **Non-Commercial Open Data License** — © 2015-2025 Hong Kong Lexicography
  Limited, https://words.hk/base/hoifong/ · credits list at https://words.hk/base/about/

Both permit this use. words.hk's licence forbids commercial use, which a personal study
wiki is not — but it is worth knowing before any of this gets published.

## See also

[[describing-my-job-dump]] · [[explaining-finances-to-mom-dump]] · [[CLAUDE]] (hard rule 1) · [[tone-sandhi]]

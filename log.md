---
type: meta
tags: [cantonese, meta/log]
created: 2026-11-01
updated: 2026-11-04
---

# Log

Append-only. Newest at the bottom. `grep "^## \[" log.md | tail -5` for recent activity.

Verbs: `wish` · `capture` · `practice` · `status` · `ingest` · `query` · `review` · `lint` · `meta`

## [2026-11-01] meta | wiki initialized
Built the skeleton from [[llm-wiki]]: [[CLAUDE]] schema, [[index]], [[log]], [[me]],
[[review]]. Decisions locked in: Jyutping only with tone numbers, traditional characters,
spoken HK Cantonese over written Standard Chinese, phrases as H3 blocks inside situation
pages rather than one page per phrase, in-wiki review via per-entry status, Obsidian
wikilinks plus frontmatter. No Anki export and no search tooling — `index.md` is the
retrieval mechanism until it isn't.

## [2026-11-01] meta | seeded 20 entries across 4 pages
[[final-particles]] (8), [[softening-and-politeness]] (6), [[work-small-talk]] (6),
[[lazy-sounds]] (6 mergers, not phrase blocks), [[what-works]] (structure only).
All entries carry `source: seed` and are deletable as a block. 喎 wo3/wo5 and 開會
hoi1 wui6-2 were verified against Wiktionary, CantoWords and the EdUHK sentence-final
particle paper rather than asserted from memory.

## [2026-11-01] lint | corrected 囉, verified at seed time
First lint pass over the fresh skeleton: 0 orphans, 20/20 blocks carry a Status line, all
wikilinks resolve (remaining grep hits are inside code blocks). One real error found and
fixed: [[final-particles]] 囉 had collapsed lo1 (stating the obvious) and lo3 (resignation)
into a single lo1 entry, and gave 「冇辦法囉」the wrong tone. Split per jyutping.org and
Wiktionary. Both two-particle characters (囉, 喎) now cross-reference each other.

## [2026-11-02] meta | wish-first redesign
Made **Wish** the primary operation: Victor dumps a moment he lacked a phrase for, the
natural version is found, verified, and filed by situation with a new **Moment** field.
Added Process inbox, Practice and Status operations, and `inbox.md`. Pages are now created
without asking when no situation fits. Rule 1 extended to composed sentences. Review gains
"Moments that keep coming back".

## [2026-11-04] ingest | "Describing My Job" vocab dump → [[describing-my-job]], [[software-and-tech]], [[concrete-and-construction]]
First ingest. Raw at `raw/2026-11-04-describing-my-job.md`, summary at
[[describing-my-job-dump]]. Fanned out to a new situation page (8 entries), two new vocab
pages (41 terms) and a 㗎 entry on [[final-particles]]. Created [[tone-sandhi]] because
the 件 → gin6-2 changed tone now has three instances plus 開會 wui6-2 already in the wiki.
Five Jyutping corrections against the source: 軟件 gin6→gin6-2, 訂單 ding6→deng6, 組件
gin2→gin6-2, 生產 saang1→sang1, 倒石屎 dou3→落石屎 lok6. Three register calls flagged as
judgment: 寫程式→寫code, 公司整產品→公司做產品, and the 開發…個系統 register clash.
[[me]] updated with the job and a new weak spot (reaching for dictionary tones).

## [2026-11-04] ingest | words.hk + rime-cantonese datasets → [[words-hk-dataset]], `bin/canto`
Pulled the reference layer local, because [[describing-my-job-dump]] spent almost all its
time on transport: ~20 lookups, each a headless-browser page load, ~2 min of that just
booting the browser. Now `bin/canto 軟件 訂單` answers offline.
`raw/words-hk/`: rime-cantonese chars/words/phrase tables (CC BY 4.0, v2026.08.10) for
Jyutping, and words.hk's 51,899 entries via wordshk-tools (Non-Commercial Open Data
License) for definitions, part of speech and register labels. ~42MB, gitignored;
`bin/canto --fetch` restores. Licence texts and `raw/words-hk/NOTICE.md` are committed.
Two wins over the website: it has the entries words.hk withholds as unpublished (8 of the
first ingest's 15 lookups were blocked that way, all present here), and register labels
are a queryable field rather than a judgement call. It also independently confirmed all
five corrections from the first ingest — including 生產 sang1 caan2, which had rested on
Wiktionary alone.
Two caveats documented and guarded in the script: absence from the tables is not evidence
(渠管, 預製, 平台 are real and missing), and the single-character table lists reduced
particle forms ahead of citation forms (㗎 ga3 before gaa3) — `bin/canto` warns on the pair.

## [2026-11-04] meta | hard rule 1 checks the local dataset first
Rewrote rule 1's search step in [[CLAUDE]]: `bin/canto` before the web, then WebFetch for
static dictionary pages, then a search engine only for usage frequency. Added `raw/words-hk/`
and `bin/canto` to the structure map. The rule's substance is unchanged — verify, don't
assert — only the cheapest path to it.

## [2026-11-04] ingest | "Explaining Finances to Mom" → [[talking-about-money]], [[banking-and-finance]]
Raw at `raw/2026-11-04-explaining-finances-to-mom.md`, summary at
[[explaining-finances-to-mom-dump]]. 9 entries on a new situation page, a 35-term vocab
page, and 呀嘛 added to [[final-particles]]. One Jyutping correction in a long sheet:
呀嘛 aa3 maa3 → **aa6 maa5**, both syllables.
Two things the sheet got righter than they looked: 戶口 over 帳戶 (words.hk's own
definitions use 帳户, so the written pull is real), and 「冇唔見呀嘛?」, which reads like a
learner's double negative but matches words.hk's third sense of 呀嘛 exactly — confirming
the worst case hasn't happened, with a negative sentence.
Recorded three orthography notes rather than corrections: 解釋下 → 解釋吓 (reading haa5
right, character per the wiki's existing 傾吓), 咁 vs 噉 for gam2/gam3, and 獨立 laap6/lap6.
Noted one gap in the finance content: Roth earnings also need the 5-year rule, not just age.
First ingest using `bin/canto`. Verification took ~90 seconds against ~15 minutes for
[[describing-my-job-dump]], and it resolved a question the browser could not: whether the
wiki's existing 傾吓 king1 haa5 was wrong. It is right — standalone 吓 is haa1/haa2, the
interjection, a different word. That trap is now documented in [[words-hk-dataset]].

## [2026-11-05] wish | describing how I guide AI to write code → [[describing-my-job]]
4 entries + 1 composite example: 叫AI寫code, 我負責判斷AI負責寫, AI寫完我自己check同改,
用AI快好多/慳好多時間. All composed from verified chunks and marked ⚠️ unverified — the
pairing of 叫 with AI, and 自己check over 校對 as the natural register for code review
(same judgment shape as 寫code over 寫程式). 5 new terms added to [[software-and-tech]]:
人工智能, 判斷, 執行, 改, 架構.

## [2026-11-05] meta | added Practice — phrase bank mode
Scene-replay was the only Practice mode on file, and Victor asked for a different shape:
a bank of phrasings per side of an exchange, for building vocabulary breadth rather than
producing one line. Documented as a sibling mode under Practice in [[CLAUDE]], same
bookkeeping (new → learning, log line) but variants are filed only if he reacts to one —
the drill itself doesn't write to any page.
## [2026-11-09] wish | full account breakdown, WF CD+checking + Wealthfront HYSA/Roth/ETFs → [[talking-about-money]], [[banking-and-finance]]
## [2026-11-11] meta | Practice (scene-replay) default is now a full read-through script + vocab table, not stop-and-wait
## [2026-11-11] practice | 5 entries, [[talking-about-money]]
## [2026-11-11] practice | 6 entries, full-picture scene (two banks, CD, HYSA, Roth, ETFs) → [[talking-about-money]]
## [2026-11-12] capture | 畀你平時用嘅 (3 phrasings, replaces 日常用嗰筆) → [[talking-about-money]], [[banking-and-finance]]
## [2026-11-12] ingest | everyday-money phrasing feedback → [[everyday-money-phrasing-feedback]], 擺咗落定期存款 → 擺咗做定期, [[talking-about-money]], [[banking-and-finance]]
## [2026-11-12] practice | 13 entries (all of the page), 17-sentence dinner scene; fixed 方法 fong3 → fong1 faat3 in the composite → [[describing-my-job]]
## [2026-11-17] wish | life is busy: 2 cats, fussy new dog, 8h office, gym/cook/clean → new [[everyday-life]] (13 entries)
## [2026-11-17] practice | 12 entries, three scenes (catching up, the fussy dog, turning down dinner) → [[everyday-life]]

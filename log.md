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

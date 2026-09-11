# Positions files: what's in this folder

Last updated: 2026-09-10

There are five files covering positions, split into two tiers: identification (does the tool recognize this raw term as a known position, and what does it match to) and typology (for positions we're confident about, what sector and occupational level they belong to). A position can be identified without being typed, so the typology files only ever cover a subset of the terms in the identification files. There's a fifth file that's neither: a bilingual reference dictionary you consult by hand rather than one the matching script runs against.

## Identification tier

### Index_Positions_Zh_Corr.csv (1,419 rows)

The Chinese-language position reference. Columns: `Position_Zh_Srce` (the term as found in Chinese historical documents, late Qing and Republican period) and `Length` (character count of the term, kept from the original file). No typology attached. Does not include Qing administration positions, which live in a separate file (CDEQ_Positions).

### Index_Positions_Eng_Corr.csv (3,587 rows)

The English-language position reference. Columns: `Position_Eng_Srce` (the term) and `Source` (which of the two source works it came from: the Biographical Dictionary of Republican China, or the Asia Directory & Chronicle, 1863-1941). No typology attached.

## Typology tier

### Index_Positions_Typology_Corr.csv (532 rows)

English-language positions classified by sector and occupational level. Built by merging two source typologies that turned out to be the same underlying classification system applied to two overlapping term lists: 309 terms came from both, 97 from the INSEE/Pinot-based typology alone, 126 from the SMC occupation list alone (the `Typology_Source` column records which).

Columns: `Position_Eng_Srce` (the term), `Sector_1` / `Sector_2` (broad sector, two levels), `Occupation_Category` (socio-professional category, e.g. "Professionals and senior executives"), `Occupation_Subcategory` (a finer occupational grouping), `Occupation_Detail` (the finest level, only populated for the 406 terms that came from the INSEE/Pinot typology, the "Both" and "Typo_positions" rows in `Typology_Source`, since the SMC list didn't go that deep), and `Typology_Source`.

### Index_typo_positions.csv (406 rows)

The original INSEE/Pinot-based typology this was built from: positions from the Shanghai International Settlement census surveys and Rotary Club research, classified against the 1954 INSEE typology as supplemented by J.L. Pinot's dissertation. This is the source file for the `Occupation_Detail` column above and for provenance if you need to trace a classification back to its origin; for matching purposes, use `Index_Positions_Typology_Corr.csv` instead, since it also covers the terms that only appear in the SMC list.

## Reference dictionary

### Index_Positions_Bilingual.csv (649 rows)

A Chinese-to-English lookup, not wired into the automated matching the way the other four files are, because the same Chinese term can genuinely take more than one correct English translation depending on context (中央執行委員會常務委員 and 3 comparable terms in this file each carry two accepted English forms). Columns: `Position_Zh_Srce`, `Position_Eng`, `Year`, `Source`, and `Eng_Source`, which tracks where each translation came from:

- `1936 dictionary` (432 rows): 中國徵信所. 上海工商人名錄. 上海: 美華書館, 1936.
- `Customs Service List 1947` (144 rows): Service List 海關職員提名錄, 1947, Chinese Maritime Customs. Chinese Maritime Customs Service ranks (稅務司, 總巡, 監察長, and similar), a different register from the 1936 commercial directory.
- `Claude Sonnet 5` (73 rows): translations supplied where the 1936 dictionary entry had a Chinese term but no English gloss. Treat these as a first draft; a handful were flagged as lower-confidence at the time (坐辦, 會辦, 技正, 審檢處技士, 民政長, 署理, 獨資經營) and are worth a second look.

## How they fit together

To normalize a dataset's raw position column, run `Positions_Zh` or `Positions_Eng` against the relevant identification file first, to flag/confirm known terms. Then run `Positions_Typology` on the same column to pick up sector and occupation level wherever it's known; most identified terms won't have one, which is expected, not an error. `Index_Positions_Bilingual.csv` stays outside this pipeline, for translating a Chinese term by hand when you need an English gloss to work with.

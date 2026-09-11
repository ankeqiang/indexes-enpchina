# IndexesEnp
Authority and reference indexes built for the ENP-China project (Christian Henriot, Aix-Marseille University), used to identify, standardize and geolocate names encountered in Chinese-studies historical sources: people's positions and occupations, institutions, disciplines, degrees, surnames, Shanghai street names, Chinese and US universities, and Chinese administrative geography.

How the files work

Most files here follow the same pattern: a _Srce (or similarly named "source") column holds a name exactly as it appears in a historical document, and a _Strd ("standardized") or equivalent column gives the normalized form to use for matching and analysis. To identify a name from a source, look it up in the relevant _Srce column and read off the standardized value. Some files add further columns: an English gloss, a typology or classification, geocoordinates, or a note on where a correction or translation came from.

A practical note on opening these files: most use a semicolon (;) as the column separator rather than a comma, since several fields contain commas of their own (English glosses, addresses). A few files use a comma instead. If a file opens as a single column in a spreadsheet, try the other separator. Text encoding throughout is UTF-8.

Folder by folder
Appointments

Index_Appointment_Corr.csv (38 rows, comma-delimited): a short list mapping terms describing how someone held a position (代理 Acting, 任命 Appointed, 充 Fill, 兼 Concurrent, and similar) from Chinese to English.

Buildings

Typology_buildings.csv (535 rows, semicolon-delimited): a hierarchical typology of building and land-use categories, from broad manmade-feature classes down through institutional site, building type, and specific use (for example: institutional site > educational facility > school > private school > religious school > kindergarten > buddhist).

Cities

Two reference gazetteers. worldcities.csv (26,568 rows, comma-delimited) is a general-purpose world cities table with coordinates, country, admin region and population. US_State_Codes.csv (53 rows, comma-delimited) maps US state names to their two-letter codes. An existing ReadMe_Cities.rtf describes this folder's original scope in more detail; note that the "US_universities_Locations" file it mentions is now Index_US_universities_cities.csv, in the Universities folder.

Degrees

Typo_degrees_MCBD.csv (89 rows, comma-delimited): a typology of academic degrees, with the expanded English name, a short English form, the Chinese term, and the common acronym (for example "Bachelor of Arts" / "Bachelor" / 學士 / "A.B.").

Disciplines

A two-level typology of academic disciplines and subjects. Index_Disciplines_Corr.csv (3,612 rows, comma-delimited) maps a raw discipline name as found in a source (in both simplified and traditional characters) to an English name and a two-level classification (for example Aeronautical Engineering, under Engineering Sciences, under Engineering); Typo_Disciplines_MCBD.csv (57 rows) lists the classification levels on their own. Index_Disciplines_Corr.csv carries a few stray empty trailing columns on a handful of rows, left over from the source spreadsheet; they can be ignored or dropped. An existing ReadMe_Disciplines.rtf describes the intended structure; it refers to a further bilingual dictionary file ("Discip_MCBD_Join") not currently present in this folder.

Institutions

Index_Institutions_Corr.csv (12,115 rows, comma-delimited): a large correcting index mapping raw institution names as they appear in sources (including OCR artifacts such as leading ㈠ markers) to a standardized name. This is a general-purpose institution list, distinct from the university-specific files in the Universities folder.

MCGD

The Modern China Gazetteer Database: place names and administrative geography for China. MCGD_PRC_V1.csv (2,462 rows) covers present-day PRC administrative divisions with coordinates. MCGD_Rep_V2.csv (1,979 rows, semicolon-delimited) covers Republican-era place names, each with its romanization, province, coordinates, administrative level, and the year the record applies to. Province_RPC.csv, Prov_Name_ID_All.csv and Prov_Zh-Py-Text.csv are smaller province name/ID/romanization lookup tables. The eight Provincial_Capitals_<period>.csv files each give the provincial capitals for a specific historical period, from 1922-28 through 1988-today, since capitals changed along with province boundaries and names. Two existing files, ReadMe_Provinces.rtf and Read_Me_MCGD_Data.rtf, describe the wider MCGD data collection; both refer to larger master files (a full gazetteer of about 464,000 entries and a Chinese-only extraction of about 175,000 entries) that are not included in this repository, likely because of size.

Positions

Identification and classification of occupations and positions found in historical sources, across several files: a bilingual source/English list, an English-side correcting index, and two typology files that classify positions into sectors and occupational categories. See Positions/Positions_README.md for the full description of how these files relate to one another. (A duplicate copy of Index_Disciplines_Corr.csv from the Disciplines folder is also present here; it appears to be misplaced and can be disregarded or removed.)

Shanghai-Streets

Index_Shanghai_Streets.csv (currently around 1,673 rows, comma-delimited): a detailed index of Shanghai street names from the late Qing through the present, tracking each attested name together with its Chinese, pinyin and English forms, the years it was in use, its district, and, where the street was later renamed, the name it became. The same street name can legitimately appear more than once in the source column, either because it was reused for different streets in different districts, or because a street went through more than one rename; both cases have been checked and distinguished from genuine data errors during cleanup.

Surnames

Chinese surname frequency and typology data drawn from the CGED-Q dataset and a 2019 surname list. Surnames_CGED-Q.csv (666 rows, comma-delimited) gives surnames with a count of individuals. Surnames_Zh_2019.csv (557 rows, semicolon-delimited) gives surnames in simplified and traditional characters with length and source. Surnames_Hist_China.csv (1,245 rows, semicolon-delimited, no header row: the columns are surname, length, source), Surnames_Single_Hist_China.csv (811 rows) and Surnames_Compounds_Hist_China.csv (46 rows) break historical surnames down into single-character and multi-character (compound) forms. ReadMe_Surnames.rtf describes the full intended set.

Universities

Two families of files: identifying Chinese institution names on one side (matching a raw Chinese name to a standardized Chinese name and an English name), and locating and geocoding US institutions on the other. See Universities/Universities_README.md for the full description of each file and how they connect.

Provenance

Several of these files were reviewed, corrected, and in places substantially reorganized with the help of Claude (Anthropic) during 2026, working directly from Christian Henriot's own review and historical research. Where a file's own folder has a more detailed README (Positions, Universities), that file documents the specific corrections made and the known open issues. Files without a detailed sub-README have not been changed as part of that review; their content and any existing .rtf notes are as originally deposited, aside from the filename corrections noted above.


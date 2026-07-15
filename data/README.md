# Data

## `team_epas.csv` (included in this repo)

Season-by-season team EPA/play, built directly from `nflfastR` play-by-play data. Used for the Rams/Browns case-study charts.

| Column | Type | Description |
|---|---|---|
| `season` | int | NFL season (2011–2024) |
| `team` | chr | Team abbreviation (32 teams) |
| `epa_per_play` | dbl | Offensive EPA per play for that team-season |

448 rows, 32 teams, 2011–2024.

## `SAL384FinalProjectData.csv` (not included — schema only)

This is the main modeling dataset (146 team-seasons, 2011–2015, 29 teams). It's **not uploaded to this repo** because two of its columns are derived from Spotrac contract/cap data, and Spotrac's terms don't clearly permit redistributing that data even in aggregated/derived form. Everything else in the file would be fine on its own, but since it's one combined table, the whole file stays local.

| Column | Type | Description | Source |
|---|---|---|---|
| `team` | chr | Team abbreviation | — |
| `season` | int | NFL season (base years 2011–2015) | — |
| `qbc` | int (0/1) | Primary QB same as prior season | nflfastR / roster data |
| `hcc` | int (0/1) | Head coach same as prior season | Public coaching records |
| `occ` | int (0/1) | Offensive coordinator same as prior season | Public coaching records |
| `sos` | dbl | Strength of schedule | nflfastR — **computed but not used in the final model specification**; kept in the data, not referenced in `analysis.Rmd` or the report |
| `off_dc` | dbl | Draft capital spent on offensive players (`1/pick_drafted`, summed) | Public draft order |
| `avg_off_age` | dbl | Average age of offensive starters | Public roster data |
| `epa_per_play` | dbl | Offensive EPA per play, that season | nflfastR |
| `epa_volatility_4yr` | dbl | **Outcome variable.** 4-year forward-looking SD of `epa_per_play` | nflfastR (derived) |
| `qb_exp` | int | Primary QB's years of NFL experience (rookie = 0) | Public roster data |
| `rookie_prop` | dbl | Share of cap space spent on rookie players | **Spotrac** |
| `offense_prop` | dbl | Share of cap space spent on all offensive players | **Spotrac** |

# Rookie Contract Allocations and Team Stability in the NFL
Examines whether rookie contract allocation and roster construction decisions relate to NFL offensive volatility 

## Summary of findings

- **Head coach continuity** has the strongest, most consistent relationship with volatility of any variable measured, confirmed by both OLS and robust regression.
- **QB Experience, rookie cap share, and offensive cap share** each show a *concave* relationship with volatility rather than a straight line - teams at the extremes of these variables tend to be more stable than teams in the middl eof the range.
- The interaction between rookie cap share and draft capital (i.e., whether rookie spending is concentrated in a premium pick) is suggestive under OLS but not confirmed by the robust model, so it's treated as a hypothesis rather than an established finding.
- Significant team fixed effects indicate that organizational factors beyond roster construction still shape offensive stability

## Data

Two data sources feed this analysis (see [`data/README.md`](data/README.md) for full column-level documentation):

| File | Included? | Used for | Source |
|---|---|---|---|
|`team_epas.csv`| ✅ | Season-by-season team EPA/play (Case Studies) | `nflfastR`|
|`SAL384FinalProjectData.csv`| ❌ (schema documented)| Main modeling dataset (146 team-seasons, 2011-2015 base years) | `nflfastR` + Spotrac (contract/cap data) |

- Play-by-play / EPA data: [`nflfastR`](https://www.nflfastr.com/)
- Contract and cap data: [SpoTrac](https://www.spotrac.com/)

## Methodology

- **Outcome**: `epa_volatility_4yr`, the 4-year forward-looking SD of EPA/play (2011-2015 base seasons, windows through 2019; 2020 excluded).
- **Predictors**: QB/HC/OC continuity, average offensive starter age, QB experience, offensive draft capital, rookie cap share, offensive cap share - plus two theory-driven interactions (rookie share x draft capital, rookie share x offensive share).
- **Model**: OLS with team-clustered standard errors, cross-checked against Huber M-estimation (robust regression) on an identical specification, both with team and season fixed effects.
- **Diagnostics**: residuals vs. fitted, Cook's distance, Durbin-Watson/ACF for autocorrelation

See [analysis/nfl_rookie_contracts_and_team_stability.Rmd](analysis/nfl_rookie_contracts_and_team_stability.Rmd) for the full model specification and inline discussion, or [the PDF report](reports/nfl_rookie_contracts_and_team_stability_report.pdf) for the knitted write-up. Findings are also presented in PowerPoint format [here](reports/nfl_rookie_contracts_and_team_stability_presentation.pdf).

## License

See [`LICENSE`](LICENSE).

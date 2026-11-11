# The Geopolitics of Oil: Impact of the 2026 Gulf Crisis on Inflation

Panel data econometrics project measuring how the oil price shock from the 2026 Gulf Crisis passed through to domestic inflation in 8 countries.

## Overview

- **Countries:** Germany, France, Japan, United States, Turkey, India, Poland, Saudi Arabia
- **Period:** January 2023 – April 2026 (monthly, 320 observations)
- **Crisis start:** 27 February 2026
- **Models:** Pooled OLS, Fixed Effects, Random Effects
- **Dependent variable:** Log(CPI)

## Model

```
ln_cpi_it = α_i + β1·oil_pct_change + β2·ln_neer + β3·policy_rate + β4·vix + β5·post_crisis + ε_it
```

| Variable | Description |
|---|---|
| `oil_pct_change` | Monthly % change in Brent crude price |
| `ln_neer` | Log of the Nominal Effective Exchange Rate |
| `policy_rate` | Central bank policy rate (%) |
| `vix` | CBOE Volatility Index |
| `post_crisis` | 1 if date ≥ March 2026 |

Data sources: IMF IFS, OECD, FRED, BIS, U.S. EIA.

## Model Selection

- **Hausman test** (p = 0.0485): rejects Random Effects, so **Fixed Effects** is used.
- **Breusch-Pagan test** (p < 2.2e-16): rejects Pooled OLS.

## Key Results (Fixed Effects)

| Variable | Coefficient |
|---|---|
| Oil price change | 0.001 ** |
| Log(NEER) | −1.219 *** |
| Policy rate | 0.003 *** |
| VIX | 0.005 *** |
| Post-crisis dummy | 0.053 *** |

- Oil pass-through to CPI is **significant but small** (about 0.1% per 1 pp oil increase).
- A 1% currency appreciation lowers CPI by about **1.2%**.
- The crisis is associated with about **5.3% higher inflation**.
- Results hold under Arellano HC3 robust standard errors.

## Main Finding: The Turkey Effect

| | Oil coefficient |
|---|---|
| Oil importers (all) | 0.001 ** |
| Oil exporters | not significant |
| Oil importers excluding Turkey | not significant |

The inflation effect among oil importers is driven almost entirely by **Turkey's hyperinflation**, not by a uniform oil channel. For stable importers, exchange rate stability and monetary policy credibility matter more than the oil shock itself.

## Limitations

- Short post-crisis window (2–4 months)
- Possible endogeneity of the policy rate
- No lag structure for oil pass-through
- Turkey dominates the emerging importer group

## Repository Structure

```
├── README.md
├── Report/
├── Data/
└── Code/
```

## Author

**Ons Guizani**

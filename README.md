# SARIMA on Brazilian retail sales (PMC)

Exercise for **Financial Analytics** (PADS Insper, 2026.34): SARIMA modeling of IBGE's PMC
expanded retail sales volume index for one state (UF), with a 24-month forecast.

**Report:** <https://gustavogb.github.io/fa-sarima-pmc/>

## Contents

| File | What it is |
|---|---|
| `template-exercicio-sarima.qmd` | The analysis (Quarto + Python) |
| `index.html` | Rendered report, served by GitHub Pages |
| `data/raw/pmc_volume_uf.parquet` | Cached copy of the course dataset |
| `pyproject.toml`, `uv.lock` | Python environment (uv) |

## Reproduce

Requires [uv](https://docs.astral.sh/uv/) and [Quarto](https://quarto.org).

```bash
uv sync
uv run quarto render template-exercicio-sarima.qmd
```

The state is a Quarto parameter (default: São Paulo). To render another one:

```bash
uv run quarto render template-exercicio-sarima.qmd -P UF:"Minas Gerais"
```

Names must match the dataset spelling, accents included; an invalid name stops the render and
lists the valid ones.

## Stack

polars for data handling, statsforecast `AutoARIMA` for modeling, statsmodels for unit-root
tests and diagnostics, seaborn/matplotlib with the colorblind-safe Okabe-Ito palette, and a
Pandera schema that checks the series before modeling (no missing or duplicated months).

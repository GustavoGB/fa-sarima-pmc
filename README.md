# SARIMA no comércio varejista brasileiro (PMC)

Exercício da disciplina **Financial Analytics** (PADS Insper, turma 2026.34): modelagem SARIMA
do índice de volume de vendas do varejo ampliado da PMC (IBGE) para uma UF, com previsão de
24 meses.

**Relatório:** <https://gustavogb.github.io/fa-sarima-pmc/>

**Autor:** Gustavo Gobetti Bertocco

## Conteúdo

| Arquivo | O que é |
|---|---|
| `template-exercicio-sarima.qmd` | A análise (Quarto + Python) |
| `index.html` | Relatório renderizado, servido pelo GitHub Pages |
| `data/raw/pmc_volume_uf.parquet` | Cópia em cache da base da disciplina |
| `pyproject.toml`, `uv.lock` | Ambiente Python (uv) |

## Como reproduzir

Requer [uv](https://docs.astral.sh/uv/) e [Quarto](https://quarto.org).

```bash
uv sync
uv run quarto render template-exercicio-sarima.qmd
```

A UF é um parâmetro do Quarto (padrão: Minas Gerais). Para gerar o relatório de outra:

```bash
uv run quarto render template-exercicio-sarima.qmd -P UF:"Bahia"
```

O nome precisa seguir a grafia da base, com acentos; um nome inválido interrompe a
renderização e lista os valores válidos.

## Ferramentas

polars para manipulação dos dados, `AutoARIMA` do statsforecast para a modelagem,
statsmodels para os testes de raiz unitária e diagnósticos, seaborn/matplotlib com a paleta
Okabe-Ito (segura para daltonismo) e um schema Pandera que valida a série antes da modelagem
(sem meses faltando ou duplicados).

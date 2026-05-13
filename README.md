# hewelio

Hewelio — przewidujemy ile naprawdę zajmie ci dojazd komunikacją w Trójmieście. MLOps project.

## Status

W budowie. Projekt edukacyjny pokazujący pełną pętlę MLOps end-to-end.

## Stack

**Język i tooling:**
- Python 3.12
- [uv](https://github.com/astral-sh/uv) — package manager
- [ruff](https://github.com/astral-sh/ruff) — linter + formatter
- [mypy](https://mypy.readthedocs.io/) (strict mode) — static type checking
- [pytest](https://pytest.org) — testy
- [pre-commit](https://pre-commit.com/) — git hooks

**Planowane (w kolejnych lekcjach):**
- Supabase (Postgres) — baza danych
- Cloudflare R2 — object storage
- DagsHub — MLflow tracking + DVC remote
- Hugging Face Hub — model registry
- Next.js + Vercel + Auth.js — frontend
- Evidently AI — monitoring
- GitHub Actions — orchestration + CI/CD

## Źródła danych

- [Otwarte dane ZTM Gdańsk](https://ckan.multimediagdansk.pl/dataset/tristar) (GTFS + real-time GPS positions, licencja CC BY)
- [Otwarte dane ZKM Gdynia](https://otwartedane.gdynia.pl/)
- [System pomiarów meteorologicznych aglomeracji gdańskiej](https://www.gdansk.pl/otwarte-dane-w-gdansku/api,a,172679)
- [Open-Meteo](https://open-meteo.com/) — backup pogody

## Setup

Wymagania: [uv](https://github.com/astral-sh/uv).

```bash
# klon repo
git clone https://github.com/rgortowski/hewelio.git
cd hewelio

# instalacja Pythona i zależności
uv sync

# uruchomienie hooków (raz po klonie)
uv run pre-commit install

# sanity check
uv run pytest
```

## Struktura projektu

```
hewelio/
├── apps/              # frontend (Next.js) + ewentualne API
│   ├── web/
│   └── api/
├── pipelines/         # data + ML pipelines (orkiestracja w GitHub Actions)
│   ├── ingest/        # pobieranie danych z ZTM, ZKM, meteo
│   ├── train/         # trenowanie modeli
│   └── predict/       # batch inference
├── src/hewelio/       # współdzielona biblioteka Python
├── tests/
├── infra/sql/         # schematy bazy, migracje
├── docs/              # COURSE.md i inne docsy
└── .github/workflows/ # GitHub Actions
```

## Licencja

[MIT](LICENSE) — kod jest open source. Dane z ZTM/ZKM Gdynia są na licencji CC BY (atrybucja wymagana).

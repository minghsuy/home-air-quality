# Home Air Quality Guide

[![Deploy](https://github.com/minghsuy/home-air-quality/actions/workflows/deploy.yml/badge.svg)](https://github.com/minghsuy/home-air-quality/actions/workflows/deploy.yml)
[![Check links](https://github.com/minghsuy/home-air-quality/actions/workflows/links.yml/badge.svg)](https://github.com/minghsuy/home-air-quality/actions/workflows/links.yml)

A practical, evidence-based guide to understanding and improving the air in your home — written for people who live with **asthma and allergies**.

📖 **Read it: https://minghsuy.github.io/home-air-quality/**

## What's inside

- **The guide** ([`docs/index.md`](docs/index.md)) — what to measure (PM2.5, CO₂, VOCs, radon, humidity), how to interpret it (indoor vs. outdoor), and how to improve it (source control, MERV-13 filtration, the ERV fresh-air trade-off, humidity, wildfire clean rooms).
- **[Filter efficiency, done right](docs/filter-efficiency.md)** — judge a filter by *how well it removes particles*, not by its age, and why clean outdoor air breaks the math.
- **[Wildfire smoke playbook](docs/wildfire-smoke.md)** — the seal-up / clean-room routine for high-AQI days.

## How this site is built

The Markdown in `docs/` is built into a website by [MkDocs](https://www.mkdocs.org/) + [Material for MkDocs](https://squidfunk.github.io/mkdocs-material/), and published to GitHub Pages automatically by the workflow in [`.github/workflows/deploy.yml`](.github/workflows/deploy.yml) on every push to `main`.

Preview it locally:

```bash
pip install mkdocs-material
mkdocs serve   # then open http://127.0.0.1:8000
```

## Contributing & disclaimer

Educational content, **not medical advice** — see the note at the top of the guide. Corrections and additions welcome via issue or PR.

Released under the [MIT License](LICENSE).

# Mojtaba Karimi

**Python backend, automation & data engineering** — FastAPI · async SQLAlchemy · Postgres · Docker

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mojtaba-karimi-python)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:mojtaba.python@gmail.com)

I build backend services, scrapers and data pipelines in Python, and I ship them the way I'd
want to inherit them: typed, tested, containerised, and wired to CI. Electrical engineering
graduate, based in Ankara, Türkiye (UTC+03:00), working remotely.

**Available for freelance projects, and open to junior/mid backend roles.** My working day
overlaps European business hours. Reach me by [email](mailto:mojtaba.python@gmail.com) or on
[LinkedIn](https://www.linkedin.com/in/mojtaba-karimi-python).

<!-- Freelance profiles: paste the public Fiverr / Upwork URLs here once they are live, e.g.
     [Fiverr](URL) · [Upwork](URL) — leave this comment empty rather than linking a draft. -->

### What I build for clients

- **Web scraping & data extraction** — crawlers that respect `robots.txt` and rate limits and
  hand back clean CSV, JSON or JSONL instead of half-parsed HTML.
- **REST APIs** — FastAPI services with authentication, validation, database migrations and a
  container image that runs the same on your machine and on the server.
- **Automation & scheduled pipelines** — a manual weekly routine turned into a job that runs on
  a schedule, keeps a history, and says so when it breaks.
- **Dashboards & reporting** — the collected data charted, scored, and exported as HTML or PDF.

Every repository below runs `ruff`, `mypy` and `pytest` on each push, plus `bandit` and
`pip-audit` for security. Each pipeline pins its GitHub Actions to full commit SHAs and
asks for a read-only token. The badges are live and the workflow files are right there, so
you can check any claim I make here — please do.

---

## Featured work

### 🛒 [E-commerce Price Intelligence](https://github.com/mojtaba-py-code/universal-ecommerce-price-intelligence)

A plugin-based price tracker: it scrapes product pages, keeps an append-only price history,
detects every change, and charts the result in a FastAPI dashboard. Adding a store is one new
file, with no change to the pipeline, the API or the database layer.

Outbound fetches pass an SSRF guard, and a fixture scraper keeps the test suite offline and
deterministic instead of dependent on a live shop.

`FastAPI` · `SQLAlchemy` · `PostgreSQL` · `Chart.js`

### 🕷️ [Polite Web Crawler](https://github.com/mojtaba-py-code/polite-web-crawler)

Give it a seed URL and it crawls within that site, extracts structured data from each page and
writes JSON Lines — respecting `robots.txt` and holding itself to one request per second per host.

The SSRF guard resolves every URL and refuses private, loopback and link-local addresses, with no
flag to switch it off. Credentials are read from the environment only and redacted from output.

`Python CLI` · `JSONL` · `bandit`-clean

### 🧭 [Smart Travel Aggregator](https://github.com/mojtaba-py-code/smart-travel-aggregator)

Travel search across several providers behind one API, with per-provider circuit breakers so a
slow upstream degrades the response instead of taking the service down. JWT auth with RBAC,
Redis-backed rate limiting and caching, and Prometheus RED metrics per route.

[**Live demo →**](https://smart-travel-aggregator.onrender.com/docs) · free tier, first request takes ~40s to wake

`Clean Architecture` · `async SQLAlchemy` · `Redis` · `Prometheus` · `Alembic`

### 🛰️ [Cyber Threat Intelligence Platform](https://github.com/mojtaba-py-code/cyber-threat-intelligence-platform)

A self-hostable TIP. Collects indicators from feeds, enriches and scores them, correlates them
into campaigns, and shares the result over STIX 2.1 / MISP with a live SSE alert stream.

Runs fully offline by default — every outbound request goes through an SSRF guard that resolves
the host and rejects private, link-local and loopback ranges before the socket opens.

`FastAPI` · `async SQLAlchemy` · `Celery` · `Alembic` · Docker Compose + nginx

### 📊 [Big Data Log Analytics Platform](https://github.com/mojtaba-py-code/big-data-log-analytics-platform)

Streaming log ingestion that holds memory flat regardless of input size, backed by a columnar
Parquet/DuckDB store with partition pruning. Adds a safe query language, statistical anomaly
detection and security analytics, served over REST, a dashboard and a CLI.

Memory behaviour is measured by a benchmark harness that runs in CI, not asserted in prose.

`DuckDB` · `Parquet` · `FastAPI` · `mypy --strict` · benchmarks in CI

### 🛠️ [DevOps Utility Collection](https://github.com/mojtaba-py-code/devops-utility-script-collection)

Fifteen operational tools — backups, file sync, Docker and SSH helpers, deployment, monitoring —
behind a single CLI with one config format and one logging setup. Written security-first:
archive extraction refuses both traversal names and symlink members, and every subprocess call
is an argument list against an allow-listed binary, never a shell.

`Python CLI` · `Bandit`-clean · `pip-audit` in CI

### 🧪 [Smart Data Quality Monitoring System](https://github.com/mojtaba-py-code/smart-data-quality-monitoring-system)

Profiles a tabular dataset, validates it against a rule battery, cleans it, and condenses the
result into a 0–100 quality score across five dimensions — then tracks schema and distribution
drift between versions and reports it as HTML, PDF, or an interactive dashboard.

The score is explainable rather than a black box: each dimension names the rules that moved it
and the row positions that failed, so a bad number tells you what to fix. Every file it reads is
treated as untrusted input.

`Clean Architecture` · `pandas` · `Streamlit` · Docker · reports in HTML/PDF

---

## Other projects

- [AI Job Market Intelligence](https://github.com/mojtaba-py-code/ai-job-market-intelligence) —
  NLP skill extraction and semantic job search
- [Vault Backup](https://github.com/mojtaba-py-code/vault-backup) — encrypted backups with
  content-addressed deduplication
- [Unified API Integration Platform](https://github.com/mojtaba-py-code/unified-api-integration-platform) —
  plugin layer over several external APIs
- [Enterprise Data Pipeline](https://github.com/mojtaba-py-code/enterprise-data-processing-pipeline) —
  config-driven pandas ETL
- [File Automation](https://github.com/mojtaba-py-code/enterprise-file-automation) —
  watched-folder file processing

---

## Toolbox

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![SQLAlchemy](https://img.shields.io/badge/SQLAlchemy-D71F00?style=flat&logo=sqlalchemy&logoColor=white)
![DuckDB](https://img.shields.io/badge/DuckDB-FFF000?style=flat&logo=duckdb&logoColor=black)
![Redis](https://img.shields.io/badge/Redis-DC382D?style=flat&logo=redis&logoColor=white)
![Celery](https://img.shields.io/badge/Celery-37814A?style=flat&logo=celery&logoColor=white)
![pandas](https://img.shields.io/badge/pandas-150458?style=flat&logo=pandas&logoColor=white)
![Docker](https://img.shields.io/badge/Docker-2496ED?style=flat&logo=docker&logoColor=white)
![Pytest](https://img.shields.io/badge/Pytest-0A9EDC?style=flat&logo=pytest&logoColor=white)
![Ruff](https://img.shields.io/badge/Ruff-D7FF64?style=flat&logo=ruff&logoColor=black)
![mypy](https://img.shields.io/badge/mypy-2A6DB2?style=flat&logo=python&logoColor=white)
![GitHub Actions](https://img.shields.io/badge/GitHub%20Actions-2088FF?style=flat&logo=githubactions&logoColor=white)

---

Open to backend, API and data-engineering roles — remote, contract or freelance.
Reach me on [LinkedIn](https://www.linkedin.com/in/mojtaba-karimi-python) or by [email](mailto:mojtaba.python@gmail.com).

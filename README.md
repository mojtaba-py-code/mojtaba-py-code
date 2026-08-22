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

### What I build for clients

- **Web scraping & data extraction** — crawlers that respect `robots.txt` and rate limits and
  hand back clean CSV, JSON or JSONL instead of half-parsed HTML.
- **REST APIs** — FastAPI services with authentication, validation, database migrations and a
  container image that runs the same on your machine and on the server.
- **Automation & scheduled pipelines** — a manual weekly routine turned into a job that runs on
  a schedule, keeps a history, and says so when it breaks.
- **Dashboards & reporting** — the collected data charted, scored, and exported as HTML or PDF.

### Two demos you can open right now

- **[Price tracker](https://price-intelligence-demo.onrender.com)** — scrapes products, keeps the
  full price history, charts it and flags every change.
- **[Travel search API](https://smart-travel-aggregator.onrender.com/docs)** — several providers
  behind one API, browsable from the interactive OpenAPI page.

Both run on a free instance, so the first request takes ~40s to wake it.

Every repository below runs `ruff`, `mypy` and `pytest` on each push, plus `bandit` and
`pip-audit` for security. Each pipeline pins its GitHub Actions to full commit SHAs and asks
for a read-only token, and CodeQL, Dependabot and secret-scanning push protection are enabled
across all 12 code repositories. Together the suites run over 1,400 tests, and every project
that names a coverage floor below fails its own build when coverage drops under it. The badges
are live and the workflow files are right there, so you can check any claim I make here —
please do.

---

## Featured work

### 🛒 [E-commerce Price Intelligence](https://github.com/mojtaba-py-code/universal-ecommerce-price-intelligence)

**Tracks prices across stores over time and shows exactly when, and by how much, each one moved.**

- Plugin-per-store scraping: adding a shop is one new file, with no change to the pipeline, the
  API or the database layer.
- Append-only price history, so every product carries a full trend line, its lowest-ever price,
  and a log of every detected change.
- A FastAPI dashboard charts that history; the same data is available over the API.
- Outbound fetches pass an SSRF guard, and a fixture scraper keeps the test suite offline and
  deterministic instead of dependent on a live shop.

[**Live demo →**](https://price-intelligence-demo.onrender.com) · free tier, first request takes ~40s to wake

80% coverage floor enforced in CI · `FastAPI` · `SQLAlchemy` · `PostgreSQL` · `Chart.js`

### 🕷️ [Polite Web Crawler](https://github.com/mojtaba-py-code/polite-web-crawler)

**Turns a seed URL into a clean JSONL dataset without getting you blocked.**

- Crawls within the seeded site, extracts structured data from each page, and writes JSON Lines.
- Respects `robots.txt` and holds itself to one request per second per host.
- The SSRF guard resolves every URL and refuses private, loopback and link-local addresses —
  there is no flag to switch it off.
- Handles what scrapers actually run into: oversized responses, redirect abuse, and credentials
  leaking into logs. Credentials come from the environment only and are redacted from output.

80% coverage floor enforced in CI · threat model written down in `SECURITY.md` · `Python CLI` · `JSONL` · `bandit`-clean

### 🧭 [Smart Travel Aggregator](https://github.com/mojtaba-py-code/smart-travel-aggregator)

**Travel search across several providers behind one API that degrades instead of falling over.**

- Per-provider circuit breakers: a slow upstream costs you that provider's results, not the
  whole response.
- JWT authentication with role-based access, plus Redis-backed rate limiting and caching.
- Prometheus RED metrics per route, so latency and error rate are visible per endpoint.
- Clean Architecture layering with Alembic migrations.

[**Live demo →**](https://smart-travel-aggregator.onrender.com/docs) · free tier, first request takes ~40s to wake

90% coverage floor enforced in CI · `async SQLAlchemy` · `Redis` · `Prometheus` · `Alembic`

### 🛰️ [Cyber Threat Intelligence Platform](https://github.com/mojtaba-py-code/cyber-threat-intelligence-platform)

**A self-hostable threat-intelligence platform that runs fully offline by default.**

- Collects indicators from feeds, enriches and scores them, and correlates them into campaigns.
- Shares the result over STIX 2.1 / MISP, with a live SSE alert stream for new detections.
- Every outbound request goes through an SSRF guard that resolves the host and rejects private,
  link-local and loopback ranges before the socket opens.

80% coverage floor enforced in CI · `FastAPI` · `async SQLAlchemy` · `Celery` · `Alembic` · Docker Compose + nginx

### 📊 [Big Data Log Analytics Platform](https://github.com/mojtaba-py-code/big-data-log-analytics-platform)

**Ingests log streams of any size on flat memory, then answers questions about them in seconds.**

- Streaming ingestion whose memory behaviour is measured by a benchmark harness that runs in CI,
  not asserted in prose.
- Columnar Parquet/DuckDB store with partition pruning behind a safe query language.
- Statistical anomaly detection and security analytics on top of the same store.
- Served three ways: REST API, dashboard and CLI.

80% coverage floor enforced in CI · `DuckDB` · `Parquet` · `FastAPI` · `mypy --strict`

### 🛠️ [DevOps Utility Collection](https://github.com/mojtaba-py-code/devops-utility-script-collection)

**Fifteen operational tools behind a single CLI, one config format and one logging setup.**

- Backups, file sync, Docker and SSH helpers, deployment and monitoring.
- Archive extraction refuses both traversal names and symlink members.
- Every subprocess call is an argument list against an allow-listed binary, never a shell.

85% coverage floor enforced in CI · `Python CLI` · `bandit`-clean · `pip-audit` in CI

### 🧪 [Smart Data Quality Monitoring System](https://github.com/mojtaba-py-code/smart-data-quality-monitoring-system)

**Scores a dataset from 0 to 100 and names the rules and rows that moved the number.**

- Profiles a tabular dataset, validates it against a rule battery, and cleans it.
- Scores it across five dimensions; each dimension names the rules that moved it and the row
  positions that failed, so a bad number tells you what to fix.
- Tracks schema and distribution drift between versions of the same dataset.
- Reports as HTML, PDF or an interactive dashboard; every file it reads is untrusted input.

80% coverage floor enforced in CI · `Clean Architecture` · `pandas` · `Streamlit` · Docker

---

## Other projects

- [AI Job Market Intelligence](https://github.com/mojtaba-py-code/ai-job-market-intelligence) —
  NLP skill extraction and semantic job search · 80% coverage floor enforced in CI
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

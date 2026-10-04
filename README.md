# Mojtaba Karimi

**Python AI backend engineer** — LLM & RAG applications, APIs and data pipelines · FastAPI · PostgreSQL · pgvector · Docker

[![LinkedIn](https://img.shields.io/badge/LinkedIn-0A66C2?style=flat&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/mojtaba-karimi-python)
[![Email](https://img.shields.io/badge/Email-EA4335?style=flat&logo=gmail&logoColor=white)](mailto:mojtaba.python@gmail.com)

I build LLM-powered backends, RAG systems, APIs and data pipelines in Python, and I ship them the way I'd
want to inherit them: typed, tested, containerised, and wired to CI. Electrical engineering
graduate, based in Ankara, Türkiye (UTC+03:00), working remotely.

**Available for freelance projects, and open to junior/mid backend roles.** My working day
overlaps European business hours. Reach me by [email](mailto:mojtaba.python@gmail.com) or on
[LinkedIn](https://www.linkedin.com/in/mojtaba-karimi-python).

### What I build for clients

- **AI integration (LLM & RAG)** — Claude-powered assistants that answer from your own documents
  with citations, call your systems through permission-checked tools, and treat the model as
  untrusted input: prompt-injection screening, data governance and a human hand-off built in.
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
across all 24 actively maintained repositories. Together the suites run over 6,000 tests, and every project
that names a coverage floor below fails its own build when coverage drops under it. The badges
are live and the workflow files are right there, so you can check any claim I make here —
please do.

---

## Featured work

### 🛡️ [AegisSupport AI — Secure LLM Customer-Support Platform](https://github.com/mojtaba-py-code/secure-ai-customer-support-platform)

**Customers chat with an AI assistant that answers from the knowledge base, looks up their own orders
and tickets, and hands over to a human agent when the situation calls for one.**

- The language model is treated as an untrusted component: who may see which record, which tools a turn
  may use and whether a reply is safe to show are decided in deterministic, tested code around it.
- Grounded RAG answers with citations over Qdrant, with visibility filtering inside the vector search and
  prompt-injection screening at upload and at retrieval.
- Refunds and cancellations are prepared by the assistant and confirmed by the customer, never executed
  by the model alone.
- Fuzzed with Schemathesis and scanned with OWASP ZAP in CI; release images are signed with cosign and
  carry SLSA provenance.

484 tests · 85% coverage floor enforced in CI · `Claude` · `FastAPI` · `PostgreSQL` · `Qdrant` · `Redis` · Docker

### 📄 [AI Document Assistant — Secure Multi-Tenant RAG](https://github.com/mojtaba-py-code/ai-document-assistant)

**Upload contracts, invoices and policies, search them by meaning and keyword, and get answers that
cite the exact page — while every user only ever sees the documents they are entitled to.**

- Authorization is compiled into the SQL of every search, and PostgreSQL row-level security enforces
  the tenant boundary underneath it.
- Hybrid search: PostgreSQL full-text plus pgvector or Qdrant, fused and reranked.
- Every citation quote is verified in code; restricted text never leaves for an external model.
- Untrusted files are parsed in a secret-free, resource-limited sandbox with ClamAV scanning.

1,747 tests · `Claude` · `FastAPI` · `PostgreSQL` · `pgvector` · `Qdrant` · Docker

### 🤖 [NexusFlow AI — Automation & Competitive-Intelligence Platform](https://github.com/mojtaba-py-code/fastapi-postgres-ai-automation-platform)

**Collects business data from websites, APIs, signed webhooks and spreadsheet uploads, keeps its full
history, and tells the right people when something meaningful changes.**

- Multi-tenant by design: PostgreSQL row-level security, forced on a role that cannot bypass it, plus
  an explicit tenant filter in every query.
- Hostile content - web pages and uploaded files - is parsed only in a sandbox worker that has no
  database, no storage and no secrets.
- n8n schedules and orchestrates; Python workers on Celery/RabbitMQ execute. Every step is authorized,
  idempotent and recorded in a hash-chained audit log.
- AI analysis is opt-in per tenant and never sees data classified as restricted.
- Sign-in with passkeys, TOTP or OIDC single sign-on, with SCIM provisioning.

2,560 tests · 80% coverage floor enforced in CI · `FastAPI` · `PostgreSQL` · `Celery` · `RabbitMQ` · `n8n` · Docker

### ⚙️ [IronFlow — Enterprise ETL Platform](https://github.com/mojtaba-py-code/ironflow)

**Declare a pipeline in YAML; it runs as a dependency graph, streams in bounded memory, and
either lands completely or not at all.**

- Extraction, validation, transformation and loading each stream, so a dataset larger than
  memory is a normal case rather than the one that kills the run.
- Loads are transactional and rows that fail validation are quarantined, so a bad batch never
  leaves the destination half-written with no record of what was dropped.
- Expressions evaluate in an AST sandbox, and path, SQL and SSRF guards sit on every boundary
  where a pipeline file could otherwise reach the host.
- Every run appends to a hash-chained audit trail, so an altered history does not verify.
- Driven from a CLI, a REST API, or the Docker image.

1443 tests · 89% branch-coverage floor enforced in CI · `Python` · `SQLAlchemy` · `Pydantic` · `FastAPI` · Docker

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
  NLP skill extraction and semantic job search · 85% coverage floor enforced in CI
- [Vault Backup](https://github.com/mojtaba-py-code/vault-backup) — encrypted backups with
  content-addressed deduplication · 80% coverage floor enforced in CI
- [Website Monitoring](https://github.com/mojtaba-py-code/website-monitoring-automation) —
  async website, API, SSL and DNS monitoring · published on
  [PyPI](https://pypi.org/project/website-monitoring-automation/)
- [Payment Gateway Integration](https://github.com/mojtaba-py-code/universal-payment-gateway-integration) —
  provider-agnostic payments with idempotency and signed webhooks · 90% coverage floor enforced in CI
- [File Automation](https://github.com/mojtaba-py-code/enterprise-file-automation) —
  watched-folder file processing · 85% coverage floor enforced in CI

---

## Upstream

- [litestar-org/litestar#5017](https://github.com/litestar-org/litestar/pull/5017) — merged:
  corrected duplicated words in two error messages.
- [pypa/pip-audit#1111](https://github.com/pypa/pip-audit/pull/1111) — proposed validating
  `--output` before running the audit, so a scan does not complete only to fail on an
  unwritable path. Not merged.

---

## Toolbox

![Python](https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white)
![Claude](https://img.shields.io/badge/Claude%20API-191919?style=flat&logo=anthropic&logoColor=white)
![LLM & RAG](https://img.shields.io/badge/LLM%20%26%20RAG-6E40C9?style=flat)
![FastAPI](https://img.shields.io/badge/FastAPI-009688?style=flat&logo=fastapi&logoColor=white)
![PostgreSQL](https://img.shields.io/badge/PostgreSQL-4169E1?style=flat&logo=postgresql&logoColor=white)
![pgvector](https://img.shields.io/badge/pgvector-336791?style=flat)
![Qdrant](https://img.shields.io/badge/Qdrant-DC244C?style=flat)
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

Open to AI backend, API and data-engineering roles — remote, contract or freelance.
Reach me on [LinkedIn](https://www.linkedin.com/in/mojtaba-karimi-python) or by [email](mailto:mojtaba.python@gmail.com).


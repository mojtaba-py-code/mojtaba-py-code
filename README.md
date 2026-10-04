Mojtaba Karimi
Python AI backend engineer — LLM & RAG applications, APIs and data pipelines · FastAPI · PostgreSQL · pgvector · Docker

LinkedIn Email

I build LLM-powered backends, RAG systems, APIs and data pipelines in Python, and I ship them the way I'd want to inherit them: typed, tested, containerised, and wired to CI. Electrical engineering graduate, based in Ankara, Türkiye (UTC+03:00), working remotely.

Available for freelance projects, and open to junior/mid backend roles. My working day overlaps European business hours. Reach me by email or on LinkedIn.

What I build for clients
AI integration (LLM & RAG) — Claude-powered assistants that answer from your own documents with citations, call your systems through permission-checked tools, and treat the model as untrusted input: prompt-injection screening, data governance and a human hand-off built in.
Web scraping & data extraction — crawlers that respect robots.txt and rate limits and hand back clean CSV, JSON or JSONL instead of half-parsed HTML.
REST APIs — FastAPI services with authentication, validation, database migrations and a container image that runs the same on your machine and on the server.
Automation & scheduled pipelines — a manual weekly routine turned into a job that runs on a schedule, keeps a history, and says so when it breaks.
Dashboards & reporting — the collected data charted, scored, and exported as HTML or PDF.
Two demos you can open right now
Price tracker — scrapes products, keeps the full price history, charts it and flags every change.
Travel search API — several providers behind one API, browsable from the interactive OpenAPI page.
Both run on a free instance, so the first request takes ~40s to wake it.

Every repository below runs ruff, mypy and pytest on each push, plus bandit and pip-audit for security. Each pipeline pins its GitHub Actions to full commit SHAs and asks for a read-only token, and CodeQL, Dependabot and secret-scanning push protection are enabled across all 24 actively maintained repositories. Together the suites run over 6,000 tests, and every project that names a coverage floor below fails its own build when coverage drops under it. The badges are live and the workflow files are right there, so you can check any claim I make here — please do.

Featured work
🛡️ AegisSupport AI — Secure LLM Customer-Support Platform
Customers chat with an AI assistant that answers from the knowledge base, looks up their own orders and tickets, and hands over to a human agent when the situation calls for one.

The language model is treated as an untrusted component: who may see which record, which tools a turn may use and whether a reply is safe to show are decided in deterministic, tested code around it.
Grounded RAG answers with citations over Qdrant, with visibility filtering inside the vector search and prompt-injection screening at upload and at retrieval.
Refunds and cancellations are prepared by the assistant and confirmed by the customer, never executed by the model alone.
Fuzzed with Schemathesis and scanned with OWASP ZAP in CI; release images are signed with cosign and carry SLSA provenance.
484 tests · 85% coverage floor enforced in CI · Claude · FastAPI · PostgreSQL · Qdrant · Redis · Docker

📄 AI Document Assistant — Secure Multi-Tenant RAG
Upload contracts, invoices and policies, search them by meaning and keyword, and get answers that cite the exact page — while every user only ever sees the documents they are entitled to.

Authorization is compiled into the SQL of every search, and PostgreSQL row-level security enforces the tenant boundary underneath it.
Hybrid search: PostgreSQL full-text plus pgvector or Qdrant, fused and reranked.
Every citation quote is verified in code; restricted text never leaves for an external model.
Untrusted files are parsed in a secret-free, resource-limited sandbox with ClamAV scanning.
1,747 tests · Claude · FastAPI · PostgreSQL · pgvector · Qdrant · Docker

🤖 NexusFlow AI — Automation & Competitive-Intelligence Platform
Collects business data from websites, APIs, signed webhooks and spreadsheet uploads, keeps its full history, and tells the right people when something meaningful changes.

Multi-tenant by design: PostgreSQL row-level security, forced on a role that cannot bypass it, plus an explicit tenant filter in every query.
Hostile content - web pages and uploaded files - is parsed only in a sandbox worker that has no database, no storage and no secrets.
n8n schedules and orchestrates; Python workers on Celery/RabbitMQ execute. Every step is authorized, idempotent and recorded in a hash-chained audit log.
AI analysis is opt-in per tenant and never sees data classified as restricted.
Sign-in with passkeys, TOTP or OIDC single sign-on, with SCIM provisioning.
2,560 tests · 80% coverage floor enforced in CI · FastAPI · PostgreSQL · Celery · RabbitMQ · n8n · Docker

⚙️ IronFlow — Enterprise ETL Platform
Declare a pipeline in YAML; it runs as a dependency graph, streams in bounded memory, and either lands completely or not at all.

Extraction, validation, transformation and loading each stream, so a dataset larger than memory is a normal case rather than the one that kills the run.
Loads are transactional and rows that fail validation are quarantined, so a bad batch never leaves the destination half-written with no record of what was dropped.
Expressions evaluate in an AST sandbox, and path, SQL and SSRF guards sit on every boundary where a pipeline file could otherwise reach the host.
Every run appends to a hash-chained audit trail, so an altered history does not verify.
Driven from a CLI, a REST API, or the Docker image.
1443 tests · 89% branch-coverage floor enforced in CI · Python · SQLAlchemy · Pydantic · FastAPI · Docker

🛒 E-commerce Price Intelligence
Tracks prices across stores over time and shows exactly when, and by how much, each one moved.

Plugin-per-store scraping: adding a shop is one new file, with no change to the pipeline, the API or the database layer.
Append-only price history, so every product carries a full trend line, its lowest-ever price, and a log of every detected change.
A FastAPI dashboard charts that history; the same data is available over the API.
Outbound fetches pass an SSRF guard, and a fixture scraper keeps the test suite offline and deterministic instead of dependent on a live shop.
Live demo → · free tier, first request takes ~40s to wake

80% coverage floor enforced in CI · FastAPI · SQLAlchemy · PostgreSQL · Chart.js

🕷️ Polite Web Crawler
Turns a seed URL into a clean JSONL dataset without getting you blocked.

Crawls within the seeded site, extracts structured data from each page, and writes JSON Lines.
Respects robots.txt and holds itself to one request per second per host.
The SSRF guard resolves every URL and refuses private, loopback and link-local addresses — there is no flag to switch it off.
Handles what scrapers actually run into: oversized responses, redirect abuse, and credentials leaking into logs. Credentials come from the environment only and are redacted from output.
80% coverage floor enforced in CI · threat model written down in SECURITY.md · Python CLI · JSONL · bandit-clean

🧭 Smart Travel Aggregator
Travel search across several providers behind one API that degrades instead of falling over.

Per-provider circuit breakers: a slow upstream costs you that provider's results, not the whole response.
JWT authentication with role-based access, plus Redis-backed rate limiting and caching.
Prometheus RED metrics per route, so latency and error rate are visible per endpoint.
Clean Architecture layering with Alembic migrations.
Live demo → · free tier, first request takes ~40s to wake

90% coverage floor enforced in CI · async SQLAlchemy · Redis · Prometheus · Alembic

🛰️ Cyber Threat Intelligence Platform
A self-hostable threat-intelligence platform that runs fully offline by default.

Collects indicators from feeds, enriches and scores them, and correlates them into campaigns.
Shares the result over STIX 2.1 / MISP, with a live SSE alert stream for new detections.
Every outbound request goes through an SSRF guard that resolves the host and rejects private, link-local and loopback ranges before the socket opens.
80% coverage floor enforced in CI · FastAPI · async SQLAlchemy · Celery · Alembic · Docker Compose + nginx

📊 Big Data Log Analytics Platform
Ingests log streams of any size on flat memory, then answers questions about them in seconds.

Streaming ingestion whose memory behaviour is measured by a benchmark harness that runs in CI, not asserted in prose.
Columnar Parquet/DuckDB store with partition pruning behind a safe query language.
Statistical anomaly detection and security analytics on top of the same store.
Served three ways: REST API, dashboard and CLI.
80% coverage floor enforced in CI · DuckDB · Parquet · FastAPI · mypy --strict

🛠️ DevOps Utility Collection
Fifteen operational tools behind a single CLI, one config format and one logging setup.

Backups, file sync, Docker and SSH helpers, deployment and monitoring.
Archive extraction refuses both traversal names and symlink members.
Every subprocess call is an argument list against an allow-listed binary, never a shell.
85% coverage floor enforced in CI · Python CLI · bandit-clean · pip-audit in CI

🧪 Smart Data Quality Monitoring System
Scores a dataset from 0 to 100 and names the rules and rows that moved the number.

Profiles a tabular dataset, validates it against a rule battery, and cleans it.
Scores it across five dimensions; each dimension names the rules that moved it and the row positions that failed, so a bad number tells you what to fix.
Tracks schema and distribution drift between versions of the same dataset.
Reports as HTML, PDF or an interactive dashboard; every file it reads is untrusted input.
80% coverage floor enforced in CI · Clean Architecture · pandas · Streamlit · Docker

Other projects
AI Job Market Intelligence — NLP skill extraction and semantic job search · 85% coverage floor enforced in CI
Vault Backup — encrypted backups with content-addressed deduplication · 80% coverage floor enforced in CI
Website Monitoring — async website, API, SSL and DNS monitoring · published on PyPI
Payment Gateway Integration — provider-agnostic payments with idempotency and signed webhooks · 90% coverage floor enforced in CI
File Automation — watched-folder file processing · 85% coverage floor enforced in CI
Upstream
litestar-org/litestar#5017 — merged: corrected duplicated words in two error messages.
pypa/pip-audit#1111 — proposed validating --output before running the audit, so a scan does not complete only to fail on an unwritable path. Not merged.
Toolbox
Show Image Show Image Show Image Show Image Show Image Show Image Show Image Show Image Show Image Show Image Show Image Show Image Show Image Show Image Show Image Show Image Show Image

Open to AI backend, API and data-engineering roles — remote, contract or freelance. Reach me on LinkedIn or by email.

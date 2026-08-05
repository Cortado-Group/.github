# Data Readiness

[dataquality.cortadogroup.ai](https://dataquality.cortadogroup.ai)

## What it does

Data Readiness profiles and cleans data before it enters a warehouse or a RAG system. Upload CSVs or a document collection and get schema inference, a ranked list of issues, and editable transformation rules you can inspect before anything runs.

It runs two pipelines:

- **Structured data:** infers schema from a CSV, detects semantic issues (malformed emails, inconsistent casing, mixed null representations), and proposes fixes — trimming, regex replacement, type coercion — as inspectable rules.
- **Unstructured data:** profiles documents (PDF, DOCX, TXT, EML, MSG, HTML) for RAG suitability, flagging duplicates, chunking quality issues, missing metadata, and staleness.

## Why we built it

We kept running into the same failure mode elsewhere: cleanup rules that silently failed — referenced but never actually implemented — with no indication anything was wrong. Data Readiness is built around the opposite instinct: every rule is inspectable and removable before it runs, every issue is labeled critical/important/minor rather than left to color alone, and every run produces a full audit trail.

## How clients use it

- Run a CSV or document set through the tool before it lands in a warehouse or a RAG pipeline
- Review the ranked issue list and remove any proposed rule before applying it
- Keep the audit trail — cleaned file, fix summary, and workflow context doc — from every run as a record of what changed and why

**Tagline:** "Clean your data. Trust your forecasts."

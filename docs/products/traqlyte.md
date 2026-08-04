# Traqlyte

[traqlyte.ai](https://traqlyte.ai)

## What it does

Traqlyte is an API-first experimentation platform that assigns users to multivariate test cohorts and tracks conversion outcomes across web, email, and advertising channels. Define campaign factors and variants, publish a versioned configuration, and a two-endpoint API (`/assign` and `/outcome`) deterministically maps users to cohorts and records what happened.

## Why we built it

Real campaigns test more than one variable at a time, but most A/B testing tools are built for the single-variable case and get bolted onto later. We designed Traqlyte for the multivariate reality from day one — as a lightweight decision layer that plugs into the CMS, ESP, and ad platforms you already run, instead of an all-in-one suite that wants to replace them.

## How clients use it

1. Define campaign factors and variants, publish a versioned configuration
2. Call `/assign` to deterministically map a user to a variant (`campaign_id + user_key + campaign_version` always resolves the same way)
3. Render content based on the returned assignment
4. Report outcomes (clicks, purchases, form submissions) back via `/outcome`
5. Analyze results in the data warehouse and scale the winning combination

## Notable details

- Supports full factorial, fractional factorial, and contextual bandit designs
- Signed decision logs and schema-first, warehouse-ready exports — no black-box assignment
- First-party identifiers only, no third-party enrichment
- p95 latency target under 100ms for assignments; idempotent and dedup-safe for retries and out-of-order outcomes

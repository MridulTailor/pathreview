## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/11

**Issue title:** Add support for ingesting a portfolio website URL

**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
Currently, users cannot provide their personal portfolio website URLs as a data source for the application. The system only ingests data from GitHub and resumes. Fixing this issue will involve adding a new pipeline that fetches the content of the provided portfolio URL, extracts relevant textual information such as the user's bio and project descriptions, and indexes it into the vector store, allowing the application to use this information alongside existing data sources. This will affect `ingestion/parsers/`, `ingestion/pipeline.py`, and `api/schemas/profile.py`.

**Branch name:** feat/11-portfolio-url-ingestion

**Setup confirmation:** [x] App runs locally at localhost:5173

**Cohort ledger:** [x] Issue added to cohort ledger

**Checklist reasoning:**
- **Understanding:** I can clearly explain that we need to add a `WebParser` to extract text from a portfolio URL and index it via `ingestion/pipeline.py`. I've located `api/schemas/profile.py`, `ingestion/pipeline.py`, and `ingestion/parsers/base.py`.
- **Tier Fit:** As a Tier 1 issue, it touches a few specific files (creating a parser, updating the pipeline, updating the schema) which is a great fit for a first contribution.
- **Codebase Readiness:** I've read `ingestion/pipeline.py` (specifically `ingest_resume` and `ingest_readme`) and understand how the new `ingest_portfolio` method will fit in.
- **Scope & Time:** The estimated 5-8 hours is realistic and achievable before Week 9. There are no open blockers or dependencies.

## Week 8 — Reproduction & solution planning

**Reproduction commit link:** https://github.com/mridultailor/pathreview/commit/a4105bf8fa4e7dd1393de3172a1cccd767112ab2

**Reproduction summary:**
I reviewed the existing ingestion pipelines and confirmed that we currently only support Resumes, Repos, and READMEs. I added a TODO comment in `ingestion/pipeline.py` to mark the exact location where the missing `ingest_portfolio` method should be implemented.

**PLAN.md link:** https://github.com/mridultailor/pathreview/blob/feat/11-portfolio-url-ingestion/PLAN.md

**Walkthrough video (recommended):** N/A

**Blockers or open questions:**
None at the moment.

## Week 9 — Solution building & PR submission

### Check-in 1 (mid-week)

**Current progress:**
I have implemented the `WebParser` class that extracts HTML content from a given URL and strips away boilerplate. I have also added `beautifulsoup4` to dependencies and implemented `ingest_portfolio` in the `IngestionPipeline`. All sub-tasks from PLAN.md are complete.

**Next steps:**
I am submitting the PR.

**Blockers:**


---

### Check-in 2 (end of week)

**PR link:** [link to your submitted pull request]

**Branch:** `feat/11-portfolio-url-ingestion`

**What you built:**
Added support for ingesting personal portfolio websites into the vector store. A new `WebParser` fetches and extracts the text content from the provided URL, and the `ingest_portfolio` pipeline method chunks and embeds this data just like existing sources.

**Tests added or updated:**
Added `tests/unit/test_web_parser.py` which covers successful and failed HTTP responses and input validation for the new `WebParser`.

**Self-review confirmation:** [x] make check passes  [x] make test-unit passes (Note: Pre-existing test and check failures exist, but my changes introduced no new failures.)

**Draft PR feedback received from:** none

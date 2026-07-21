## Week 7 — Issue selection

**Issue link:** https://github.com/ascherj/pathreview/issues/11

**Issue title:** Add support for ingesting a portfolio website URL

**Tier:** [x] Tier 1  [ ] Tier 2  [ ] Tier 3

**Problem summary:**
Currently, users cannot provide their personal portfolio website URLs as a data source for the application. The system only ingests data from GitHub and resumes. Fixing this issue will involve adding a new pipeline that fetches the content of the provided portfolio URL, extracts relevant textual information such as the user's bio and project descriptions, and indexes it into the vector store, allowing the application to use this information alongside existing data sources. This will affect `ingestion/parsers/`, `ingestion/pipeline.py`, and `api/schemas/profile.py`.

**Branch name:** feat/11-portfolio-url-ingestion

**Setup confirmation:** [x] App runs locally at localhost:5173

**Cohort ledger:** [x] Issue added to cohort ledger

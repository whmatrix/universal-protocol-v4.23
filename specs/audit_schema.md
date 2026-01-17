# Audit Schema — RAG Readiness Report

## Required Sections

| Section | Purpose |
|---------|---------|
| Executive Summary | One-paragraph verdict: READY / NOT READY / CONDITIONAL |
| Scope | What was evaluated (file types, corpus size, time period) |
| Findings | Categorized issues with severity (Critical / Warning / Info) |
| Quality Metrics | Quantitative scores for each dimension |
| Recommendations | Prioritized action items if not fully ready |
| Decision | Final GO / NO-GO with rationale |

## Quality Metrics (Scoring)

Each metric scored 0-100:

| Metric | Description | PASS Threshold |
|--------|-------------|----------------|
| Chunk Quality | Token distribution, coherence, no truncation artifacts | >= 80 |
| Metadata Completeness | Required fields present, no nulls | >= 95 |
| Embedding Integrity | Vectors non-zero, correct dimensions | >= 99 |
| Index Performance | Query latency < 100ms for top-k=10 | PASS/FAIL |
| Error Rate | Failed chunks / total chunks | < 1% |

## Decision Output Format

```json
{
  "decision": "READY" | "NOT_READY" | "CONDITIONAL",
  "confidence": <float 0-1>,
  "blocking_issues": [<string>, ...],
  "recommendations": [<string>, ...],
  "auditor": "<string>",
  "audit_date": "<ISO8601>"
}
```

## Severity Definitions

| Severity | Definition | Impact on Decision |
|----------|------------|-------------------|
| Critical | Data loss, incorrect retrieval, security issue | Blocks READY status |
| Warning | Degraded performance, missing optional metadata | May block depending on count |
| Info | Style issues, optimization opportunities | Does not block |

## READY Criteria

A corpus is **READY** when:
1. Zero Critical findings
2. Fewer than 5 Warning findings (or all have documented mitigations)
3. All quality metrics meet PASS thresholds
4. Index loads and queries successfully

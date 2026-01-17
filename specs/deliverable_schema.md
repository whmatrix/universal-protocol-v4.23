# Deliverable Schema — RAG-Ready Indexing Output

## Required Artifacts

| Artifact | Format | Description |
|----------|--------|-------------|
| `chunks.jsonl` | JSONL | One chunk per line, each with `chunk_id`, `text`, `source_file`, `position` |
| `metadata.jsonl` | JSONL | Line-aligned with chunks; contains `chunk_id`, `token_count`, `embedding_model`, `timestamp` |
| `vectors.index` | FAISS | Dense vector index (flat or IVF), dimensions match embedding model |
| `summary.json` | JSON | Manifest with stats, quality gates, and verification results |

## summary.json Required Fields

```json
{
  "manifest": {
    "total_chunks": <int>,
    "total_files_processed": <int>,
    "embedding_model": "<string>",
    "embedding_dimensions": <int>,
    "index_type": "<string>",
    "created_at": "<ISO8601>"
  },
  "stats": {
    "avg_chunk_tokens": <float>,
    "min_chunk_tokens": <int>,
    "max_chunk_tokens": <int>,
    "total_tokens": <int>
  },
  "quality_gates": {
    "chunk_alignment_pass": <bool>,
    "embedding_coverage_pass": <bool>,
    "index_integrity_pass": <bool>,
    "error_rate_below_threshold": <bool>
  },
  "errors": []
}
```

## Quality Gates — Pass Criteria

| Gate | PASS Condition |
|------|----------------|
| `chunk_alignment_pass` | Every line in `chunks.jsonl` has corresponding line in `metadata.jsonl` |
| `embedding_coverage_pass` | 100% of chunks have vectors in `vectors.index` |
| `index_integrity_pass` | Index loads without error; vector count matches chunk count |
| `error_rate_below_threshold` | `errors.length / total_chunks < 0.01` (< 1% error rate) |

## Verification Command (Example)

```bash
# Check line counts match
wc -l chunks.jsonl metadata.jsonl

# Verify FAISS index loads
python -c "import faiss; idx = faiss.read_index('vectors.index'); print(idx.ntotal)"
```

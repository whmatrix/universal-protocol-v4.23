> **Author:** John Mitchell (@whmatrix)
> **Status:** ACTIVE
> **Audience:** Protocol Implementers / Engineers
> **Environment:** No code to run (specification only)
> **Fast Path:** Read the deliverable contract below

> This is the authoritative specification for RAG deliverables, audit contracts, and quality gates.

# Universal Protocol v4.23 — RAG Deliverables & Audit Artifacts

This repository is the "start here" surface for how I operate under Universal Protocol v4.23:
- Deliverable contract (RAG-ready indexing outputs)
- Audit contract (RAG readiness evaluation)
- Quality gates and verification primitives
- Portfolio artifacts (PDF examples)

## What changed in v4.23 (artifact-first execution)

- Evidence artifacts are first-class: manifests, validation gates, and audit outputs.
- Explicit pass/fail thresholds for chunk integrity, alignment, and error states.
- Standardized deliverable structure for client handoff.

## Deliverable contract (Indexing output structure)

See: [portfolio_artifacts/Semantic_Indexing_Output__Example_Structure.pdf](portfolio_artifacts/Semantic_Indexing_Output__Example_Structure.pdf)

Deliverables (canonical):
- `chunks.jsonl`
- `metadata.jsonl` (line-aligned with chunks)
- `vectors.index` (FAISS)
- `summary.json` (manifest + stats + quality gates)

## Audit contract (RAG readiness report)

Examples:
- [portfolio_artifacts/Portfolio_01_RAG_Readiness_Audit.pdf](portfolio_artifacts/Portfolio_01_RAG_Readiness_Audit.pdf)
- [portfolio_artifacts/RAG_Readiness_Audit__Sample_Report.pdf](portfolio_artifacts/RAG_Readiness_Audit__Sample_Report.pdf)

## Portfolio artifacts (examples)

- Large-scale indexing example:
  [portfolio_artifacts/Portfolio_03_Large_Scale_Semantic_Indexing.pdf](portfolio_artifacts/Portfolio_03_Large_Scale_Semantic_Indexing.pdf)
- RAG-ready indexing example:
  [portfolio_artifacts/Portfolio_02_RAG_Ready_Semantic_Indexing.pdf](portfolio_artifacts/Portfolio_02_RAG_Ready_Semantic_Indexing.pdf)

## Implementation Lineage

| Role | Repository | Status |
|------|------------|--------|
| **Production** | [semantic-indexing-batch-02](https://github.com/whmatrix/semantic-indexing-batch-02) | Active (8.3M+ vectors) |
| **Foundational** | [semantic-indexing-batch-01](https://github.com/whmatrix/semantic-indexing-batch-01) | Superseded |

## License

This repository is licensed under **Apache License 2.0** (not MIT).

**Why Apache-2.0 for the protocol spec?**

- **Patent grant clause**: Apache-2.0 includes explicit patent grants, protecting anyone who implements this protocol
- **Industry standard**: API and protocol specifications commonly use Apache-2.0 (OpenAPI, gRPC, Protobuf)
- **Derivative implementations**: If you build a pipeline that follows this protocol, the patent grant covers your implementation

**Other whmatrix repositories** use MIT (simpler, permissive). The choice is intentional:
- **MIT** for implementation code (tools, scripts, indices)
- **Apache-2.0** for this specification (patent protection for implementers)

---

## Limitations & Non-Claims

This protocol defines structure and deliverable contracts, not retrieval quality guarantees. Compliance with this protocol does not imply fitness for any specific application. Retrieval quality, relevance, and domain suitability require independent evaluation.

---

## Protocol source

- [protocol/UNIVERSAL_PROTOCOL_v4.23_DRAFT.json](protocol/UNIVERSAL_PROTOCOL_v4.23_DRAFT.json)

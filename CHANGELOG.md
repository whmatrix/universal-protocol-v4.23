# Changelog

All notable changes to Universal Protocol will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

---

## [4.23.0] - 2026-01-17

### Added

- **Validation Pipeline:** 6-step checkpoint system for RAG deliverables
  - Format validation
  - Encoding validation
  - Deduplication check
  - Metadata alignment
  - Vector validation
  - Null vector detection

- **Manifest Structure:** Standardized build artifacts
  - `summary.json` — metadata, timing, and quality gates
  - Processing logs with drop/skip reasons
  - Audit trail for compliance

- **Metadata Alignment:** 1:1:1 mapping enforcement
  - Vectors <-> Chunks <-> Metadata
  - Zero null vectors enforcement
  - Score distribution validation

- **Deliverable Contracts:** Standardized output structure
  - `chunks.jsonl` — text segments with metadata
  - `metadata.jsonl` — document-level metadata (line-aligned)
  - `vectors.index` — FAISS index file
  - `summary.json` — manifest with stats and quality gates

- **Audit Contracts:** RAG readiness evaluation
  - Pass/fail thresholds for chunk integrity
  - Alignment verification
  - Error state classification

### Changed

- Evidence artifacts are first-class: manifests, validation gates, and audit outputs
- Explicit pass/fail thresholds for chunk integrity, alignment, and error states
- Standardized deliverable structure for client handoff

---

## [4.22.0] - 2025-12-01

### Added

- Initial protocol specification
- Audit checkpoints framework
- Deliverable schemas
- Embedding model constraints (e5-large-v2, 1024-dim, FP16)
- FAISS IndexFlatIP as default index type

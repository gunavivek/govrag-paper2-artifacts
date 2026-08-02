# Artifact Package — Benchmark Evaluation of Governed RAG (anonymous submission)

Integrity artifacts for the pre-registered, three-corpus benchmark evaluation
reported in the accompanying paper. Metric definitions are in the paper's
Section IV; this package supplies the records those definitions run against.

## Contents

- `preregistration/` — the analysis plan and stopping rule, including the
  complete dated deviation log (one file; the log is a section of the plan).
  Every deviation entry was pushed to a version-controlled repository before
  the affected step executed.
- `selection/` — the deterministic selection code, the frozen selection lists
  for the two subset corpora (records, questions, and selection JSON, which
  embeds the 462-document junk filter as `junk_doc_hashes`), the frozen
  benchmark input for the full corpus (`delucionqa_records_912.csv`), and the
  selection-validity document.
- `manifests/` — SHA-256 manifests and run manifests for all four sealed run
  archives, and build manifests for the three index archives.
- `eval-layer/` — the run-1 master evaluation log and frontier summary (the
  files from which run-1 reported numbers recompute). Runs 1R, 2, and 3 carry
  these inside their full archives below.
- `archives/` — the complete sealed archives for run 1 re-judge, run 2, and
  run 3 (evaluation logs, frontier summaries, per-configuration serve records,
  SHA-256 manifests). The run-1 build archive and the index archives exceed
  repository file-size limits (single files up to ~400 MB); their manifests
  are included above and the archives are available to reviewers on request.

## Recomputing a reported number

1. Pick the number's run and configuration in the paper (Section IV–V).
2. Open the corresponding `*_master_eval_log.csv` (in `eval-layer/` for run 1;
   inside `archives/` for runs 1R, 2, 3).
3. Apply the metric definition from the paper's Section IV over the rows of
   that configuration. Frontier summaries provide the per-configuration
   aggregates for cross-checking.
4. Verify file integrity against the archive's `SHA256SUMS.txt`.

## Anonymisation notes

- Two execution-state files (`state.json`, runs 2 and 3) are withheld: they
  contain local filesystem paths and no evaluation content. Their hash lines
  remain in the respective `SHA256SUMS.txt`; the files are available to
  reviewers on request. Every file shipped in `archives/` is verbatim and
  hash-verifiable.
- Run/build manifests and documentation files are anonymised copies (paths,
  repository names, a cost-attribution key prefix, and personal names
  neutralised); their technical content — dates, hashes, models, counts — is
  verbatim. Benchmark corpus content is untouched.

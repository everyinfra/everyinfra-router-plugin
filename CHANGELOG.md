# Changelog

## 0.3.0 — 2026-10-10

- The data cleanup tools were retired on 2026-10-09. Router now sends cleaning, labeling, extraction
  and summaries to EveryAI (`everyinfra_chat`), free for accounts that have topped up.
- Remove the cleanup transition guide and cleanup examples; update the skill, README files,
  manifests and repository metadata to match.
- Replace the plain-text terminology check in `scripts/validate.py` with a hashed blocklist that also
  covers JSON and YAML files.

## 0.2.0 — 2026-09-06

- Route authorized EveryData results to the cleanup contract (retired in 0.3.0).
- Document all 15 cleanup operations, entitlement and bounded included-use limits.
- Add inferred field discovery, task listing and original-task recovery by idempotency key.
- Keep `everyinfra_chat` active for ordinary supplied text during the separate migration window.

## 0.1.0 — 2026-09-05

- Standalone packaging for `everyinfra`.
- Focused English and Chinese README, setup, workflow, examples and repository discovery metadata.
- Imported the reviewed skill and H2 brand assets from the source commit in `repository-metadata.json`.
- Release scope is GitHub source distribution; marketplace approval and live paid-operation tests remain separate.

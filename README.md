# LifeGraph — SWE-bench Lite N=300 (tree + Qwen2.5-Coder-14B)

Public artifact repository for the LifeGraph hierarchical tree submission (`Locate → Diagnose → Patch`) on SWE-bench Lite.

## Contents
- `all_preds.jsonl` — official predictions (instance_id, model_name_or_path, model_patch)
- `predictions_official.json` / `.jsonl` — same payload

## System
- Scaffold: LifeGraph CSA tree orchestrator (3 nodes)
- Model: Qwen2.5-Coder-14B via Ollama on AWS g5.xlarge
- Split: SWE-bench Lite test (N=300)
- Pass@1; generation does not use FAIL_TO_PASS / PASS_TO_PASS / hints as an oracle

## Status
Docker harness evaluation (c6i) in progress for the non-empty sanitized subset. Logs/trajs will be added when the run completes.

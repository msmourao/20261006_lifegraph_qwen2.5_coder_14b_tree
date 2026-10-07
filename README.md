# PolyStack / LifeGraph — Tree Agent (Locate → Diagnose → Patch)

Public artifacts for a **reasoning architecture** coding agent: navigation lives in the system, not in free-roaming model heuristics.

Open Agent Hackathon 2026 · team **PolyStack** · track **Reasoning Architecture**.

## Claim (one line)

Mid-size open coders fail on repos less from weak fluency than from unstructured navigation. Tree replaces that with a deterministic hierarchy; the model only patches over **verbatim** source windows.

## Architecture

| Node | Role |
|------|------|
| **Locate** | Production-file candidates + byte-identical source snippets (SEARCH must match disk) |
| **Diagnose** | Signature / contract extraction on the target subgraph (blind-safe; no gold oracle) |
| **Patch** | Constrained SEARCH/REPLACE over Locate snippets only |

Anti-hallucination gate: invented SEARCH anchors fail closed (`sr_search_miss`) instead of applying a wrong edit.

## Official proof (SWE-bench Lite)

| Layer | Figure | Meaning |
|-------|--------|---------|
| R3 Resolved | **13 / 300 = 4.33%** | Sole official % Resolved (pass@1) |
| Of sanitized patches | 13 / 129 = 10.07% | Non-empty judged subset |
| Internal `tree_ok` | 64 / 300 | Pipeline alignment — **not** Resolved |

- Harness: official R3 · model: Qwen2.5-Coder-14B (Ollama) · g5.xlarge for the sealed run  
- Submission: [SWE-bench/experiments#500](https://github.com/SWE-bench/experiments/pull/500)  
- Generation posture: no FAIL_TO_PASS / PASS_TO_PASS / hints as oracle  

**Honesty:** do not equate `tree_ok` or `apply_ok` with Resolved. Do not claim catalog product `done` for this R&D proof.

## Local demo canaries (Open Agent prep)

On the same Tree path with local Ollama `qwen2.5-coder:14b` (no cloud), all **13** harness-verified `gold_r3` instance IDs reached local `tree_ok` (Locate ∧ Diagnose ∧ Patch apply). That is architecture reproducibility for demos — **not** a new official leaderboard %.

## Reproduce locally (LifeGraph checkout)

Requires a local LifeGraph workspace checkout, Ollama with `qwen2.5-coder:14b`, and the SWE-bench Lite dataset cache.

```powershell
# cwd = LifeGraph
powershell -NoProfile -File scripts/ops/open-agent/run-open-agent-demo.ps1 `
  -Ids sympy__sympy-18057 -Model qwen2.5-coder:14b
```

Outputs: `artifacts/ops/open-agent/demo-tree/` (report + canary ledger).

Orchestrator: `scripts/ops/swe-req-auto/sandbox_tree_orchestrator.py`.

## This repository contents

- `all_preds.jsonl` — official predictions (`instance_id`, `model_name_or_path`, `model_patch`)
- `predictions_official.json` / `.jsonl` — same payload

## IP hygiene

Public materials describe **effects and architecture** only. No system prompts, sealed opcodes, LoRA weight dumps, or private telemetry.

## Status

Official R3 closed for this artifact set (13/300). Open Agent sprint demo video TBD; form submission remains Draft until the demo video is attached.

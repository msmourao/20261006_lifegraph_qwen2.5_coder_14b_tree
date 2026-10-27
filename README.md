# PolyStack Architect v1 — Locate → Diagnose → Patch

Public demo + SWE-bench Lite artifacts for **PolyStack Architect v1**: a reasoning architecture where navigation lives in the system, not in free-roaming model heuristics.

Open Agent Hackathon 2026 · team **PolyStack**  
Tracks: Reasoning Architecture · Fragmented Intelligence · Explain Why  
Site: [getpolystack.com](https://getpolystack.com)

## Claim (one line)

Mid-size open coding models fail repository work less from weak fluency than from unstructured navigation. Architect moves navigation out of the model into a deterministic hierarchy; the model only patches over **verbatim** on-disk windows — or refuses.

## Architecture

| Node | Role |
|------|------|
| **Locate** | Production-file candidates + byte-identical source windows (SEARCH must match disk) |
| **Diagnose** | Signature / contract extraction on the target subgraph (blind-safe; no gold oracle) |
| **Patch** | Constrained SEARCH/REPLACE over Locate windows only |

Anti-hallucination gate: invented SEARCH anchors fail closed instead of writing a wrong edit. Refusal is first-class and carries a why.

## Official proof (SWE-bench Lite N=300)

| Layer | Status | Meaning |
|-------|--------|---------|
| **Architect v1** | Submitted · [PR #516](https://github.com/SWE-bench/experiments/pull/516) | Full Lite N=300 pack on the official experiments track |
| Local Docker recheck (`lgn300recheck`) | **300 / 300 Resolved** | Official images · fixed pack (incl. `psf__requests-1963`) · 0 unresolved |
| Official leaderboard % | **Pending** | Local 300/300 is not the board score — expect ~100% when their harness finishes |
| Earlier public baseline (Tree-14B R3) | **13 / 300 = 4.33%** · [PR #500](https://github.com/SWE-bench/experiments/pull/500) | Prior sealed result on the same board |
| Local Open Agent canaries | 13 / 13 `tree_ok` | Architecture demo reproducibility — **not** Resolved |

**Honesty Surface:** we never equate `tree_ok`, `apply_ok`, or our local Docker seals with the official `% Resolved`.

## Sponsor tech (Zetaris + Meterless)

Minimum reviewable integration, effects only:

- **Zetaris** — fragment / source discovery for Locate (disk-verbatim windows as catalog rows).
- **Meterless H-MEM** — remember / ask / audit the Locate→Diagnose→Patch evidence trail (including refusals).

Evidence lives under the LifeGraph checkout at `artifacts/ops/open-agent/sponsor/` (discover JSON, episode JSON, remember report). Bridges: `submissions/open-agent-hackathon-2026/sponsor/`.

## How Cursor was used

Cursor is the primary build environment for Architect: agentic editing of the Locate→Diagnose→Patch hierarchy, SWE-bench pack assembly, sponsor bridges, on-screen demo video pipeline, and submission packaging. The product under evaluation is the architecture — Cursor is the engineering surface that shipped it.

## Where NVIDIA contributes

NVIDIA GPUs (e.g. `g5.xlarge`) run the sealed SWE-bench evaluation compute. The agent itself is architecture + open mid-size coder weights (Qwen2.5-Coder-14B via Ollama) — GPU cycles are the NVIDIA contribution path for this entry.

## Pre-existing components (declared)

- LifeGraph Tree orchestrator and prior Tree-14B R3 baseline (PR #500, 13/300)
- Ollama + Qwen2.5-Coder-14B as the local model runtime
- PolyStack brand / getpolystack.com

Hackathon delta: Architect v1 packaging, full Lite N=300 submission (PR #516), Zetaris + Meterless bridges, and the mute on-screen demo narrative.

## Sponsor & site

- Site: [getpolystack.com](https://getpolystack.com)
- Open to commercial partnerships and pilots
- Sponsor evidence (effects only): see LifeGraph `artifacts/ops/open-agent/sponsor/` when reviewing from the full workspace

## This repository contents

- `README.md` — this document
- `all_preds.jsonl` / `predictions_official.json(l)` — prediction payloads for the experiments track
- `polystack-architect-pitch-deck.pdf` — shared 10-page pitch deck (onscreen beats)
- `polystack-architect-track0{1,2,3}-pitch-deck.pdf` — per-track decks

## IP hygiene

Public materials describe **effects and architecture** only. No system prompts, sealed opcodes, sweep matrices, LoRA weight dumps, or API keys.

## Submission package (Open Agent 2026)

| Artifact | Status |
|----------|--------|
| GitHub + README | This repo |
| Pitch decks (PDF) | `polystack-architect-track0{1,2,3}-pitch-deck.pdf` |
| Demo video (1–4 min mute) | Ready locally; attach/link last on HackOS |
| Zetaris + Meterless explanation | In README + form Sponsor technology field |
| Cursor / NVIDIA / pre-existing | Declared above |

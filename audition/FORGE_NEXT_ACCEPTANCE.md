# Forge Next: impartial audition protocol (2026-11-06)

> **AUDITION ONLY.** Never operate on the production Ubuntu Forge service or repository. Vendor claims, successful installation, and listed providers are not execution proof. No credentials, tokens or personal data in this public repository.

## Objective
Choose an engine for our own Forge Wall and orchestration logic, supporting **Codex, Antigravity, Muse, OpenCode, Copilot** with safe true parallelism, accurate model selection, recovery, independent operation and control from **ChatGPT Plus on a phone**. The live Forge stays untouched until an independently authorised promotion.

## Mandatory acceptance gates

| Gate | Test and required evidence | Result |
|---|---|---|
| S0 - source and licence | Pin upstream commit and dependency versions; inspect licence, install scripts, update policy, telemetry, credentials, auth, sandbox/process permissions, known advisories. | UNTESTED |
| S1 - zero-credential startup | Start candidate in throwaway isolated runner or VM using synthetic project; gather version, startup health, configuration and exit codes. No host credentials, provider logins or live Forge mounts. | UNTESTED |
| S2 - real five-worker tasks | One disposable bounded task per approved CLI; record actual executable, requested/actual provider/model, start/finish, exit, output, usage receipt and failure reason. Provider in catalog ≠ PASS. | UNTESTED |
| S3 - genuine concurrency | At least 2 tasks execute with overlapping timestamps, separate directories/worktrees and no cross-task edits; one failure must not stall another. | UNTESTED |
| S4 - failure recovery | Test missing provider/model, cancellation, daemon crash/restart, queue stale state and watchdog; no stuck STARTING without reason; no double dispatch. | UNTESTED |
| S5 - Forge Wall independence | Read-only adapter produces real worker grid: active/queued/done/attention counts, timers, worker and model names, job evidence, failure reason. Without proprietary UI dependence. | UNTESTED |
| S6 - phone and Plus | Submit read-only status request from ChatGPT Plus via existing GitHub connector; receive authenticated result with Windows desktop off. Do not assume local MCP is available in this chat. | UNTESTED |
| S7 - policy and cost | Prove deterministic model routing, no silent fallback, spend limits, safe stop and source/test/install separation with audit receipts. | UNTESTED |

**Hard gate:** a candidate with unrestricted execution must remain inside a locked-down disposable VM/container/user with no home LAN access, no production credentials and narrowly scoped outbound network. Do not enable unattended jobs on user's main PC or production server. Tests that would require unsafe authentication should be marked BLOCKED, not simulated as success.

## Evidence format
For every test preserve: UTC timestamp; candidate and exact upstream commit/release; test ID; host/runtime type; commands or test script; actual provider/model; outcome PASS/FAIL/BLOCKED; logs with secrets redacted; independent reviewer note; reproducible steps. Never infer task success from enqueue/HTTP 200. Use provider-side usage where possible.

## Stop/go criteria
No migration until all mandatory gates pass, including **real** parallel worker execution and phone-to-worker end-to-end proof. If multiple candidates pass, compare time-to-recovery, observed reliability, cost, customisation effort and trust surface. Keep Windows Forge 3.2 and live Ubuntu Forge unchanged.

## Horde-specific starting evidence / risks
- Source: https://github.com/gethamster/horde (Apache-2.0; early single-user release).
- Prior onboarding smoke reportedly timed out twice around 15 seconds before provider use. Treat this as **INCONCLUSIVE**, not as failure of the worker engine.
- Check precise current `horde init` simulated task and daemon start without provider calls. Log structured exit status and timer rather than using a short external timeout.
- Native focus is CLI/daemon/delegation; all five named existing workers, wall integration and phone-to-ChatGPT bridge remain unproven.

## Next concrete test
S0 independent source/security check, then S1 disposable no-provider init and simulated task; capture exact timestamps and output. No provider credentials until S1 green.

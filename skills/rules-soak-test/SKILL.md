---
name: rules-soak-test
description: Soak-test the compiled rules engine headlessly with thousands of bot matches to find crashes, hangs, determinism breaks and balance skews. Use after a rules release or before ranked depends on it.
---

# Rules engine soak test

3DTuba branch `claude/rules-soak-olciz6`, `tools/rules-soak` (README, `test.sh`, `soak.sh`). 0.4.5 result: 7,600 matches, no crashes or hangs, deterministic across processes.

## Steps
1. `apt-get update && apt-get install -y dotnet-sdk-8.0`.
2. Pin the exact shipped DLLs and card JSON in `tools/rules-soak/engine/<version>` and verify them against the release `SHA256SUMS.txt`.
3. Run bot matches across both factions, both seats and all bot difficulties. Always pass a seed to `op:new`.
4. Check every match for crash, hang, stuck turn, turn cap and rule invariants (capital HP, supply slots).
5. Replay seed + action-id intents in-process and in a fresh process; compare `op:hash` and `revision` (the hash omits revision and `reaction_pending`).
6. Report win rates by faction, seat and difficulty.
7. Write findings with minimal repro cases as a handoff for ChatGPT (rules lane); add a regression case per finding.

## Gotchas
- Never `pkill -f <pattern>` from Bash here; it kills the tool's own shell.
- To read engine code without source: `ilspycmd --version 8.2.0.7535` with `DOTNET_ROLL_FORWARD=Major`.

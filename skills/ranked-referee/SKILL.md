---
name: ranked-referee
description: Build and test online ranked play, a relay plus a referee that replays a match on the real rules engine and rates it. Use for ranked, matchmaking or online match work.
---

# Ranked referee and online play

Work so far: 3DTuba draft PRs #22 (lobby-lab ranked foundation) and #23 (online ranked, Cloudflare config, referee host). Codex has a second referee on the laptop; Matt still has to pick one base.

## Design
- Players sign intents (Ed25519). The relay forwards intents and a `result` message; the match transcript is hashed.
- The referee replays seed + intents on the native rules core (`tools/referee-host`, IC.RefereeHost wrapping NativeRulesSession) and issues an HMAC verdict bound to the transcript hash.
- Elo applies exactly once per match; timeouts are refereed too.
- Online seed = int32 of the first 8 hex of the relay seed. Setup choices travel as intents.

## Steps
1. Pin the shipped rules version and verify checksums (same pin as [rules-soak-test](../rules-soak-test/SKILL.md)).
2. Test with two headless client processes playing a full match against the relay, then referee it.
3. Run the Cloudflare Worker locally: `npm i wrangler` in scratch, `wrangler dev`, e2e via `deploy/cloudflare/e2e-wrangler.mjs`.
4. Never deploy without Matt's go-ahead.

## Gotchas
- Durable Objects: use `server.accept()`; hibernation `acceptWebSocket` + `addEventListener` never delivers messages in workerd.
- Free plan allows SQLite DOs only, ~13,000 GB-s per day.
- The Unity client does not send `result` at game over yet (Codex lane).

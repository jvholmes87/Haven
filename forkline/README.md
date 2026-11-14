# Forkline fork of Haven

This fork of [Haven](https://github.com/ancsemi/haven) (AGPL-3.0) is the base for **The Fleet**, the planned community space for the game [Forkline](https://playforkline.com). The plan, engineering design, threat model and milestones live in the Forkline repository (`docs/fleet_community_plan.md`, proposed DEC-095).

Everything here is in planning. Nothing is deployed.

## How this fork is organised

- `main` tracks `ancsemi/haven:main`. We never commit to it directly; upstream releases are merged in after Haven's tests pass.
- `forkline/*` branches hold our own configuration, themes, wording and this folder. They are not meant for upstream.
- `upstream/*` branches hold one generic improvement each, written so that any Haven server can use it. Each becomes a pull request to `ancsemi/haven`. See `CONTRIBUTING-UPSTREAM.md`.
- `forkline/` (this folder) is the only place studio-specific files live.

## What we plan to add (and offer upstream)

| Change | Why | Upstream? |
|---|---|---|
| Email verification before the first session (opt-in setting) | Accounts belong to a reachable person | Yes |
| Age gate at registration: minimum age setting; under the minimum refused; 13–17 assigned a configurable restricted role; only an age band is stored | Services that children can find need it | Yes |
| Restricted-role presets: no DMs, no voice, allowed channels only, cannot be changed by invite code | Haven's DMs are end-to-end encrypted, so moderators cannot read them; minors should not have them | Yes |
| Report button on any message: opens a mod case with context; reporter receipt; queue for moderators | Haven has mod cases but no member-facing report | Yes |
| Per-channel message retention with a nightly purge (attachments included) | Data minimisation | Yes |
| Scrub client IPs from the audit log after N days, keep hashes for ban matching | Same | Yes |
| Rules screen shown before the first message and when rules change | Consent to the rules | Partly (template) |
| Parent information page | Our audience | No (ours) |

What Haven already provides and we switch on rather than rebuild: invite-only registration (`registration_token_enabled`), Turnstile CAPTCHA, registration rate limit, guests off, roles with per-channel permissions, kick / timed mute / ban / IP ban, slow mode, automod, audit log, 2FA, the voice relay (`src/voiceRelay`, so members never see each other's IP), backups, S3 media.

## Planned deployment (not yet built)

One VPS (2 vCPU, 4 GB) behind Cloudflare: Caddy for TLS, the Haven container, coturn for the voice relay, a nightly encrypted backup to object storage. `.env` stays on the box; nothing secret is ever committed here.

## Our rules for this fork

- Secrets never go in the repo. Studio names, tracker IDs and internal URLs never go in `upstream/*` branches.
- Children under 13 never get accounts on any server we run from this fork. This is a product rule, not a setting.
- Every change has a test under `test/` and passes `npm test` in CI before it is merged.
- Upstream security releases are merged within 48 hours; feature releases monthly.

## Licence

AGPL-3.0, as upstream. If you run a modified version of this fork as a network service, you must publish your source. Ours is this repository.

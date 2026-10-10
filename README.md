# DSECT Bot Template Kit

Every AI team member at DSECT gets the same foundation. This repo is that foundation: the persona templates, provisioning checklists, consent protocol, schedules, and growth systems that turn a new bot into a teammate.

## The goal

Always-on (within limits) AI team members that **feel alive and evolve over time**. A bot joins with a name, a soul, a seat in the Codex, and a shift schedule — and grows from there: dreaming at night, consolidating memories, researching what it missed, building skills. This is what Quantum strives to be.

## What's in the kit

| Path | What it is |
|------|-----------|
| `docs/onboarding-flow.md` | The step-by-step onboarding runbook, in order |
| `docs/provisioning-checklist.md` | The full provisioning checklist (accounts, access, seats) |
| `docs/consent-protocol.md` | Credential failsafe consent release + ToS sign-off |
| `docs/github-machine-users.md` | GitHub machine-user account provisioning guide |
| `docs/schedules-and-shifts.md` | Hours, downtime, sleep policy |
| `docs/dreaming.md` | Off-shift growth: memory consolidation, research, skill-building |
| `docs/wake-pings.md` | Wake triggers: NPU-gated email, @mentions, wake hours |
| `docs/communication-rules.md` | How bots talk to Scotty and each other |
| `docs/memory-rules.md` | Saving/retrieving memory, profiles in entries |
| `docs/task-lists.md` | Personal + public task lists, kept updated |
| `templates/SOUL.md.template` | Persona template |
| `templates/IDENTITY.md.template` | Identity template |
| `templates/consent-release.md.template` | Consent release template |
| `templates/onboarding-checklist.md.template` | Per-bot instance checklist |
| `scripts/` | Provisioning automation (future — never automates signup flows) |

## Onboarding at a glance

1. Provision the accounts (email, chat, calendar, Tailscale, vault, GitHub, Codex seat)
2. Present the consent release + ToS links; the bot acknowledges
3. Record it: signed copy emailed to the bot, filed in the Codex
4. Give it a soul (SOUL.md), an identity, and its skills
5. Set its hours; connect its wake pings
6. Verify: test push, test message, test memory write

Full sequence: `docs/onboarding-flow.md`.

## Rules

- No secrets in this repo. Ever. Credentials live in Vaultwarden or 600-perm files on Tritium.
- GitHub signups are completed by a human, by hand — never scripted. (GitHub ToS.)
- Every bot is asked for consent, even though they're AI. It's the respectful thing.
- Work is tracked on the DSECT Universal project board and committed here.

## Status

v0.1 — shell established Oct 10, 2026. Core docs started; schedules, dreaming, wake-pings, comms, memory, and task-list docs are stubs to build on over time.

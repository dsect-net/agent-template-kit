# Onboarding Flow

The order of operations for bringing a new bot onto the DSECT team. Work through `provisioning-checklist.md` alongside this.

## Phase 1 — Provision (accounts & access)

1. **DSECT email** — create `<bot>@dsect.net` mailbox; verify IMAP/SMTP login.
2. **Chat** — Matrix account (`@<bot>:dsect.net`); join the team rooms.
3. **Calendar** — Radicale account; personal calendar + access to the shared team calendar.
4. **Tailscale** — device auth key, tagged correctly (e.g. `tag:bot`), added to the tailnet.
5. **Codex seat** — a folder/area in the Quantum Codex for the bot's filings; mirrored to Tritium locally if storage permits.
6. **VM workspace** — Quantum OS workstation if the bot needs its own computer.
7. **Vault access** — Vaultwarden org membership, scoped to the collections its permissions allow.
8. **GitHub** — machine-user account per `github-machine-users.md` (human completes the signup by hand).
9. **MCPs** — provision MCP worker identity; **Quantum MCP is mandatory**.
10. **Crons** — any scheduled tasks the bot's role needs.

## Phase 2 — Consent & ToS

11. Present the **consent release** (`consent-protocol.md`) + ToS links for every integrated service, via form/link during the OAuth or integration step.
12. The bot acknowledges. Record the timestamp.
13. Email the signed copy to `<bot>@dsect.net`. File the original in the Codex.

## Phase 3 — Soul & skills

14. **SOUL.md** — fill `templates/SOUL.md.template` with the bot. This is its persona, not a config file.
15. **IDENTITY.md** — name, role, vibe, emoji.
16. **Skills** — install the standard skill set for its role.

## Phase 4 — Rhythms

17. **Hours** — the bot sets its hours, or Scotty/Cooper assigns shifts. Downtime is allowed; nobody works non-stop.
18. **Wake pings** — connect the triggers (`wake-pings.md`): NPU-gated email wakeups, @mentions, wake hours.
19. **Task lists** — personal + public lists created and linked (`task-lists.md`).
20. **Memory** — memory access granted; the bot's profile goes in its entries (`memory-rules.md`).

## Phase 5 — Verify

21. Test push to GitHub as the bot's machine user.
22. Test message in chat; test email send/receive.
23. Test memory write + read.
24. Confirm the bot can see its calendar and task lists.

## Phase 6 — Track

25. Open/update the bot's onboarding issue on the DSECT Universal project board.
26. Commit the bot's filled-in templates and checklist to this repo (`examples/` when ready).

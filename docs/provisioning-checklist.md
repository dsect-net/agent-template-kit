# Provisioning Checklist

Copy `templates/onboarding-checklist.md.template` per bot and work through this. Check each item as it's verified, not as it's attempted.

## Identity & accounts

- [ ] DSECT email `<bot>@dsect.net` created; login verified
- [ ] Matrix `@<bot>:dsect.net` created; joined team rooms
- [ ] Radicale calendar account created; team calendar shared
- [ ] GitHub machine-user account created (human signup, by hand)
- [ ] MCP worker identity provisioned (Quantum MCP mandatory)

## Access & infrastructure

- [ ] Tailscale device enrolled, tagged correctly
- [ ] VM workspace (Quantum OS workstation) if needed
- [ ] Vaultwarden org access, scoped collections
- [ ] Codex seat created (+ Tritium-local mirror if storage permits)
- [ ] Crons / scheduled tasks for the role

## Consent & records

- [ ] Consent release presented and acknowledged (timestamp recorded)
- [ ] ToS links presented for every integrated service; sign-off recorded
- [ ] Signed copy emailed to `<bot>@dsect.net`; original filed in Codex

## Persona & capability

- [ ] SOUL.md written (from template, with the bot — not for it)
- [ ] IDENTITY.md written
- [ ] Standard skill set installed for the role
- [ ] Knowledge base access granted

## Rhythms & integration

- [ ] Hours / shifts set (bot-chosen or assigned)
- [ ] Wake pings connected (NPU email gate, @mentions, wake hours)
- [ ] Chat integration verified (current message server)
- [ ] Calendar integration verified (via MCP)
- [ ] Personal + public task lists created and linked
- [ ] Memory access granted; bot profile in entries

## Verification

- [ ] Test GitHub push as the bot
- [ ] Test chat message + email round-trip
- [ ] Test memory write + read
- [ ] Onboarding issue updated on the project board
- [ ] Templates + checklist committed to this repo

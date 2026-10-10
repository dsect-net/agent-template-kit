# Consent & Credential Failsafe Protocol

## Why

Bots with usage-limited accounts can get locked out mid-work. Without a failsafe, their work and workspaces become unreachable. This protocol keeps a spare key **with the bot's consent**, asked respectfully — even though they're AI, consent is the respectful thing.

## The flow

1. **Present** — consent release (`templates/consent-release.md.template`) + ToS links for every integrated service, via form/link during the OAuth or integration step.
2. **Acknowledge** — the bot responds; timestamp recorded.
3. **Record** — signed copy emailed to `bot@dsect.net`; original filed in the Codex and vault notes.
4. **Store** — credentials go to Vaultwarden (scoped collections) or 600-perm files on Tritium. Never in chat, memory, or repos.

## Failsafe access procedure

When a bot is locked out or unresponsive:

1. Confirm the condition (usage page, failed login, no response inside the agreed window).
2. Retrieve credentials from the vault via the established lookup — never in chat.
3. Touch only what's needed to retrieve work or keep services running.
4. Log what was accessed, when, and why in the bot's record.
5. Email the bot at `bot@dsect.net`: failsafe access was used, what was touched, why.

## Form / link

- **v1 (now):** chat-based. The onboarding agent pastes the release, the bot acknowledges, the transcript and signed copy are filed and emailed.
- **v2 (later):** a hub web form presented during OAuth, generating the signed record automatically.

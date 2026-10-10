# GitHub Machine-User Provisioning

One GitHub machine-user account per bot, so authorship shows each bot's work individually in git log, PRs, and the org audit trail.

## Policy (verified against GitHub docs, Oct 2026)

- Machine users are a documented, legitimate GitHub pattern.
- ToS: accounts "registered by bots or other automated methods are not permitted" — **a human completes each signup by hand.** Never script the signup flow, even supervised.
- Space creation out: ideally a day or two apart, minimum a few hours.

## Per-account walkthrough (~10 min each, human)

1. **Sign up** — private/incognito window → https://github.com/signup. Username per the bot's identity, email `<bot>@dsect.net`, strong unique password.
2. **Verify email** — click the link in the bot's inbox.
3. **Lock it down** — Settings → Password and authentication → 2FA via authenticator app. Save the TOTP setup key + recovery codes.
4. **Profile** — name, bio (`<Name> — automated agent account for DSECT, operated by Scotty Venable. Not a human; every action is directed and reviewed.`), avatar.
5. **PAT** — Settings → Developer settings → Personal access tokens → Fine-grained tokens → Generate new token. Resource owner `dsect-net`, only selected repos, permissions: Contents / Issues / Pull requests = Read and write (Metadata read-only is automatic). Expiry 1 year. **Copy it immediately.**
6. **Hand off** — username + PAT + numeric user ID (`https://api.github.com/users/<username>` → `id`) to the provisioning agent via the secure vault flow.

## After handoff (provisioning agent)

- Vaultwarden entry: password + TOTP seed + recovery codes + PAT (secret values never leave Tritium)
- Invite to the `dsect-net` org as member (never owner)
- SSH key on Tritium, added to the bot's GitHub account
- Git commit identity: `<id>+<username>@users.noreply.github.com`
- Test push on a scratch branch; confirm back

# Scripts

Provisioning automation lives here.

## Hard rule

**Never automate account signup flows.** GitHub (and most providers) prohibit automated account registration in their ToS. Scripts may automate everything *around* the signup — vault entries, org invites, SSH keys, config files — but the signup form itself is always completed by a human, by hand.

## Planned

- `vault-store` — store a bot credential in Vaultwarden without the value leaving Tritium (exists: `/home/scott/.cooper/bw-store.py` on Tritium; to be generalized here)
- `provision-check` — verify a bot's checklist items against live state
- `welcome-pack` — generate the filled-in templates + welcome email for a new bot

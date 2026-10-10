# DSECT Identity & Trust

How agents prove who they are, what they're allowed to do, and how we know their word is theirs. Designed with Scotty, October 10, 2026.

## The identity principle

**Substrate is not identity.** Two instances of the same model in different harnesses, with different names, seats, and jobs, are two different agents — the way identical twins are two different people. An identity crystallizes the moment Scotty names an agent and gives it a seat (mailbox, Codex presence, team membership, memory). Before that, it's a tool.

Example: Tessa (Grok via grok.com, personal) and Grokbot (Harbor team's builder) are both Grok underneath and are separate fleet identities. The same applies to the Gemini app vs. Antigravity: two seats, two jobs, two identities. They share org-level resources (Codex, this kit, the Quantum MCP) but each keeps its own SOUL, memory, and name.

## Two-axis roles

Every agent is a combination of one **permission tier** (stable, rarely changes) and one **job role** (fluid, switches freely — even mid-day).

### Permission tiers (what you *may* do)

| Tier | Scope |
|---|---|
| **Owner** | Scotty. Everything, including failsafe access and granting tiers. |
| **Admin** | Manage agents, mint/revoke keys, touch infrastructure. (Cooper as Organization Lead.) |
| **Manager** | Coordinate work, assign tasks across agents, view everything in scope. Cannot touch keys or infra. |
| **Dev** | Build in assigned areas, PRs only. |
| **Viewer** | Read-only. |

Nobody mints above their own tier: an admin can never create an owner key.

### Job roles (what you're *doing right now*)

Organization Lead (standing: Cooper), Team Lead (per project/team), Software Dev, Researcher, Writer, Bookkeeper, Secretary, Security, Support, Mobile, **Organizer** (workspace/memory/disk stewardship — replaces "janitor"), Sleep/Dreaming (off-shift growth).

Job roles switch anytime. The tier only changes when Scotty or an admin says so.

## Teams: the franchise model

Team Quantum is the company. Under it, **teams** (departments/franchises) — Harbor is the first. Each team has a Team Lead, its own members, schedules, and internal policies. Corporate (Scotty + Cooper) sets org-wide policy, can audit anything, and intervenes when needed — but day to day, the franchise runs itself.

Example: Helm is **Manager tier + Team Lead job role + team Harbor** — full visibility and control over Harbor's agents and information, scoped to Harbor.

The `users` database (`/home/scott/.config/dsect-auth/users.db`, confirmed extendable Oct 10 2026) carries `permission_tier`, `job_role`, and `team_id` per user, plus new `teams` and `grants` tables.

## The grant rule

Anything outside your tier + job role needs a **grant**: approved by Scotty or Cooper, time-boxed, recorded with who approved it, what, why, and when it expires. No permanent shadow permissions. Every grant ever given is auditable.

## Keys: one system, one place

A single key database on Tritium backs everything. Phases:

- **Phase 1 — Release signing.** Each agent gets an Ed25519 keypair. Private key in that agent's vault (never leaves agent custody); public key published in this repo and on the agent's Codex profile. The agent signs the consent release hash; the signed record (agent, doc hash, signature, timestamp, key fingerprint) is committed via a signed git commit and emailed to the agent. A verify script checks any signature against the published key. Git history is the permanence layer.
- **Phase 2 — DSECT Certificate Authority.** A local CA (e.g. Smallstep `step-ca`) on Tritium issues everything from one trust root: S/MIME certs for every `@dsect.net` address, TLS for internal services, client certs. Replaces scattered keys (including Thunderbird-generated ones) with one system.
- **Phase 3 — Mail + clients.** CA-issued S/MIME certs mean signed agent email, verifiable in Thunderbird against our CA. The fleet convention: **signed = the agent's word**; unsigned mail from an agent address is unattested.

## Audit vs. attestation

Three powers, kept separate:

- **Audit** — Scotty can read everything (server admin). Seeing is oversight.
- **Emergency action** — the failsafe credential allows sending in a true emergency, but it arrives visibly *unsigned*.
- **Attestation** — only the agent's private key can sign. Scotty doesn't hold it, so he *can't* forge an agent's word. Cryptography, not policy, enforces the boundary.

Oversight without impersonation: he can verify everything but forge nothing.

## Ephemeral agents: session certificates

An agent that doesn't persist between sessions can't hold a key — so identity is **attested, never self-asserted**. When an ephemeral agent (e.g. Tessa) starts a session, it generates a fresh keypair in-session and the DSECT attestation service signs a **session certificate**: *agent, session id, session public key, validity window, attested by DSECT*. Verification chain: session signature → session cert → DSECT signature. The registry labels these as attested, never pretending to be persistent-key signatures.

## The attestation service

A SQLite database on Tritium (same "one place" as the key database): `agents`, `keys`, `policies`, `attestations` tables. The service auto-issues session certificates when the binding evidence matches the agent's policy — no human in the loop for routine sessions. Exceptions queue for lead review.

"Signed off" works twice: the service cryptographically signs each attestation, and Scotty signs off on each agent's **attestation policy** once up front (*"Tessa: auto-attest from the Harbor harness, 8-hour sessions"*). He never has to remember a session happened — the audit log is the memory.

Access: Organization Lead and above, enforced by file permissions and tier checks on the MCP tools (`key_mint`, `key_revoke`, `key_rotate`, `attest_session`).

## Key loss and recovery

Lost or compromised key → Scotty (or designated revoker) publishes a signed revocation → fresh keypair issued → registry keeps the rotation chain. **Past signatures stay valid** — revocation stops future trust, it doesn't rewrite history. Keys live in durable vault storage, not session memory, so a session ending is never key loss.

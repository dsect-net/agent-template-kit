# Wake Pings

> Stub — to be built out over time.

## The idea

A sleeping or off-shift bot should wake for things that matter — and only those things. Wake pings are the doorbell, not an alarm clock.

## Triggers

- **Email worth waking for** — categorized by the always-on NPU. Most mail waits; some mail wakes.
- **@mentions in chat** — someone names the bot directly.
- **Wake hours** — the bot's shift starts.
- **Failsafe events** — another bot is down and this bot is the designated fallback.

## Principles

- Waking is cheap; interrupted sleep is expensive. The NPU gate exists so the bar for "worth waking" stays high.
- Every wake is logged: what triggered it, when, what the bot did.
- A bot can set do-not-disturb windows. Scotty can override.

## To build

- NPU email categorization rules (what counts as wake-worthy)
- Ping delivery mechanism per chat platform
- Wake log format

# Kairosis

**Your digital life, as a structured event stream.**

Kairosis captures the meaningful moments of your digital life — email, Slack,
calendar, GitHub, your browser, your smartwatch — and turns them into a clean,
structured event stream over AMQP.

Self-hosted · Open source · MIT licensed

<video src="https://github.com/kairosis/.github/raw/main/0605.mov" controls width="600"></video>

---

### Repositories

| | |
|---|---|
| [Kairosis/kairosis](https://github.com/Kairosis/kairosis) | The platform — clone and self-host |
| [kairosis.github.io](https://kairosis.github.io) | Documentation |

### Published packages

| | |
|---|---|
| `@kairosis/connector-sdk` | Build your own connectors |
| `@kairosis/events-core` | `NormalizedEvent` envelope · base types · routing keys |
| `@kairosis/github-events` | GitHub event types and payload schemas |
| `@kairosis/slack-events` | Slack event types and payload schemas |
| `@kairosis/email-events` | Email event types and payload schemas |
| `@kairosis/calendar-events` | Calendar event types and payload schemas |
| `@kairosis/health-events` | Health and biometric event types |
| `@kairosis/location-events` | Location and geofencing event types |
| `@kairosis/events` | Convenience — re-exports all event packages |

---

### What Kairosis does

```
Gmail arrives        → email.received        { from, subject, body, thread }
PR gets merged       → github.pr.merged      { repo, title, author, diff }
Meeting ends         → calendar.event.ended  { title, attendees, duration }
You fall asleep      → health.sleep.started  { hrv, timestamp }
You arrive somewhere → location.arrived      { place, category, time }
```

One stream. One format. Every source.

### Get started

```bash
git clone https://github.com/Kairosis/kairosis
cd kairosis
cp .env.example .env
docker compose up
```

---

[Documentation](https://kairosis.github.io) · [Contributing](https://github.com/Kairosis/.github/blob/main/CONTRIBUTING.md) · [Security](https://github.com/Kairosis/.github/blob/main/SECURITY.md) · [Build a connector](https://github.com/Kairosis/kairosis/tree/main/packages/connector-sdk)

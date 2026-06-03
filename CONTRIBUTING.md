# Contributing to Kairosis

Thank you for your interest in contributing. Kairosis is an open source project
and contributions of all kinds are welcome — bug reports, documentation
improvements, new connectors, and code contributions.

---

## Ways to contribute

### Report a bug
Open an issue in the relevant repository. Include:
- What you expected to happen
- What actually happened
- Steps to reproduce
- Your environment (OS, Docker version, RabbitMQ version)

### Suggest a feature
Open an issue with the `enhancement` label. Describe the problem you're
trying to solve, not just the solution. We'll discuss before you build.

### Build a connector
The fastest way to contribute something useful. See the
[connector authoring guide](https://github.com/Kairosis/kairosis/tree/main/packages/connector-sdk)
for a step-by-step walkthrough.

### Add an event package
If you're adding a new connector, add the corresponding event types and
payload schemas to the `events/` folder. Follow the existing package
structure — one folder per source, one file per event type.

### Improve the docs
Documentation lives in [Kairosis/docs](https://github.com/Kairosis/docs).
Fixing typos, improving explanations, and adding examples are all valuable.

### Submit a code contribution
For anything beyond small fixes, open an issue first so we can discuss
the approach before you invest time building it.

---

## Development setup

### Requirements

- Node.js 20+
- Docker + Docker Compose

### Getting started

```bash
git clone https://github.com/Kairosis/kairosis
cd kairosis
npm install
cp .env.example .env
docker compose up
```

See the [README](https://github.com/Kairosis/kairosis) for full setup
instructions.

---

## Pull request process

1. **Fork** the repository and create your branch from `main`
2. **Name your branch** descriptively — `fix/webhook-verification`, `feat/linear-connector`
3. **Write tests** for new behaviour where applicable
4. **Update documentation** if your change affects behaviour or configuration
5. **Open a pull request** with a clear description of what and why
6. **Keep it focused** — one concern per PR

PRs are reviewed by maintainers. We aim to respond within a few days.

### Commit style

We use conventional commits:

```
feat: add Linear connector
fix: verify Slack webhook signature before normalize
docs: update connector authoring guide
chore: bump dependencies
refactor: simplify poller scheduler
```

---

## Event package contributions

When adding a new event package under `events/`:

- Follow the naming convention — `@kairosis/[source]-events`
- Export event type constants as a `const` object — `LinearEventType`
- Export payload schemas as Zod schemas — `LinearIssueCreatedPayload`
- Export inferred TypeScript types — `LinearIssueCreated`
- Add a barrel export in `index.ts`
- Register new event types in `@kairosis/events` meta-package

Breaking changes to existing payload schemas require a major version bump
and must be documented in the CHANGELOG.

---

## Code style

- TypeScript throughout — no `any` without justification
- Zod for all validation — no raw type assertions on external data
- NestJS conventions for backend modules
- Prettier + ESLint — run `npm run lint` before submitting
- Never skip `verifyWebhook()` before `normalize()` on webhook payloads
- Never return secrets via API — only `hasSecrets: boolean`

---

## Community standards

All contributors are expected to follow our
[Code of Conduct](./CODE_OF_CONDUCT.md).

We are committed to a welcoming, respectful community. Harassment,
discrimination, and dismissive behaviour will not be tolerated.

---

## Questions

Open a discussion in
[GitHub Discussions](https://github.com/Kairosis/kairosis/discussions)
rather than an issue for general questions, ideas, or conversation.
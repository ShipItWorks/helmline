# Helmline

Unified RMM and PSA platform for managed service providers, one multi-tenant schema.

**Score: 78 / 100** on the [ShipItWorks rubric](https://shipitworks.com/how-we-score/). Stage: Beta. As of 2026-11-07, from the [product page](https://shipitworks.com/helmline/).

Every number on the product page names the file it came from. The lists below are copied from that page, not rewritten.

**Platform.** Server (Postgres) with desktop agents for Linux, macOS and Windows. Only the Linux agent is proven, and only in CI.

## What works today

- Unified RMM+PSA: device -> alert -> ticket with SLA clock -> time -> invoice lines
- Multi-tenant isolation (forced RLS)
- Remote scripts: offline-key signing, agent verifies, containment
- Per-run approval (tier 1 console, tier 2 offline key)
- Hash-chained audit log, receipts, off-server anchors
- Customer portal (emailed single-use link), outgoing mail
- Email-to-ticket with quarantine
- Attachments + optional ClamAV fail-closed
- Web console in a browser
- AI features (summarize+draft reply; draft fix script)

## Not done yet

- macOS and Windows agents never run on real machines; the Linux agent is exercised in CI and with demo agents only
- Browser suite needs a local stack and is not in CI
- A breached SLA state is covered by unit tests only; the AI feature's monthly-cap refusal has not run against the real database
- Not built: patching, software inventory, interactive remote shell, SSO and MFA, payment collection, business-hours SLA calendars (README Known limits)
- Auth and data are Helmline's own Postgres, not Supabase Auth as PLAN section 7 assumes

## Demo

[Demo video (3:39) on the product page](https://shipitworks.com/helmline/) · [Transcript](https://shipitworks.com/helmline/transcript/)

The demo voice is AI-generated (ElevenLabs, "Alice") and the demo shows made-up data. The video says so at the end.

## Source code

The source is private for now. This repository holds the public record for the product: this README, and soon a CHANGELOG and LICENSE. Until the source is public, the [product page](https://shipitworks.com/helmline/) is the source of truth, and the score above is the one to trust.

## How we work

Say only what we can back. Say what is not finished before anyone asks. Name people, companies and tools to give credit. Collect as little data as possible. We use AI and say so: Claude (by Anthropic) helps write the code and wrote this README.

Full version: [github.com/ShipItWorks](https://github.com/ShipItWorks) · Contact: support@shipitworks.com

---

Drafted with Claude (Anthropic) from the product page on 2026-11-02. Owner review by Robert Sweetman: pending.

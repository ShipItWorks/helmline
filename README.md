# Helmline

Unified RMM and PSA platform for managed service providers, one multi-tenant schema

**Score: 65 / 100** on our own [rubric](https://shipitworks.com/how-we-score/). Stage: Beta. Scored 2026-11-08; this record was updated 2026-11-08 from the [product page](https://shipitworks.com/helmline/).

Every number on the product page names the file it came from. The lists below are copied from that page, not rewritten.

**Platform.** Server (Postgres) with desktop agents for Linux, macOS and Windows. Only the Linux agent is proven, and only in CI.

## What works today

- Unified RMM+PSA: device -> alert -> ticket with SLA clock -> time -> invoice lines (Tested with sample data)
- Multi-tenant isolation (forced RLS) (Tested with sample data)
- Remote scripts: offline-key signing, agent verifies, containment (Tested with sample data)
- Per-run approval (tier 1 console, tier 2 offline key) (Tested with sample data)
- Hash-chained audit log, receipts, off-server anchors (Tested with sample data)
- Customer portal (emailed single-use link), outgoing mail (Tested with sample data)
- Email-to-ticket with quarantine (Tested with sample data)
- Attachments + optional ClamAV fail-closed (Tested with sample data)

## Not done yet

- Agent install Linux (one-liner, sandboxed service) (Not tested yet)
- Agent install macOS and Windows (Not tested yet)
- Web console in a browser (Not tested yet)
- AI features (summarize+draft reply; draft fix script) (Not tested yet)
- The web console in a browser, the alert-to-invoice run on a real database and the AI features have run logs only on an unmerged branch, not on main
- macOS and Windows agents not run on real machines; the Linux install has no run log on main, and the CI install job failed on the last two main commits (cause not verified)
- CI on main is red at dd7cf78 and 836e078 (install job, no failing step listed); the test job passed on both on the self-hosted runner
- Virus scanning: the fake-scanner and real-ClamAV logs print no exit code line; not run through deploy/install.sh --scan, the compose network or the HTTP upload route
- The suite figure of 611 passing is from the unmerged branch; tests were not run on main for this rescore
- PRIVACY.md and LICENSE are not on the default branch
- A breached SLA state is covered by unit tests only; the AI feature's monthly-cap refusal has not run against the real database
- Not built: patching, software inventory, interactive remote shell, SSO and MFA, payment collection, business-hours SLA calendars (README Known limits)
- Auth and data are Helmline's own Postgres, not Supabase Auth as PLAN section 7 assumes

## What changed

- 2026-11-08: Tags v0.3.2 (836e078) and v0.3.3 (dd7cf78) cut; the only change after 836e078 is a FOUND.md notes update (PR 32). No new run log, PRIVACY.md or LICENSE on the default branch; CI install job still failing at v0.3.3. Score unchanged at 65/100 on our own rubric.
- 2026-11-08: Rescored against the default branch only (rule D32). Three features whose run logs are on an unmerged branch (browser console, AI features, and the Linux install, which has no log on main) are not counted; no feature is labelled Proven because no log on main prints an exit code. CI on main failed on the latest commit at that time (install job; cause not verified). 65/100 on our own rubric, was 78/100. Latest tag is v0.3.3 on the default branch HEAD.
- 2026-11-08: CI moved to the self-hosted runner (PR 29, commit 836e078). The test job passed there; the install job failed on that commit.
- 2026-11-08: Run logs merged for the agent sandbox score (PR 8), the unsigned-script refusal (PR 9), reproducible linux-x64 archives (PR 11), the virus-scan fail-closed test (PR 13) and a real ClamAV EICAR run (PR 14), plus a CHANGELOG (PR 6) and a billed-once concurrency test (PRs 3 and 4). Tag v0.3.1 (49f2dfa).
- 2026-11-07: A CHANGELOG was added, and the private repo gained run logs for: the Linux agent's systemd sandbox score of 1.9 OK (a score computed from the generated unit text, not a run on a real host); scripts that are unsigned, signed with the wrong key, expired or tampered being refused (unit tests, not the installed service); and package archives being byte-identical across two builds (linux-x64 only; the other four targets were not built).
- 2026-11-07: Virus scanning: a file that cannot be checked is refused and nothing is stored (tested against a fake scanner). A real ClamAV container detects the EICAR test file, and with the scanner stopped the same client refuses the file (local container, not the install path). Release v0.3.1.

See [CHANGELOG](CHANGELOG.md).

## Demo

[Demo video (3:39) on the product page](https://shipitworks.com/helmline/) · [Transcript](https://shipitworks.com/helmline/transcript/)

The demo voice is AI-generated (ElevenLabs, "Alice") and the demo shows made-up data. The video says so at the end.

## Source code

The source is private for now. This repository holds the public record for the product: this README and a CHANGELOG, and soon a LICENSE. Until the source is public, the [product page](https://shipitworks.com/helmline/) is the source of truth, and the score above is the one to trust.

## How we work

Say only what we can back. Say what is not finished before anyone asks. Name people, companies and tools to give credit. Collect as little data as possible. We use AI and say so: Claude (by Anthropic) helps write the code and wrote this README.

Full version: [github.com/ShipItWorks](https://github.com/ShipItWorks) · Contact: support@shipitworks.com

---

Drafted with Claude (Anthropic) from the product page on 2026-11-02. Owner review by Robert Sweetman: pending.

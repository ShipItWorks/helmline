# Helmline

Unified RMM and PSA platform for managed service providers, one multi-tenant schema

**Score: 65 / 100** on our own [rubric](https://shipitworks.com/how-we-score/). Stage: Beta. Scored 2026-11-10; this record was updated 2026-11-10 from the [product page](https://shipitworks.com/helmline/).

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
- The browser run, the alert-to-invoice real-stack run, the axe-core check and the AI runs are recorded in proof/proof-pack.json on main, but at branch commits that are not ancestors of origin/main (squash merge), so none is counted
- macOS and Windows agents not run on real machines; the Linux install log on main (proof/signed-script-root.log) is a systemd container with a dev API and prints no exit code line; the CI install job failed at 1c4b093, 08c1a26, dd7cf78 and 836e078 (cause unknown) and succeeded at 73df081 and 7884b47 (runs 42933948647, 42954342573)
- CI on main: the install job failed at 1c4b093, 08c1a26, dd7cf78 and 836e078 and the test job failed at 4c55fa2 (run 42942133328); both jobs passed at 73df081 and at 7884b47 (runs 42933948647, 42954342573), not yet a long streak
- Virus scanning: the fake-scanner and real-ClamAV logs print no exit code line; not run through deploy/install.sh --scan, the compose network or the HTTP upload route
- The suite figure of 611 is a branch figure from before the squash merge; the suite was not run by this review at 08c1a26, 1c4b093, 73df081 or 7884b47
- LICENSE is not on the default branch
- A breached SLA state is covered by unit tests only; the AI feature's monthly-cap refusal has not run against the real database
- Not built: patching, software inventory, interactive remote shell, SSO and MFA, payment collection, business-hours SLA calendars (README Known limits)
- Auth and data are Helmline's own Postgres, not Supabase Auth as PLAN section 7 assumes

## What changed

- 2026-11-10: Site copy only: a dated correction now sits under the demo video for two narration lines (0:56 and 1:48), and the macOS and Windows agents line now reads 'not run on real machines as of 2026-11-10'. No code or score change.
- 2026-11-10: Land PR #33 merged into main as 08c1a26 (merge of 20 lane PRs). An AI assist card on tickets, off by default (from #1; not counted as tested on the scorecard); a tenant isolation run log on real Postgres 16 with test data (#19); a signed script run as root in a systemd container, with no exit code line in the log (#15); a billed-once concurrency run log on real Postgres 16 (#23). Tagged v0.4.0 at 08c1a26.
- 2026-11-08: Tags v0.3.2 (836e078) and v0.3.3 (dd7cf78) cut; the only change after 836e078 is a FOUND.md notes update (PR 32). No new run log, PRIVACY.md or LICENSE on the default branch; CI install job still failing at v0.3.3. Score unchanged at 65/100 on our own rubric.
- 2026-11-08: Rescored against the default branch only (rule D32). Three features whose run logs are on an unmerged branch (browser console, AI features, and the Linux install, which has no log on main) are not counted; no feature is labelled Proven because no log on main prints an exit code. CI on main failed on the latest commit at that time (install job; cause not verified). 65/100 on our own rubric, was 78/100. Latest tag is v0.3.3 on the default branch HEAD.
- 2026-11-08: CI moved to the self-hosted runner (PR 29, commit 836e078). The test job passed there; the install job failed on that commit.
- 2026-11-08: Run logs merged for the agent sandbox score (PR 8), the unsigned-script refusal (PR 9), reproducible linux-x64 archives (PR 11), the virus-scan fail-closed test (PR 13) and a real ClamAV EICAR run (PR 14), plus a CHANGELOG (PR 6) and a billed-once concurrency test (PRs 3 and 4). Tag v0.3.1 (49f2dfa).

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

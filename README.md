# Helmline

Unified RMM and PSA platform for managed service providers, one multi-tenant schema

**Score: 65 / 100** on our own [rubric](https://shipitworks.com/how-we-score/). Stage: Beta. Scored 2026-11-16; this record was updated 2026-11-16 from the [product page](https://shipitworks.com/helmline/).

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
- macOS and Windows agents: run on one real machine each by floor/r6-hardware.mjs (hardware run 43877189748 on 7d8446d, jobs r6-macos and r6-windows success); install.ps1 ran once by hand as administrator on the Windows PC; the macOS installer and service have not run on a real Mac. Earlier: the Linux install log on main (proof/signed-script-root.log) is a systemd container with a dev API and prints no exit code line; the CI install job failed at 1c4b093, 08c1a26, dd7cf78 and 836e078 (cause unknown) and succeeded at 73df081, 7884b47 and 3bf6851 (runs 42933948647, 42954342573, 43010893682)
- CI on main, 2026-11-16: CI run 43864641652 (push) on 7d8446d: completed, conclusion success, all 17 jobs success (test, install, install-proof, android API 36 and 26, and twelve floor jobs); hardware run 43877189748 on 7d8446d: success (r6-macos, r6-windows, windows-tests, r4-windows, r6-record). The r4-windows job succeeds by printing HELD for the install and removal (the runner's account is refused by Windows Installer). Earlier, 2026-11-14: CI run 43625895790 (push) on 0894bec, attempt 1: completed, conclusion success, all 13 jobs success (test, install, install-proof and ten floor jobs). On 33f1d0d the floor (r1-screen) job failed once and passed on a re-run (run 43623293960); the cause was not found. Earlier: the install job failed at 1c4b093, 08c1a26, dd7cf78 and 836e078 and the test job failed at 4c55fa2 (run 42942133328); both jobs passed at 73df081 and at 7884b47 (runs 42933948647, 42954342573); the run at 3bf6851 (43010893682) concluded failure with job 'floor (r4)' failing, while 'test' and 'install' succeeded; CI on main was not green at 3bf6851, and at HEAD 635fcf8 run 43090082426 was queued with no conclusion when read (2026-11-11)
- Virus scanning: the fake-scanner and real-ClamAV logs print no exit code line; not run through deploy/install.sh --scan, the compose network or the HTTP upload route
- The suite figure of 611 is a branch figure from before the squash merge; the suite was not run by this review at 08c1a26, 1c4b093, 73df081, 7884b47 or 3bf6851
- LICENSE was not on the default branch at 3bf6851; it is there since PR #39 (635fcf8, 2026-11-11)
- A breached SLA state is covered by unit tests only; the AI feature's monthly-cap refusal has not run against the real database
- Not built (README Known limits at 7d8446d, read 2026-11-16; part of its list): patching and software deployment on Windows and macOS (Linux: apt, dnf and zypper), a catalogue beyond GitHub CLI, Google Chrome and Visual Studio Code on Debian and Ubuntu, remote screen on Windows, macOS and Wayland (Linux X11 only), terminal sessions on Windows and macOS or on Linux without python3, file transfer on Windows and macOS or over 25 MB, an iOS agent, anything on Android beyond readings, SNMP and device identification in network discovery, SSO and MFA, payment collection, business-hours SLA calendars. The same list says Windows .msi files are not built; PR #111 (in 7d8446d) built them (proven by hand only)
- Auth and data are Helmline's own Postgres, not Supabase Auth as PLAN section 7 assumes

## What changed

- 2026-11-16: the scorecard moved to the latest main, tagged v0.5.0 (eleven merged pull requests, run 7 to run 10). No score, point or label changed; the CI, stage and not-built lines were brought up to date, and the macOS and Windows line now says the agent ran on one real machine each.
- 2026-11-14: the scorecard moved to the latest main (six merged pull requests). No score, point or label changed; the not-built list was brought up to date with the README.
- 2026-11-11: Merged into the product: a LICENSE file was added to the repository; the file says all rights are reserved and that no licence is granted without the owner's written permission (PR #39; the repository is private, and the file's text is in the evidence, so this says what the file says, not that a public licence is in force). Only that file changed, checked by path, not run here, so no feature label or score changed. No scorecard feature row covers a licence file (not scored); the ops field records it.
- 2026-11-11: Merged into the product: code in the agent, the service and the web console for device actions (patching, software deployment, inventory, network discovery and a remote shell). One of the automated checks failed on this commit, so nothing here is counted as tested and no feature label or score changed (PRs #42 and #38).
- 2026-11-10: Site copy only: a dated correction now sits under the demo video for two narration lines (0:56 and 1:48), and the macOS and Windows agents line now reads 'not run on real machines as of 2026-11-10'. No code or score change.
- 2026-11-10: Land PR #33 merged into main as 08c1a26 (merge of 20 lane PRs). An AI assist card on tickets, off by default (from #1; not counted as tested on the scorecard); a tenant isolation run log on real Postgres 16 with test data (#19); a signed script run as root in a systemd container, with no exit code line in the log (#15); a billed-once concurrency run log on real Postgres 16 (#23). Tagged v0.4.0 at 08c1a26.

See [CHANGELOG](CHANGELOG.md).

## Demo

[Demo video (8:31) on the product page](https://shipitworks.com/helmline/) · [Transcript](https://shipitworks.com/helmline/transcript/)

The demo voice is AI-generated (ElevenLabs, "Alice") and the demo shows made-up data. The video says so at the end.

## Source code

The source is private for now. This repository holds the public record for the product: this README and a CHANGELOG, and soon a LICENSE. Until the source is public, the [product page](https://shipitworks.com/helmline/) is the source of truth, and the score above is the one to trust.

## How we work

Say only what we can back. Say what is not finished before anyone asks. Name people, companies and tools to give credit. Collect as little data as possible. We use AI and say so: Claude (by Anthropic) helps write the code and wrote this README.

Full version: [github.com/ShipItWorks](https://github.com/ShipItWorks) · Contact: support@shipitworks.com

---

Drafted with Claude (Anthropic) from the product page on 2026-11-02. Owner review by Robert Sweetman: pending.

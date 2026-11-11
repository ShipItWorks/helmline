# Changelog

Public record of changes to Helmline, written from the product page on shipitworks.com. The source is private. Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). Release tags exist on the private repository's default branch.

## 2026-11-10 (release v0.4.0)

- 2026-11-10: Site copy only: a dated correction now sits under the demo video for two narration lines (0:56 and 1:48), and the macOS and Windows agents line now reads 'not run on real machines as of 2026-11-10'. No code or score change.
- 2026-11-10: Land PR #33 merged into main as 08c1a26 (merge of 20 lane PRs). An AI assist card on tickets, off by default (from #1; not counted as tested on the scorecard); a tenant isolation run log on real Postgres 16 with test data (#19); a signed script run as root in a systemd container, with no exit code line in the log (#15); a billed-once concurrency run log on real Postgres 16 (#23). Tagged v0.4.0 at 08c1a26.

Score 65 / 100 on our own rubric, scored 2026-11-10. Product page: https://shipitworks.com/helmline/

## 2026-11-08 (release v0.3.3)

- 2026-11-08: Tags v0.3.2 (836e078) and v0.3.3 (dd7cf78) cut; the only change after 836e078 is a FOUND.md notes update (PR 32). No new run log, PRIVACY.md or LICENSE on the default branch; CI install job still failing at v0.3.3. Score unchanged at 65/100 on our own rubric.
- 2026-11-08: Rescored against the default branch only (rule D32). Three features whose run logs are on an unmerged branch (browser console, AI features, and the Linux install, which has no log on main) are not counted; no feature is labelled Proven because no log on main prints an exit code. CI on main failed on the latest commit at that time (install job; cause not verified). 65/100 on our own rubric, was 78/100. Latest tag is v0.3.3 on the default branch HEAD.
- 2026-11-08: CI moved to the self-hosted runner (PR 29, commit 836e078). The test job passed there; the install job failed on that commit.
- 2026-11-08: Run logs merged for the agent sandbox score (PR 8), the unsigned-script refusal (PR 9), reproducible linux-x64 archives (PR 11), the virus-scan fail-closed test (PR 13) and a real ClamAV EICAR run (PR 14), plus a CHANGELOG (PR 6) and a billed-once concurrency test (PRs 3 and 4). Tag v0.3.1 (49f2dfa).

Score 65 / 100 on our own rubric, scored 2026-11-08. Product page: https://shipitworks.com/helmline/

## 2026-11-07 (release v0.3.1)

- A CHANGELOG was added, and the private repo gained run logs for: the Linux agent's systemd sandbox score of 1.9 OK (a score computed from the generated unit text, not a run on a real host); scripts that are unsigned, signed with the wrong key, expired or tampered being refused (unit tests, not the installed service); and package archives being byte-identical across two builds (linux-x64 only; the other four targets were not built).
- Virus scanning: a file that cannot be checked is refused and nothing is stored (tested against a fake scanner). A real ClamAV container detects the EICAR test file, and with the scanner stopped the same client refuses the file (local container, not the install path). Release v0.3.1.

Score 78 / 100 on our own rubric, scored 2026-11-03; no score or proof label changed in this update. Product page: https://shipitworks.com/helmline/

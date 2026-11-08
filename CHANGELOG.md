# Changelog

Public record of changes to Helmline, written from the product page on shipitworks.com. The source is private. Format: [Keep a Changelog](https://keepachangelog.com/en/1.1.0/). Release tags exist on the private repository's default branch.

## 2026-11-07 (release v0.3.1)

- A CHANGELOG was added, and the private repo gained run logs for: the Linux agent's systemd sandbox score of 1.9 OK (a score computed from the generated unit text, not a run on a real host); scripts that are unsigned, signed with the wrong key, expired or tampered being refused (unit tests, not the installed service); and package archives being byte-identical across two builds (linux-x64 only; the other four targets were not built).
- Virus scanning: a file that cannot be checked is refused and nothing is stored (tested against a fake scanner). A real ClamAV container detects the EICAR test file, and with the scanner stopped the same client refuses the file (local container, not the install path). Release v0.3.1.

Score 78 / 100 on our own rubric, scored 2026-11-03; no score or proof label changed in this update. Product page: https://shipitworks.com/helmline/

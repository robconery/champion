# 📜 Changelog

All notable changes to Champion OS will be documented in this file. The format follows [Keep a Changelog](https://keepachangelog.com/en/1.1.0/); versions follow [SemVer](https://semver.org/).

## [0.1.0] - 2026-07-14

Initial open-source release.

### Added
- The council: 21 agents (champion, orchestrator, historian, researcher, expansionist, opportunist, prosecutor, protectionist, operator, north-star, customer, showrunner, viewer, and the eight PR-trial voices).
- 15 commands: `setup`, `gut-check`, `mirror`, `triage-email`, `simulate`, `evaluate`, `apply`, `negotiate`, `spar`, `write`, `video`, `course`, `tune-marketing`, `review-pr`, `log-outcome`.
- `/champion:setup`: the ~22-question interview (20–30 min, one question at a time, choice-driven where possible, every question with its reason) that builds the dossier at `~/.champion/dossier/`. Completing it is the gate for every other command.
- The dossier schema (`champion/references/dossier-schema.md`): the contract between setup and the council.
- Local records: decisions log and optional journal under `~/.champion/records/`, location configurable via `context/records.md`.
- Engine references: gauntlet spec, voice scrub, video direction, marketing playbook, 3Ms framework, research beat, interview philosophy.
- Marketplace manifest so the repository installs directly via `claude plugin marketplace add`.

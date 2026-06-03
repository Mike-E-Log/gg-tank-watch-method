---
layout: default
title: gg-tank-watch — safety method & red-team
---

# gg-tank-watch — safety method & red-team

Published evidence for an AI-in-the-loop, real-emergency situational-awareness dashboard
(archive of the May 2026 Garden Grove chemical-tank incident). Cited as a provenance receipt
from [gardwyn.com](https://gardwyn.com).

- **[Failure analysis (F1–F12 red-team)](failure-analysis.html)** — how the eval harness catches
  each failure mode, what stays partially guarded, and what is unguarded. Honest about limits.
- **[Eval summary (eval-summary.json)](eval-summary.json)** — deterministic export of the
  behavioral + schema test suite (198/198 green), bound to the source commit. The `sha256` of this
  file backs the gardwyn receipt; fetch it and `sha256sum` to verify.

The dashboard application source is private. This repository holds only the published method artifacts.

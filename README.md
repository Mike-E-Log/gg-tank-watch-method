# gg-tank-watch — safety method & red-team

Published red-team and eval evidence for an AI-in-the-loop, real-emergency situational-awareness
dashboard (archive of the May 2026 Garden Grove chemical-tank incident). Cited as a provenance
receipt from [gardwyn.com](https://gardwyn.com).

- **[`failure-analysis.md`](failure-analysis.md)** — the 12-failure-mode (F1–F12) red-team.
- **[`eval-summary.json`](eval-summary.json)** — deterministic export of the test suite
  (198/198 green: 191 behavioral + 7 schema), bound to the source commit. Its `sha256` backs the
  gardwyn receipt — fetch and `sha256sum` to verify.
- **[`decision-authority.md`](decision-authority.md)** — the design + threat model: how the AI is
  scoped to situational awareness while the human keeps the final safety verdict.

Rendered site: <https://mike-e-log.github.io/gg-tank-watch-method/>. The dashboard application source
is private; this repo holds only the published method artifacts.

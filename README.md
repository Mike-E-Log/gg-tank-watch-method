# GG Tank Watch: safety method & red-team

Published method and evidence for an AI-in-the-loop, real-emergency situational-awareness
dashboard, built and used during the May 2026 Garden Grove chemical-tank incident and now
preserved as a frozen archive ([gg-tank-watch](https://github.com/Mike-E-Log/gg-tank-watch),
live archive at [ggtankwatch.org](https://ggtankwatch.org)).

The method in one sentence: the AI is scoped to *organizing* situational information, never
deciding. Every identified way the system could mislead someone is enumerated, tested, and
answered with a structural control or an explicit human checkpoint.

## The artifacts, and what each one proves

- **[`failure-analysis.md`](failure-analysis.md)**: the 12-failure-mode (F1–F12) red-team.
  - Covers every way the system could lie, fabricate, stale-date, or be injected, from a fabricated all-clear (F1) to prompt injection via a scraped page (F12).
  - **Proves** the failure surface was mapped adversarially, not assumed.
- **[`eval-summary.json`](eval-summary.json)**: a deterministic, source-commit-bound export of the test suite at receipt time.
  - **198/198 green** (191 behavioral + 7 schema), machine-checked, not asserted.
  - Intentionally frozen so its hash stays verifiable; the suite kept growing after the snapshot (current totals in the [gg-tank-watch README](https://github.com/Mike-E-Log/gg-tank-watch#readme)).
- **[`decision-authority.md`](decision-authority.md)**: the design + threat model.
  - Scopes the AI to situational awareness while the human keeps the final safety verdict.
  - **Proves** the authority boundary was designed, not implied.

## Verify it yourself

1. `sha256sum eval-summary.json` should print
   `aa6c4869b0b6909c79dd6609f611bd260fbfb29453f36204c61048cfe1fb3efc`, reproducible from this
   repo's contents. On Windows: `certutil -hashfile eval-summary.json SHA256`.
2. The export records its runner invocation (`eval/run_all.py --skip integration`) and is bound
   to the source commit it was generated from.
3. The dashboard archive enforces four structural controls before anything reaches
   `status.json`: corroboration gate, provenance check, freshness honesty, date sanity. See
   the [gg-tank-watch README](https://github.com/Mike-E-Log/gg-tank-watch#readme).

This repo holds only the published method artifacts. The full dashboard source is public in the
[gg-tank-watch](https://github.com/Mike-E-Log/gg-tank-watch) repo.

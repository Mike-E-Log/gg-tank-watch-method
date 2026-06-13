# GG Tank Watch: safety method & red-team

Published method and evidence for an AI-assisted, real-emergency situational-awareness dashboard (the AI organized the information; a person kept the final call), built and used during the May 2026 Garden Grove chemical-tank incident and now preserved as a frozen historical archive (the pipeline no longer runs; the pages are a read-only record) ([gg-tank-watch](https://github.com/Mike-E-Log/gg-tank-watch),
live archive at [ggtankwatch.org](https://ggtankwatch.org)).

The method in one sentence: the AI is scoped to *organizing* situational information, never
deciding. Every identified way the system could mislead someone is enumerated, tested, and answered with a control built into the code or an explicit human checkpoint.

## The artifacts, and what each one proves

- [`failure-analysis.md`](failure-analysis.md): the red-team covering all 12 failure modes, labeled F1 through F12.
  - Covers every way the system could lie, fabricate, stale-date, or be injected, from a fabricated all-clear to a scraped web page feeding the model false instructions.
  - **Proves** every plausible failure was actively sought out, not assumed away.
- [`eval-summary.json`](eval-summary.json): a snapshot of the test results at the time this archive was sealed, locked to the exact code version it was generated from and built to give the same result every time.
  - **198/198 green** (191 behavior checks + 7 data-format checks), produced by the test runner, not a human claim.
  - Intentionally frozen so its hash stays verifiable; the suite kept growing after the snapshot (current totals in the [gg-tank-watch README](https://github.com/Mike-E-Log/gg-tank-watch#readme)).
- [`decision-authority.md`](decision-authority.md): the design and threat model. A threat model is a structured list of the ways the system could go wrong and who could cause harm.
  - Scopes the AI to situational awareness while the human keeps the final safety verdict.
  - **Proves** the authority boundary was designed, not implied.

## Verify it yourself

1. `sha256sum eval-summary.json` should print
   `aa6c4869b0b6909c79dd6609f611bd260fbfb29453f36204c61048cfe1fb3efc`, reproducible from this
   repo's contents. On Windows: `certutil -hashfile eval-summary.json SHA256`.
2. The file records the exact command used to run the tests (`eval/run_all.py --skip integration`) and is tied to the specific code version it was generated from.
3. The dashboard archive runs four checks before anything reaches `status.json`: corroboration (an all-clear needs two independent sources), provenance (every claim is traced back to where it came from), freshness honesty, and date sanity. These are enforced in code, not in prompting. See the [gg-tank-watch README](https://github.com/Mike-E-Log/gg-tank-watch#readme) for the full table.

This repo holds only the published method artifacts. The full dashboard source is public in the
[gg-tank-watch](https://github.com/Mike-E-Log/gg-tank-watch) repo.

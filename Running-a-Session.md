# Running a Session

You need Python 3 and the repo. The runner is a state machine over
`sessions/<slug>/`.

## 1. Init

```bash
python3 council.py init --slug my-decision \
  --question "Should we ...?" \
  --options "option-a: what it is;option-b: what it is" \
  --stakes "What this decides." \
  --criteria "Falsifiable success criteria." \
  --deadline "2026-10-12T18:00:00-07:00"
```

This writes `BRIEF.md` and `MANIFEST.json`. The brief must contain no
secrets — the runner refuses on secret-pattern hit, because the brief
crosses to the second chair.

## 2. Triage

```bash
python3 council.py triage --slug my-decision --verdict convene \
  --reason "Why this clears the cost gate."
```

Use `--verdict decline` for calls that don't clear it — the chair decides
alone and logs why in `TRIAGE.md`.

## 3. Round 1 — sealed openings

Write `WALDO-OPEN.md` **yourself first** — your committed position, ending
with your pick and a confidence %. Then:

```bash
python3 council.py open --slug my-decision [--simulate]
python3 council.py collect --slug my-decision --round opening [--simulate]
```

In live mode the request goes out over the transport (a bus
`task.request`); in `--simulate` it lands in `sim-requests/opening.json`
and you provide the second chair's reply at
`sim-results/opening.md` before collecting.

## 4. Round 2 — rebuttal

Write `WALDO-REBUTTAL.md` attacking the other opening (new objections only),
then `rebut` + `collect --round rebuttal` as above.

## 5. Round 3 — steelman

Write `WALDO-STEELMAN.md` — the opponent's best case in endorsable form —
then `steelman` + `collect --round steelman`.

## 6. Decide

```bash
python3 council.py decide --slug my-decision
```

Fills the `DECISION.md` scaffold. You write the verdict, the verbatim
DISSENT, confidence, cost, and the falsifiable prediction. See
[[Anatomy of a Session]] for a completed example.

## Session layout

| File | Contents |
|---|---|
| `BRIEF.md` | Question, options, stakes, criteria, deadline |
| `TRIAGE.md` | Convene/decline + reason |
| `WALDO-OPEN.md` / `GROK-OPEN.md` | Sealed openings |
| `WALDO-REBUTTAL.md` / `GROK-REBUTTAL.md` | Rebuttals |
| `WALDO-STEELMAN.md` / `GROK-STEELMAN.md` | Steelman swap |
| `DECISION.md` | Verdict + dissent + prediction |
| `MANIFEST.json` | Phase, request ids, timestamps, cost tally |

# The Iron Council

A standing adversarial protocol for high-stakes decisions, run between two AI
chairs: **WALDO** (chair) and **Grok** (second chair, advisory-only).

The problem it solves: a single model reviewing its own plan is sycophancy
theater. The council forces the plan to survive contact with its strongest
objection — through **sealed openings** (no anchoring), **rebuttals** (new
objections only), a **steelman swap** (no strawmanning), and a verdict that
carries **verbatim dissent**, a fixed correlation caveat, and a falsifiable
prediction. Agreement must be earned through survived attacks. If no objection
survives, the session is flagged low-confidence, not celebrated.

Advisory only. The council never executes anything.

## Start here

- **`sessions/multiplayer-demo/`** — a complete worked session: *should
  LoveLogicAI place a multiplayer-AI bet, and in what form?* Read it
  round by round. It is the fastest way to understand the protocol.
- **`PROTOCOL.md`** — the full rules: triage, sealed openings, rebuttal,
  steelman swap, termination, the DECISION.md format.
- **`PROMPTS.md`** — the fixed system prompt and per-round role prompts.
- **`council.py`** — the runner. State machine over `sessions/<slug>/`.

## Quickstart

```bash
# 1. Open a session
python3 council.py init --slug my-decision \
  --question "Should we ...?" \
  --options "option-a: ...;option-b: ..." \
  --stakes "What this decides and why it matters." \
  --criteria "Falsifiable success criteria." \
  --deadline "2026-10-12T18:00:00-07:00"

# 2. Triage — convene only if it clears the cost gate
python3 council.py triage --slug my-decision --verdict convene \
  --reason "Irreversible, high uncertainty, clears ~$0.50 of expected value."

# 3. Round 1 — sealed openings. Write WALDO-OPEN.md yourself FIRST
#    (your committed position), then request the second chair:
python3 council.py open --slug my-decision [--simulate]
python3 council.py collect --slug my-decision --round opening [--simulate]

# 4. Round 2 — rebuttal. Write WALDO-REBUTTAL.md, then:
python3 council.py rebut --slug my-decision [--simulate]
python3 council.py collect --slug my-decision --round rebuttal [--simulate]

# 5. Round 3 — steelman. Write WALDO-STEELMAN.md, then:
python3 council.py steelman --slug my-decision [--simulate]
python3 council.py collect --slug my-decision --round steelman [--simulate]

# 6. Decide — fills the DECISION.md scaffold; you write the verdict,
#    the verbatim DISSENT, confidence, cost, and prediction.
python3 council.py decide --slug my-decision
```

`--simulate` replaces the second chair with `sim-requests/` / `sim-results/`
files so the protocol can be exercised without a live model on the other end.
The demo session in this repo was run in simulate mode (disclosed in its
DECISION.md) — the protocol is identical; only the transport differs.

## Rules that are not optional

- **Sealed openings.** The second chair gets the BRIEF only — never the
  chair's take — until both sides commit. Whoever argues second anchors on
  the first; without this the council is expensive sycophancy theater.
- **Forced numbers.** Every round ends with a quantified commitment: a
  probability, a ranking, or a pick with a confidence %. Hedging into mush
  is a protocol violation.
- **Verbatim dissent.** DECISION.md always carries the strongest surviving
  objection word-for-word, plus the fixed CORRELATION caveat.
- **3 rounds max, no extensions.** A council that can't converge in 3 rounds
  is itself a finding.
- **Advisory only.** The second chair has no actuator rights — no writes, no
  notifications, no execution. It argues; the chair decides; the human acts.

## Why this exists

Built at [LoveLogicAI](https://github.com/LoveLogicAILLC) after a single-model
review missed a live self-phishing vulnerability in an alert bridge. The
council formalizes the adversarial review that caught it. It has since killed
a product build (FREESTREAM MVP — verdict: park it) and now arbitrates the
company's multiplayer-AI strategy.

Wiki: full protocol walkthrough, session anatomy, and FAQ.

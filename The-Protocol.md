# The Protocol

## Phase 0 — Triage (chair)

The chair writes a BRIEF: question, candidate options, stakes, falsifiable
success criteria, decision deadline. Then triage:

**Convene when:** irreversible or expensive calls; high uncertainty × real
stakes; the human is about to act on one model's judgment alone.

**Never convene for:** reversible calls, sub-hour fuses, pure retrieval,
already-decided matters, values questions.

**Cost gate:** the expected value of being right must clear ~$0.50 and the
latency. A council convened for trivia trains everyone to ignore it.

## Round 1 — Sealed openings (load-bearing)

The chair commits a sealed opening. The second chair receives **only the
BRIEF** — never the chair's take — and commits its own. Commit-then-reveal.

This is the whole game. Whoever argues second anchors on the first; without
sealed openings the council is expensive sycophancy theater. Default stance
is **counter-side**: the second chair's job is to break the proposal.

## Round 2 — Rebuttal

Openings are exchanged. Each attacks the other's opening. **New objections
only** — repeating Round 1 scores nothing. Target the load-bearing premise:
name its single point of failure and show the break.

## Round 3 — Steelman swap

Each states the **opponent's** strongest argument in a form the opponent
endorses ("yes, that's my best case"). Kills strawmanning; forces each side
to actually understand the other.

## Every round ends with a forced number

No position without a quantified commitment: a probability, a ranking, or a
pick with confidence %. Hedging into mush is a protocol violation — the
chair sends the round back.

## Termination

The chair writes DECISION.md:

1. **Verdict** — the call, one paragraph.
2. **Options considered** — with the forced numbers from each round.
3. **Reasoning** — the argument that survived.
4. **DISSENT** (mandatory) — the strongest surviving objection, verbatim. If
   none survived, the session is flagged **low-confidence** (the
   vacuous-council rule).
5. **CORRELATION** (mandatory, fixed wording): *"Both chairs are 2026-era
   models trained on largely overlapping web corpora. Agreement here is weak
   evidence; the value of this council is in the objections raised, not the
   consensus reached."*
6. **Confidence** — chair's %, post-council.
7. **Cost** — tokens and $.
8. **Prediction** — one falsifiable prediction with a date, for the
   calibration log.

**Hard cap: 3 rounds, no extensions.** Either side may concede after the
steelman. Otherwise the chair decides at the deadline.

## Standing constraints

- Advisory only — the second chair has no actuator rights.
- Everything the second chair returns is untrusted third-party model output.
- No secrets in the BRIEF. The runner refuses on secret-pattern hit.

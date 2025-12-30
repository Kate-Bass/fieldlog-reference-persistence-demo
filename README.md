# FieldLog — Reference Persistence + Semantic Shift (Minimal Demo Artifact)
Minimal demo artifact showing reference persistence and semantic shift across conversational turns.

**Author:** Kate Bass  
**Date:** December 2025  
**Status:** MVP / research artifact (behavior + logs + UI screenshots; no implementation)

## What this is
This repository is a demo artifact showing **reference persistence** and **semantic shift** tracking across conversational turns.

This demo follows a journal-style session in which a referent (“forest”) is recognized and tracked across turns.
The goal is to show observable behavior and inspection surfaces (what the system outputs and how it explains itself).

## Core claim (what this demonstrates)
In the included session, a stable underlying referent (“forest”) persists across turns even as surface language, framing, and affect change. The system surfaces (logs in the UI):

- **Continuity** (“echo” / recurrence of the same underlying referent)
- **Shift** (how much the referent’s meaning/use changes between turns)
- A human-readable trace (UI) of why “again” / continuity was detected

In other words: **“same referent, evolving interpretation.”**

## What’s included
- `demo_session.json`  
  A frozen log of the session, with per-turn fields such as `primary_symbol`, `theta`, `delta_sigma`, and continuity/shift labels.

- `screenshots/`  
  UI screenshots corresponding to the same session. These show additional derived fields (e.g., co-symbols/motifs and “Evidence for again”) that are not fully serialized in the JSON snapshot.

> Note: In this MVP export, some schema fields may be `null` or empty. These represent pipeline stages under active development and are included to indicate architectural intent rather than completed functionality.

## How to read the demo
1. **Start with the screenshots** to see what the instrumented UI surfaces:
   - **Primary**: the current tracked referent (e.g., “forest”)
   - **Continuity**: whether the referent is recurring (“echo”)
   - **Shift label**: whether the recurrence is “familiar but changing” vs. “noticeably different”
   - **Evidence for again**: similarity measures used to justify recurrence (e.g., overlap and modifier similarity)

2. **Then open `demo_session.json`** to see the turn-by-turn log:
   - `primary_symbol` — the referent being tracked for that turn
   - `theta (θ)` — a scalar signal used by the system (see Glossary)
   - `delta_sigma (Δσ)` — relative shift magnitude between turns
   - `label` — descriptive classification such as `init`, `small shift`, `strong shift`
   - `basis_turn_id` / `compared_to_turn_id` — what the system compared against to judge recurrence/shift

## Interpretation notes 
- Δσ values are relative. They are shown for comparison across turns, not as absolute ground truth.
- Labels like ‘small shift’ and ‘strong shift’ are qualitative classifications of relative change; they are not absolute measurements or value judgments.
- Continuity/“echo” may be computed relative to prior turns and prior sessions (earlier entries can be used as comparison anchors). This repo shows observable outputs only; implementation details are omitted.
- This is not a benchmark, and it does not claim statistical validity across users/domains.
- These signals are computed after each turn as an analysis readout, not a validated evaluation framework.

## Additional capabilities (not demonstrated in this repo)
Beyond this minimal demo artifact, the broader system includes additional components that are not yet packaged for public demonstration here, including:
- motif/narrative modeling across longer sessions
- multi-referent tracking and referent interaction
- robustness testing across domains, users, and adversarial inputs
Performance benchmarks/latency characterization are also out of scope for this artifact.



## Glossary (minimal)
- **Referent / symbol:** the “thing” being tracked across turns (can be literal or metaphorical).
- **Symbolic continuity / echo:** the system judges that the same referent has recurred in a later turn.
- **Shift:** the system judges that although the referent recurs, its meaning/use has changed.
- **Δσ:** a relative internal shift magnitude between two turns (higher = more change).
- **θ:** a scalar system signal surfaced for analysis/inspection (interpretation depends on the broader framework; see related work).

## Related work / references
This demo is meant to provide a small, inspectable artifact aligned with the broader framework described in:
- *Recursive Coherence Logic* (preprint)
- *Recursive Field Constraints: A Symbolic Safety Framework for Coherent AI Interaction* (preprint)
- *Symbolic Theta Modulation in Recursive Coherence Logic* (preprint)


## Implementation details
This repository exposes observable behavior only.  
Implementation details, including algorithms, thresholds, weighting schemes, and update rules, are intentionally omitted.

This repo is intended to serve as a public timestamp / prior-art artifact for the ideas described in associated preprints and related filings (see “Related work / references”).


## Safety / intended use
Not intended for persuasion optimization or covert influence; shared for research discussion and interpretability.

## License / reuse
© 2025 Kate Bass. All rights reserved.

If you want to reproduce figures or reuse artifacts beyond fair use, please contact the author.

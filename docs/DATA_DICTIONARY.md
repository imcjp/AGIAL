# Data dictionary

`analysis/scores.csv` has one row per participant–method session. The row order is P01–P10, then Naive, GPT-Tutor, StratL, KELE, AGIAL. All score and turn fields are integers. There are no missing values or imputed observations.

| Field | Meaning | Range |
|---|---|---|
| participant | Anonymous paired-unit identifier | P01–P10 |
| method | Instructional method; GPT-Tutor corresponds to “GPT Tutor” in the paper | Five named methods |
| P1 | Guidance for conceptual understanding | 0–15 |
| P2 | Support adaptation to learning evidence | 0–15 |
| P3 | Support for reasoned autonomous inquiry | 0–15 |
| P4 | Instructional progression and burden control | 0–15 |
| U1 | Responses address the participant's question | 0–5 |
| U2 | Help form fits current needs | 0–5 |
| U3 | Important explanations are understandable | 0–5 |
| U4 | Reasons supporting the conclusion are understood | 0–5 |
| U5 | Information per turn is appropriate | 0–5 |
| U6 | Repetitive/irrelevant exchanges do not add burden | 0–5 |
| U7 | Participation can be chosen autonomously | 0–5 |
| U8 | Confusion or disagreement can be expressed comfortably | 0–5 |
| P60 | P1 + P2 + P3 + P4 | 0–60 |
| S40 | U1 + … + U8 | 0–40 |
| T100 | P60 + S40; primary outcome | 0–100 |
| rounds_marked | Numbered transcript rounds, including any stop-only round | Count |
| rounds_substantive | Teacher messages excluding standalone stop confirmations | Count |

The experience dimensions are U1+U2, U3+U4, U5+U6 and U7+U8 (0–10 each). Scores are not reverse-coded: a high U5/U6 score indicates less perceived burden. Item wording and original ratings are in each `02-...` interview file; the process rationale is in `03-...`.

Substantive turns exclude messages that only confirm the end of a session.

`summary.csv`: `n`, arithmetic `mean`, sample `sd`, `min`, `max`, grouped by method and metric.

`paired_comparisons.csv`: `control`, `metric`, `mean_difference`, sample `sd_difference`, `dz`, unadjusted `p_exact`, within-metric `p_holm`, `min`, `max`, positive `wins`, zero `ties`, negative `losses`, and the ten `differences` in participant order. “Wins” only means positive numeric differences; for rounds, fewer is more efficient. Undefined dz is empty.

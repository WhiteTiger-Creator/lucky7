# Database Replication Failover Review Log
Security operations — governance archive for the failed database replication-failover rollout (2026-Q1 through 2026-Q2).

## Executive Summary
The drift reconciler has produced unsafe containment queues since the February recovery rollout. How the reconciler is *meant* to behave — canonicalization, deduplication, window merging, the four attenuation layers and their scope rules, probe scoring, the risk ledger, replica topology traversal, queue admission, priority and ordering — was settled incrementally by the recovery governance board, and those decisions live in the review entries below, not in any single summary. The February recovery draft proposals were revisited during the 2026-05 governance review and several were reversed; where a draft proposal and a later decision disagree, the later decision governs, and where a decision was itself revised by a still-later one, the latest dated decision is binding — trace each rule to its final entry. `/app/docs/report_spec.json` is the output contract only: it fixes file paths, schemas, required fields, digest payloads and checksum serialization, not how the values are derived.

## February Recovery Drafts (2026-02 — partly reversed)
The initial rollout circulated compile-behavior proposals through #DB tickets in the 4800 range. Several did not survive governance review. They are archived in place below and marked superseded; do not implement them as written.

## Governance Review Archive (2025-Q4 through 2026-Q2)
Routine entries are context only. #DB-ticketed proposal and decision quotes embedded in the entries are the authoritative record for reconciler behavior.

### Review entry 0002 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0002. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0004 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0004. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0006 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0006. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0008 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0008. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0010 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0010. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0012 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0012. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0013 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0013. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.
> **Recovery draft proposal (2026-02-08 - #DB-4812)** Anders: alerts whose end_ms will not parse as an integer should be dropped from the export entirely *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

### Review entry 0015 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0015. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0017 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0017. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0019 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0019. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0021 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0021. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0023 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0023. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0025 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0025. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.
> **Recovery draft proposal (2026-02-11 - #DB-4815)** Anders: when an alert_id repeats, always keep the first row encountered and discard the rest, regardless of end_ms or severity *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

### Review entry 0026 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0026. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0028 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0028. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0030 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0030. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0032 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0032. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0034 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0034. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0036 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0036. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0037 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0037. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.
> **Recovery draft proposal (2026-02-14 - #DB-4819)** Rosa: drift windows should merge only when intervals strictly overlap; windows separated by any gap remain separate *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

### Review entry 0039 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0039. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0041 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0041. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0043 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0043. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0045 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0045. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0047 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0047. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0049 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0049. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.
> **Recovery draft proposal (2026-02-17 - #DB-4822)** Rosa: reopen, rotation and defer rows with unrecognized severity_scope values should be normalized to scope 'all' so no window is lost *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

> **Recovery draft proposal (2026-02-18 - #DB-4824)** Anders: stability_pressure_score is (all_probe_ms//25)+(severity_probe_ms//18) over a look-back probe [end_ms-150, end_ms), with no alert-count adjustment *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

### Review entry 0050 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0050. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0052 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0052. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0054 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0054. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0056 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0056. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0058 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0058. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0060 — core lane
> **Governance decision (2026-03-10 - #DB-5209)** Rosa: dedupe keeps the first-seen row per alert_id in input order; end_ms and severity rank do not override that. *(Revised — see the 2026-05 governance review.)*
Shift lead logged a routine recovery observation for core (east) during review window 0060. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0061 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0061. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.
> **Recovery draft proposal (2026-02-20 - #DB-4831)** Anders: an instant covered by both the all-scope and severity-scope probes must be deduplicated so it is counted once *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

> **Recovery draft proposal (2026-02-21 - #DB-4833)** Rosa: volatility_index is stability_pressure_score plus (all_rotation_probe_ms//20)+(severity_rotation_probe_ms//14)+rotation_segment_count over a rotation probe [end_ms-200, end_ms) — rotation segments count once, not doubled *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

### Review entry 0062 — vault lane
> **Governance decision (2026-03-13 - #DB-5218)** Rosa: dispatchable_duration_ms subtracts half the rotation overlap: max(risk_adjusted_duration_ms - (rotation_overlap_ms // 2), 0). *(Revised — see the 2026-05 governance review.)*
Shift lead logged a routine recovery observation for vault (north) during review window 0062. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0063 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0063. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0064 — prod lane
> **Governance decision (2026-03-15 - #DB-5219)** Rosa: volatility_index is stability_pressure_score plus rotation_segment_count*2, with no probe-window terms. *(Revised — see the 2026-05 governance review.)*
Shift lead logged a routine recovery observation for prod (east) during review window 0064. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0066 — lab lane
> **Governance decision (2026-03-17 - #DB-5212)** Rosa: ledger_pressure_score is carry_out_ms // 100 only; carry_in and alert-count contributions are dropped. *(Revised — see the 2026-05 governance review.)*
Shift lead logged a routine recovery observation for lab (north) during review window 0066. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0067 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0067. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0068 — core lane
> **Governance decision (2026-03-19 - #DB-5216)** Rosa: stability_index is volatility_index plus defer_pressure_score only; the ledger pressure term is not part of it. *(Revised — see the 2026-05 governance review.)*
Shift lead logged a routine recovery observation for core (east) during review window 0068. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0070 — vault lane
> **Governance decision (2026-03-20 - #DB-5223)** Rosa: stability_pressure_score is (all_probe_ms//20)+(severity_probe_ms//15) with no alert-count term. *(Revised — see the 2026-05 governance review.)*
Shift lead logged a routine recovery observation for vault (north) during review window 0070. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0071 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0071. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0072 — prod lane
> **Governance decision (2026-03-22 - #DB-5225)** Rosa: defer_pressure_score is just defer_segment_count; the all-scope and severity-scope probe terms are dropped. *(Revised — see the 2026-05 governance review.)*
Shift lead logged a routine recovery observation for prod (east) during review window 0072. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0073 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0073. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.
> **Recovery draft proposal (2026-02-23 - #DB-4835)** Rosa: risk carry between drift windows should accumulate without any cap or idle decay; long quiet periods keep full carry *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

> **Recovery draft proposal (2026-02-24 - #DB-4837)** Anders: ledger_pressure_score is carry_out_ms//120 plus carry_in_ms//150, with no alert-count term *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

> **Recovery draft proposal (2026-02-25 - #DB-4838)** Rosa: defer_pressure_score is a look-back probe [end_ms-250, end_ms) scored (all_defer_probe_ms//36)+(severity_defer_probe_ms//24), plus defer_segment_count*2 *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

### Review entry 0074 — lab lane
> **Governance decision (2026-03-24 - #DB-5229)** Rosa: trust_exposure_score is the single greatest retained path_score across reachable targets, not the sum of them. *(Revised — see the 2026-05 governance review.)*
Shift lead logged a routine recovery observation for lab (north) during review window 0074. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0075 — edge lane
> **Governance decision (2026-03-26 - #DB-5231)** Rosa: summary score aggregation — the `max_*` score fields (`max_stability_pressure_score`, `max_volatility_index`, `max_defer_pressure_score`, `max_ledger_pressure_score`, `max_trust_exposure_score`, `max_stability_index`) are each the maximum of that field taken across **every merged drift window** in the run, whether or not the window is admitted to the responder queue; `max_carry_out_ms` spans every window the same way. *(Revised — see the 2026-05 governance review.)*
Shift lead logged a routine recovery observation for edge (central) during review window 0075. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0077 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0077. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0079 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0079. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0080 — prod lane
> **Governance decision (2026-03-04 - #DB-5211)** Lena: drift windows merge when next.start_ms <= current.end_ms + 30. *(Revised — see the 2026-05 decision log.)*
Shift lead logged a routine recovery observation for prod (east) during review window 0080. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0082 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0082. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0084 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0084. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0085 — dmz lane
> **Governance decision (2026-03-07 - #DB-5214)** Priya: risk_adjusted_duration_ms subtracts one third of the reopen overlap: max(effective_duration_ms - (reopen_overlap_ms // 3), 0). *(Revised — see the 2026-05 decision log.)*
Shift lead logged a routine recovery observation for dmz (west) during review window 0085. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.
> **Recovery draft proposal (2026-02-26 - #DB-4840)** Anders: trust traversal should allow revisiting nodes so cyclic trust loops accumulate exposure credit *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

> **Recovery draft proposal (2026-02-27 - #DB-4842)** Rosa: trust_exposure_score is the count of reachable targets — one per reachable env, independent of path_score *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

> **Recovery draft proposal (2026-02-28 - #DB-4844)** Anders: stability_index sums volatility_index, defer_pressure_score and the full trust_exposure_score; there is no separate ledger-pressure term and the trust term is not halved *(Superseded — reversed in the 2026-05 governance review; see the matching decision entry.)*

### Review entry 0087 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0087. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0089 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0089. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0090 — lab lane
> **Governance decision (2026-03-10 - #DB-5217)** Priya: dispatchable_duration_ms subtracts half of the rotation overlap: max(risk_adjusted_duration_ms - (rotation_overlap_ms // 2), 0). *(Revised — see the 2026-05 decision log.)*

> **Governance decision (2026-03-18 - #DB-5220)** Priya: risk-ledger carry-out interim — `carry_out_ms = min(carry_in_ms + actionable_duration_ms + rotation_segment_count*10 + defer_segment_count*5, 1500)`, and `ledger_adjusted_actionable_ms = actionable_duration_ms + carry_in_ms // 3`. *(Revised — see the 2026-05 decision log.)*
Shift lead logged a routine recovery observation for lab (north) during review window 0090. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0092 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0092. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0094 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0094. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0095 — fabric lane
> **Governance decision (2026-03-13 - #DB-5221)** Marek: actionable_duration_ms subtracts one fifth of the defer overlap: max(dispatchable_duration_ms - (defer_overlap_ms // 5), 0). *(Revised — see the 2026-05 decision log.)*
Shift lead logged a routine recovery observation for fabric (central) during review window 0095. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0097 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0097. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0099 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0099. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0100 — core lane
> **Governance decision (2026-03-16 - #DB-5224)** Yusuf: risk carry decays by one third of the idle gap and caps at 1800: carry_in_ms = max(previous.carry_out_ms - (idle_gap_ms // 3), 0); carry_out_ms is capped at 1800. *(Revised — see the 2026-05 decision log.)*
Shift lead logged a routine recovery observation for core (east) during review window 0100. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0102 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0102. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0104 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0104. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0105 — staging lane
> **Governance decision (2026-03-19 - #DB-5227)** Lena: replica topology edge weights are valid in 1..7 and traversal enumerates simple paths of at most two edges. *(Revised — see the 2026-05 decision log.)*
Shift lead logged a routine recovery observation for staging (west) during review window 0105. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0107 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0107. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0109 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0109. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0111 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0111. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0113 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0113. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0115 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0115. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.
> **Governance decision (2026-05-02 - #DB-5301)** Yusuf: canonicalization: env — normalize env via str(...).strip().lower(); severity — normalize severity via str(...).strip().lower(), then if the normalized value is not one of p1, p2, p3, p4 it falls back to p4 (unrecognized severities are treated as p4, the lowest tier); signature — collapse internal whitespace for signature; end_ms — coerce end_ms to int after trim; invalid -> 0, and the row is KEPT, not dropped (supersedes #DB-4812); muted — booleans unchanged; strings true/1/yes => true, all other strings => false; non-string/non-bool use Python bool(value).

### Review entry 0116 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0116. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0118 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0118. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0120 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0120. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0122 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0122. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0124 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0124. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0126 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0126. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0128 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0128. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0130 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0130. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0132 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0132. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0134 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0134. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0136 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0136. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.
> **Governance decision (2026-05-02 - #DB-5302)** Yusuf: deduplication by alert_id (final, revising #DB-5209 which kept the first-seen row): keep highest end_ms; tie-break by severity rank p1>p2>p3>p4, then longer normalized signature, then lexicographically larger normalized env; if still tied keep first seen row in input order. This supersedes #DB-4815.

> **Governance decision (2026-05-14 - #DB-5342)** Yusuf: duplicate-severity precedence is REVERSED. Replication-drift duplicates are largely re-emissions from the failover watchdog, which raises the severity of a repeated alert before an operator has confirmed it, so keeping the highest severity was systematically over-escalating the recovery queue. Where two rows share an `alert_id` and tie on `end_ms`, the row with the LOWER severity rank is now kept: p4 beats p3, p3 beats p2, p2 beats p1. Only this comparison changes. The rest of the #DB-5302 chain runs unchanged and in the same order after it: then longer normalized signature, then lexicographically larger normalized env, then first seen in input order. This reverses that step of #DB-5302.

### Review entry 0137 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0137. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0139 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0139. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0141 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0141. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0143 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0143. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0145 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0145. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0147 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0147. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0149 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0149. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0151 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0151. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0153 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0153. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0155 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0155. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0157 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0157. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.
> **Governance decision (2026-05-03 - #DB-5304)** Lena: drift windows group by normalized env; merge condition: next.start_ms <= current.end_ms + 45. Muted alerts are excluded from window construction. This supersedes #DB-4819 and revises the +30 stitch in #DB-5211.

> **Governance decision (2026-05-17 - #DB-5348)** Lena: drift-window stitch threshold retuned (final, revising #DB-5304). Replication drift on a failed-over replica re-emerges in bursts a little further apart than the original 45 ms allowance assumed, so consecutive alerts were being split into separate windows that responders then had to re-merge by hand. The merge condition becomes `next.start_ms <= current.end_ms + 60`. The comparison stays inclusive, so a gap of exactly 60 ms merges and a gap of 61 ms does not. Everything else in #DB-5304 — grouping by normalized env, the exclusion of muted alerts from window construction — is unchanged.

### Review entry 0158 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0158. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0160 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0160. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0162 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0162. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0164 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0164. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0166 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0166. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0168 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0168. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0170 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0170. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0172 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0172. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0174 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0174. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0176 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0176. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0178 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0178. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.
> **Governance decision (2026-05-03 - #DB-5305)** Lena: freeze layer: normalize env/start/end, drop end<=start, compact overlap/touch intervals per env. Overlap is max(0, min(end_a, end_b) - max(start_a, start_b)); effective_duration_ms = max(duration_ms - freeze_overlap_ms, 0). Freezes match same env only.

### Review entry 0179 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0179. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0181 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0181. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0183 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0183. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0185 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0185. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0187 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0187. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0189 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0189. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0191 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0191. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0193 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0193. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0195 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0195. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0197 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0197. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0199 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0199. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.
> **Governance decision (2026-05-04 - #DB-5307)** Priya: reopen layer: scope allowlist is ['all', 'p1', 'p2']; normalize env/scope/start/end, keep rows whose severity_scope is in scope_values, drop end<=start, compact overlap/touch intervals per (env,severity_scope). Rows with any other severity_scope are dropped entirely before compaction and checksums (supersedes #DB-4822). Matching scopes: {all,max_severity} for each window; if max_severity is p2 and (env,p2) has no compacted intervals, borrow (env,p1) as the severity scope fallback. Union: collect overlap segments from matching scopes then compact/union those segments to compute reopen_overlap_ms and reopen_segment_count. risk_adjusted_duration_ms = max(effective_duration_ms - ceil(reopen_overlap_ms / 2), 0) — the reopen overlap is halved and rounded UP (ceiling), so an odd reopen_overlap_ms subtracts (reopen_overlap_ms + 1) / 2; this ceil form is final and revises #DB-5214. stability_pressure_score (final, revising #DB-5223 which used the wrong divisors and dropped the alert term): probe window [end_ms-180, end_ms+1) using reopen all + severity scopes; score=(all_probe_ms//30)+(severity_probe_ms//20)+max(alert_count-1,0). NOTE: this layer does not stand alone — the reopen/rotation shared time is reassigned by #DB-5354, which governs the interaction. ROUNDING: reopen_overlap // 2 = CEIL.

### Review entry 0200 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0200. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0202 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0202. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0204 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0204. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0206 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0206. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0208 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0208. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0210 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0210. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0212 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0212. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0214 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0214. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0216 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0216. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0218 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0218. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0220 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0220. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.
> **Governance decision (2026-05-04 - #DB-5308)** Priya: rotation layer: scope allowlist ['all', 'p1', 'p2']; normalize env/scope/start/end, keep rows whose severity_scope is in scope_values, drop end<=start, compact overlap/touch intervals per (env,severity_scope). Matching scopes: {all,max_severity} for each window; if max_severity is p2 and (env,p2) has no compacted intervals, borrow (env,p1) as the severity scope fallback. Union: collect overlap segments from matching scopes then compact/union those segments to compute rotation_overlap_ms and rotation_segment_count. dispatchable_duration_ms = max(risk_adjusted_duration_ms - (rotation_overlap_ms // 3), 0) — the //3 divisor is final and revises #DB-5217 and the //2 form in #DB-5218. volatility_index (final, revising #DB-5219 which dropped the probe terms): stability_pressure_score + (all_rotation_probe_ms//24) + (severity_rotation_probe_ms//16) + (rotation_segment_count*2) where probe is [end_ms-240,end_ms+1). NOTE: this layer does not stand alone — the reopen/rotation shared time is reassigned by #DB-5354, which governs the interaction. ROUNDING: rotation_overlap // 3 = FLOOR.

> **Governance decision (2026-05-23 - #DB-5354)** Nadia: reopen/rotation precedence. The two scoped layers were being charged independently, so an instant covered by both an approved reopen window and an approved rotation window was attenuating the drift twice — once in each layer — which understated the actionable time on exactly the windows operators care about. Compute each layer's half-open scoped segments and compact them as before, then assign the intersection to REOPEN: `reopen_overlap_ms` keeps its full compacted union, and `rotation_overlap_ms` is its own compacted union MINUS the duration of the reopen/rotation intersection, floored at zero. Reopen therefore wins the shared time. The defer layer is not part of this rule and keeps its independent union, so the three layers must not be assumed to interact alike. The rounding of each subtraction is unchanged and still governed by its own entry.

> **Governance decision (2026-05-25 - #DB-5358)** Nadia: trust contention (final). Each origin's `trust_exposure_score` is computed independently, so a target env reachable from several origins is currently counted by every one of them. A target reachable from MORE THAN ONE origin is charged to exactly ONE of them. For each such contended target, take the origins that reach it (its claimants) and pick the OWNER: the claimant whose strongest bounded simple-path score TO THAT TARGET is highest, ties broken by lexicographically smallest origin name. Note this is the per-target path score, NOT the origin's overall `trust_exposure_score` -- the two pick different owners. The owner adds that same per-target score to its own `trust_exposure_score`; every other claimant adds nothing for that target, and a target reachable from exactly one origin is not contended and adds nothing to anybody. The bonus is folded in BEFORE `trust_path_digest` is taken, so the digest commits to the attributed score. `trust_reachable_envs` and `trust_strongest_path` are unaffected: attribution changes what an origin SCORES, never what it reaches. Worked example: target t is reached by origins a (path score 9) and b (path score 4); a owns t and adds 9 to its own score, b adds 0, and t still appears in both origins' `trust_reachable_envs`.

### Review entry 0221 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0221. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0223 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0223. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0225 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0225. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0227 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0227. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0229 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0229. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0231 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0231. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0233 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0233. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0235 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0235. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0237 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0237. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0239 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0239. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0241 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0241. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.
> **Governance decision (2026-05-05 - #DB-5310)** Marek: defer layer: scope allowlist ['all', 'p1', 'p2']; normalize env/scope/start/end, keep rows whose severity_scope is in scope_values, drop end<=start, compact overlap/touch intervals per (env,severity_scope). Matching scopes: {all,max_severity} for each window; if max_severity is p2 and (env,p2) has no compacted intervals, borrow (env,p1) as the severity scope fallback. Union: collect overlap segments from matching scopes then compact/union those segments to compute defer_overlap_ms and defer_segment_count. actionable_duration_ms = max(dispatchable_duration_ms - ceil(defer_overlap_ms / 4), 0) — the defer overlap is quartered and rounded UP (ceiling), so a defer_overlap_ms not divisible by 4 subtracts one extra millisecond; this ceil form is final and revises the floor form `defer_overlap_ms // 4` in #DB-5221. defer_pressure_score (final, revising #DB-5225 which dropped the probe terms): probe [end_ms-300,end_ms+1): (all_defer_probe_ms//40)+(severity_defer_probe_ms//28)+defer_segment_count. ROUNDING: defer_overlap // 4 = CEIL.

### Review entry 0242 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0242. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0244 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0244. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0246 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0246. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0248 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0248. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0250 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0250. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0252 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0252. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0254 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0254. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0256 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0256. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0258 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0258. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0260 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0260. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0262 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0262. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.
> **Governance decision (2026-05-05 - #DB-5311)** Marek: probe scoring: all source intervals and probes are half-open; overlap is max(0,min(probe_end,interval_end)-max(probe_start,interval_start)). all_probe_ms uses only the already-compacted (env,all) intervals; severity_probe_ms uses already-compacted (env,max_severity) intervals, except p2 windows fall back to (env,p1) when (env,p2) is empty. do not union or deduplicate all-scope probe overlap against severity-scope probe overlap; an instant covered by both scopes contributes independently to both integer-division terms (supersedes #DB-4831). source intervals are compacted within each (env,severity_scope) before probing, so overlap is not duplicated within one scope. Probe endpoint: the +1 endpoint is literal: an anchor E with lookback L probes [E-L,E+1), whose duration is L+1 milliseconds before clipping.

### Review entry 0263 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0263. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0265 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0265. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0267 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0267. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0269 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0269. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0271 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0271. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0273 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0273. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0275 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0275. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0277 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0277. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0279 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0279. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0281 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0281. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0283 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0283. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.
> **Governance decision (2026-05-06 - #DB-5313)** Yusuf: risk ledger: state is independent per normalized env; process each env's merged windows in start_ms ascending order after all four attenuation layers are complete. First window: idle_gap_ms=0, carry_in_ms=0. idle_gap_ms: for later windows max(current.start_ms-previous.end_ms,0). carry_in_ms = max(previous.carry_out_ms-(idle_gap_ms//2),0). ledger_adjusted_actionable_ms = actionable_duration_ms+(carry_in_ms//4). carry_out_ms = min(carry_in_ms+actionable_duration_ms+(rotation_segment_count*15)+(defer_segment_count*10),2000). finalize carry_out_ms for one window before evaluating the next window in the same env. The //2 idle decay and the 2000 cap are final and revise #DB-5224. This supersedes #DB-4835. ROUNDING: idle_gap_ms // 2 = FLOOR. ROUNDING: carry_in_ms // 4 = FLOOR.

> **Governance decision (2026-05-17 - #DB-5346)** Yusuf: risk-ledger carry-out cap retuned (final, revising #DB-5313). The 2000 ms cap recorded there was set before the failover backlog was measured and never actually bound, which let a single long-running env accumulate carry without limit across a recovery shift. The cap is now 921 ms: `carry_out_ms = min(<computed carry>, 921)`. The cap is applied after the computed value, so a window whose computed carry is exactly 921 is unaffected and one above it is clamped down to 921. The `//2` idle decay, the carry-in formula and the ledger-adjusted credit recorded in #DB-5313 are unchanged.

### Review entry 0284 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0284. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0286 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0286. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0288 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0288. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0290 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0290. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0292 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0292. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0294 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0294. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0296 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0296. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0298 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0298. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0300 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0300. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0302 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0302. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0304 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0304. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.
> **Governance decision (2026-05-06 - #DB-5314)** Yusuf: ledger scoring (ledger_pressure_score is final, revising #DB-5212): ledger_pressure_score = (carry_out_ms//80)+(carry_in_ms//120)+max(alert_count-1,0); stability_index = volatility_index+defer_pressure_score+ledger_pressure_score — the ledger term is included, revising #DB-5216. Worked example, no attenuation: lab [100,400): actionable=300, idle_gap=0, carry_in=0, carry_out=min(0+300,2000)=300, ledger_adjusted=300 Then: lab [600,850): idle_gap=200, carry_in=max(300-(200//2),0)=200, actionable=250, ledger_adjusted=250+(200//4)=300, carry_out=min(200+250,2000)=450 Second window ledger pressure: (450//80)+(200//120)+max(1-1,0)=6.

### Review entry 0305 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0305. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0307 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0307. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0309 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0309. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0311 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0311. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0313 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0313. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0315 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0315. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0317 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0317. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0319 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0319. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0321 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0321. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0323 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0323. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0325 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0325. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.
> **Governance decision (2026-05-07 - #DB-5316)** Lena: replica topology edges: normalize source_env and target_env with canonicalization.env_normalization; coerce weight with int(str(value).strip()) and invalid to 0; discard self edges and weights outside 1..9 (the 1..9 bound is final and revises #DB-5227); collapse duplicate directed (source_env,target_env) rows by maximum weight. edges are directed from source_env to target_env.

### Review entry 0326 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0326. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0328 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0328. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0330 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0330. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0332 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0332. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0334 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0334. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0336 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0336. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0338 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0338. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0340 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0340. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0342 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0342. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0344 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0344. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0346 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0346. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.
> **Governance decision (2026-05-07 - #DB-5317)** Lena: trust traversal: for each drift window, begin at its normalized env and enumerate simple directed paths of one, two, or three edges (the three-edge bound is final and revises #DB-5227); a simple path never repeats a node, so cycles are bounded and the origin cannot reappear Path score: sum canonical edge weights along the path. This supersedes #DB-4840.

### Review entry 0347 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0347. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0349 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0349. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0351 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0351. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0353 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0353. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0355 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0355. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0357 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0357. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0359 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0359. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0361 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0361. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0363 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0363. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0365 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0365. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0367 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0367. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.
> **Governance decision (2026-05-08 - #DB-5319)** Priya: trust retention: for each reachable target retain the path with greatest path_score; on equal score retain the lexicographically smallest full node sequence. trust_reachable_envs: all retained target names sorted ascending. trust_exposure_score (final, revising #DB-5229 and the earlier per-target sum which double-counted shared hops): the maximum total weight of a set of **node-disjoint** bounded simple directed paths out of the origin env. Enumerate every simple directed path of 1, 2, or 3 edges from the origin — a path's weight is the sum of its edge weights and its node set is the non-origin envs it visits — then choose a subset of those paths that pairwise share **no** non-origin env, maximising the summed weight; the empty selection scores 0. This is NOT the sum of each reachable target's strongest path: two paths that reuse an env (even reaching different targets) cannot both be counted, so the exposure is the best node-disjoint packing. Use 0 when no target is reachable. trust_strongest_path: among retained target paths choose greatest path_score, then lexicographically smallest full node sequence; use [origin_env] when no target is reachable.

### Review entry 0368 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0368. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0370 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0370. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0372 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0372. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0374 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0374. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0376 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0376. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0378 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0378. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0380 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0380. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0382 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0382. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0384 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0384. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0386 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0386. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0388 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0388. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.
> **Governance decision (2026-05-08 - #DB-5320)** Priya: trust integration: stability_index=volatility_index+defer_pressure_score+ledger_pressure_score+(trust_exposure_score//2). Priority integration: critical when trust_exposure_score>=24; otherwise high when trust_exposure_score>=12, in addition to existing rules. ROUNDING: trust_exposure_score // 2 = FLOOR.

### Review entry 0389 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0389. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0391 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0391. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0393 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0393. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0395 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0395. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0397 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0397. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0399 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0399. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0401 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0401. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0403 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0403. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0405 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0405. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0407 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0407. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0409 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0409. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.
> **Governance decision (2026-05-09 - #DB-5322)** Marek: queue admission: minimum ledger_adjusted_actionable_ms per max_severity is {'p1': 222, 'p2': 242}; admitted severities are ['p1', 'p2']. These floors are inclusive (a window whose ledger_adjusted_actionable_ms equals its floor is admitted) and they are final, revising the looser 180/225 pair circulated during the March review.

> **Governance decision (2026-05-18 - #DB-5350)** Priya: recovery policy baseline. Every threshold the reconciler applies is a policy value, not a global constant, and is read from `/app/data/recovery_policies.json` at that fixed absolute path — `--input` selects the alert stream only and never relocates the policy file. The approved baseline, used for any field the policy file does not supply, is: `admission_min_p1` = 222; `admission_min_p2` = 242; `critical_p1_ledger_min` = 437; `critical_ledger_min` = 550; `critical_stability_min` = 33; `critical_trust_min` = 35; `high_ledger_min` = 407; `high_risk_adjusted_min` = 340; `high_dispatchable_min` = 320; `high_duration_min` = 420; `high_trust_min` = 12; `carry_out_cap` = 921; `stitch_gap_ms` = 60. These supersede the corresponding literals recorded in #DB-5304, #DB-5313, #DB-5322 and #DB-5344, which are retained only as the baseline values above.

> **Governance decision (2026-05-18 - #DB-5352)** Priya: policy resolution, applied per normalized env in three layers. Start from the approved baseline of #DB-5350. Overlay every field the policy file's `default` object supplies — it may differ from the baseline and it need not be complete, so a field it omits keeps its baseline value. Then overlay every field that env's entry in `env_overrides` supplies. An override is never a complete policy: it names only the fields it changes and inherits the rest from the layer beneath it, so an env listing one field differs from the resolved default in that one field alone. An env with no entry in `env_overrides` resolves to the overlaid default. Coerce every policy value with the same millisecond coercion used elsewhere. `policy_checksum` is the SHA-256 hex digest of one line per resolved policy — first `default`, then each env named in `env_overrides` in ascending name order — each line being the env name followed by the thirteen field values in the order they are listed in #DB-5350, joined by `|`, lines joined by a single newline with no trailing newline, hashed over UTF-8.

### Review entry 0410 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0410. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0412 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0412. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0414 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0414. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0416 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0416. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0418 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0418. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0420 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0420. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0422 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0422. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0424 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0424. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0426 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0426. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0428 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0428. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0430 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0430. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.
> **Governance decision (2026-05-09 - #DB-5323)** Marek: priority rules: critical — max_severity == p1 and ledger_adjusted_actionable_ms >= 235, or ledger_adjusted_actionable_ms >= 500, or stability_index >= 20, or trust_exposure_score >= 24. high — ledger_adjusted_actionable_ms >= 265, or alert_count >= 3 with max_severity in {p1,p2}, or rotation_segment_count == 0 with risk_adjusted_duration_ms >= 340, or defer_pressure_score > 0 with dispatchable_duration_ms >= 320, or reopen_segment_count == 0 with duration_ms >= 420, or trust_exposure_score >= 12. Otherwise otherwise.

> **Governance decision (2026-05-16 - #DB-5344)** Marek: priority thresholds retuned (final, revising #DB-5323). The recovery review found the critical cutoffs were absorbing almost the whole queue, so the high tier never applied and responders lost the distinction entirely. Critical now requires: max_severity == p1 with ledger_adjusted_actionable_ms >= 437; or ledger_adjusted_actionable_ms >= 550; or stability_index >= 33; or trust_exposure_score >= 35. High, evaluated only when critical does not hold, now requires: ledger_adjusted_actionable_ms >= 407; or alert_count >= 2 with max_severity in {p1, p2}; or rotation_segment_count == 0 with risk_adjusted_duration_ms >= 340; or defer_pressure_score > 0 with dispatchable_duration_ms >= 320; or reopen_segment_count == 0 with duration_ms >= 420; or trust_exposure_score >= 12. Otherwise medium. Every threshold in this entry replaces the corresponding one in #DB-5323; the clause structure and evaluation order are unchanged, and the alert_count term moves from 3 to 2. This supersedes the thresholds in #DB-5323.

### Review entry 0431 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0431. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0433 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0433. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0435 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0435. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0437 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0437. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0439 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0439. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0441 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0441. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0443 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0443. replica topology edge audit sampled cross-account roles; no reconciler-relevant findings for this lane.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0445 — dmz lane
Shift lead logged a routine recovery observation for dmz (west) during review window 0445. Rule-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0447 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0447. Quarterly access recertification touched this lane; no compile-relevant configuration changed.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.

### Review entry 0449 — staging lane
Shift lead logged a routine recovery observation for staging (west) during review window 0449. Capacity review noted rising alert volume; thresholds unchanged outside the governance process.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

### Review entry 0451 — edge lane
Shift lead logged a routine recovery observation for edge (central) during review window 0451. Dashboard tiles for drift volume lagged during rule refresh; attributed to cache staleness, not the reconciler.
Thread archived; see the #DB decision entries for anything affecting reconciler behavior.
> **Governance decision (2026-05-10 - #DB-5325)** Yusuf: final queue ordering, applied strictly in sequence: priority rank critical>high>medium; then ledger_adjusted_actionable_ms desc; then actionable_duration_ms desc; then stability_index desc; then trust_exposure_score desc; then defer_pressure_score desc; then volatility_index desc; then dispatchable_duration_ms desc; then risk_adjusted_duration_ms desc; then freeze_segment_count desc; then alert_count desc; then env asc; then start_ms asc.

> **Governance decision (2026-05-24 - #DB-5356)** Marek: responder capacity cap. A single environment was filling the recovery queue and starving the others, so the queue is now capped at THREE rows per normalized env. The cap is applied as a final pass over the fully ordered queue, not during admission and not per env before ordering: build the queue, admit and prioritise every window as before, apply the complete ordering chain of #DB-5325, and only then walk the ordered queue from the top keeping the first three rows of each env and discarding the rest. Which rows survive therefore depends on the global order, so a window that would rank fourth within its env is dropped even when it outranks a retained row from another env. The discarded rows are not re-admitted anywhere and do not contribute to any queue-derived summary field.

### Review entry 0451 — core lane
> **Governance decision (2026-05-10 - #DB-5327)** Yusuf: summary score aggregation domains (final, revising #DB-5231): the six `max_*` **score** fields — `max_stability_pressure_score`, `max_volatility_index`, `max_defer_pressure_score`, `max_ledger_pressure_score`, `max_trust_exposure_score`, and `max_stability_index` — are maxima over the **final admitted response_queue rows only**, using 0 when the queue is empty. Only `max_carry_out_ms` is taken over **every drift window** (admitted or not), 0 when there are no windows. The earlier all-windows form for the score fields in #DB-5231 counted attenuated windows that never reach a responder and is not the shipped behavior; this matches the `maximum_aggregation_domains` split in report_spec.json.

### Review entry 0731 — probe bench
> **Governance decision (2026-05-14 - #DB-5332)** Rosa: recovery-probe review found the severity-scoped half of the stability probe was systematically under-counting partial probe windows, because a scoped overlap shorter than one full divisor step scored zero. That term therefore ROUNDS UP: `stability_pressure_score = (all_probe_ms // 30) + ceil(severity_probe_ms / 20) + max(alert_count - 1, 0)`. Only the severity-scoped term rounds up; the `all`-scoped term keeps its floor, and the alert-count term is unchanged. In integer arithmetic ceil(x/20) is -(-x // 20). This revises the floored severity term recorded in #DB-5307. ROUNDING: all_probe_ms // 30 = FLOOR. ROUNDING: severity_probe_ms // 20 = CEIL.

### Review entry 0733 — probe bench
> **Governance decision (2026-05-14 - #DB-5334)** Rosa: the same under-count applies to the rotation probe, and is corrected the same way: `volatility_index = stability_pressure_score + (all_rotation_probe_ms // 24) + ceil(severity_rotation_probe_ms / 16) + (rotation_segment_count * 2)`. The `all`-scoped rotation term stays floored and the segment term is unchanged. This revises the floored severity term recorded in #DB-5308. ROUNDING: all_rotation_probe_ms // 24 = FLOOR. ROUNDING: severity_rotation_probe_ms // 16 = CEIL.

### Review entry 0735 — probe bench
> **Governance decision (2026-05-15 - #DB-5336)** Marek: defer probe, same correction: `defer_pressure_score = (all_defer_probe_ms // 40) + ceil(severity_defer_probe_ms / 28) + defer_segment_count`. The `all`-scoped defer term stays floored. This revises the floored severity term recorded in #DB-5310. ROUNDING: all_defer_probe_ms // 40 = FLOOR. ROUNDING: severity_defer_probe_ms // 28 = CEIL.

### Review entry 0737 — ledger bench
> **Governance decision (2026-05-15 - #DB-5338)** Yusuf: the carry-in half of the ledger pressure score suffered the same partial-step loss, so it rounds up while the carry-out half does not: `ledger_pressure_score = (carry_out_ms // 80) + ceil(carry_in_ms / 120) + max(alert_count - 1, 0)`. The 80 carry-out divisor and the alert term recorded in #DB-5314 are unchanged, and the worked example in that entry predates this correction. This revises the floored carry-in term in #DB-5314. ROUNDING: carry_out_ms // 80 = FLOOR. ROUNDING: carry_in_ms // 120 = CEIL.

### Review entry 0739 — probe bench
> **Governance decision (2026-05-15 - #DB-5340)** Yusuf: recording the rounding map settled across #DB-5332, #DB-5334, #DB-5336 and #DB-5338 for the avoidance of doubt: rounding is NOT uniform across the pipeline and no layer's rounding may be inferred from another's. Each divisor's direction is fixed by its own governing decision and must be read there.
Shift lead logged a routine recovery observation for core (east) during review window 0451. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0452 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0452. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0454 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0454. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0456 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0456. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0458 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0458. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0460 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0460. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0462 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0462. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0464 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0464. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0466 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0466. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0468 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0468. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0470 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0470. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0472 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0472. Change-board reviewed stale exception approvals; owners pinged before the next recovery cycle.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0474 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0474. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0476 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0476. Noise review: repeated drift alerts traced to a flapping policy probe, muted at the source.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0478 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0478. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0480 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0480. Replica checksum sync drill completed; drift alert acknowledgment stayed within the governance SLO.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0482 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0482. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0484 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0484. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0486 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0486. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0488 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0488. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0490 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0490. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0492 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0492. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0494 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0494. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0496 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0496. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0498 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0498. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0500 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0500. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0502 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0502. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0504 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0504. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0506 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0506. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0508 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0508. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0510 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0510. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0512 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0512. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0514 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0514. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0516 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0516. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0518 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0518. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0520 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0520. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0522 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0522. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0524 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0524. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0526 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0526. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0528 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0528. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0530 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0530. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0532 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0532. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0534 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0534. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0536 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0536. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0538 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0538. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0540 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0540. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0542 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0542. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0544 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0544. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0546 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0546. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0548 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0548. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0550 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0550. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0552 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0552. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0554 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0554. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0556 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0556. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0558 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0558. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0560 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0560. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0562 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0562. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0564 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0564. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0566 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0566. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0568 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0568. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0570 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0570. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0572 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0572. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0574 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0574. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0576 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0576. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0578 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0578. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0580 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0580. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0582 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0582. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0584 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0584. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0586 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0586. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0588 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0588. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0590 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0590. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0592 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0592. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0594 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0594. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0596 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0596. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0598 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0598. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0600 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0600. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0602 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0602. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0604 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0604. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0606 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0606. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0608 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0608. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0610 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0610. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0612 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0612. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0614 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0614. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0616 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0616. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0618 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0618. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0620 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0620. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0622 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0622. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0624 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0624. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0626 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0626. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0628 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0628. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0630 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0630. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0632 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0632. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0634 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0634. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0636 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0636. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0638 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0638. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0640 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0640. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0642 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0642. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0644 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0644. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0646 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0646. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0648 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0648. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0650 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0650. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0652 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0652. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0654 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0654. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0656 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0656. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0658 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0658. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0660 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0660. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0662 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0662. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0664 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0664. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0666 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0666. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0668 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0668. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0670 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0670. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0672 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0672. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0674 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0674. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0676 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0676. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0678 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0678. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0680 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0680. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0682 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0682. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0684 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0684. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0686 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0686. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0688 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0688. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0690 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0690. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0692 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0692. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0694 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0694. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0696 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0696. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0698 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0698. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0700 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0700. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0702 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0702. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0704 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0704. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0706 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0706. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0708 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0708. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0710 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0710. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0712 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0712. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0714 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0714. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0716 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0716. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0718 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0718. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0720 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0720. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0722 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0722. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0724 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0724. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0726 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0726. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0728 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0728. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0730 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0730. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0732 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0732. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0734 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0734. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0736 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0736. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0738 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0738. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0740 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0740. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0742 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0742. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0744 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0744. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0746 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0746. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0748 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0748. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0750 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0750. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0752 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0752. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0754 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0754. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0756 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0756. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0758 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0758. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0760 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0760. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0762 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0762. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0764 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0764. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0766 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0766. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0768 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0768. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0770 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0770. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0772 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0772. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0774 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0774. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0776 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0776. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0778 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0778. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0780 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0780. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0782 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0782. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0784 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0784. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0786 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0786. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0788 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0788. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0790 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0790. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0792 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0792. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0794 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0794. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0796 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0796. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0798 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0798. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0800 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0800. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0802 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0802. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0804 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0804. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0806 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0806. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0808 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0808. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0810 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0810. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0812 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0812. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0814 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0814. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0816 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0816. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0818 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0818. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0820 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0820. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0822 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0822. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0824 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0824. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0826 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0826. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0828 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0828. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0830 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0830. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0832 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0832. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0834 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0834. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0836 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0836. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0838 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0838. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0840 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0840. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0842 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0842. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0844 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0844. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0846 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0846. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0848 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0848. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0850 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0850. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0852 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0852. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0854 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0854. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0856 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0856. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0858 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0858. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0860 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0860. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0862 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0862. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0864 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0864. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0866 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0866. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0868 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0868. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0870 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0870. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0872 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0872. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0874 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0874. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0876 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0876. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0878 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0878. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0880 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0880. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0882 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0882. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0884 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0884. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0886 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0886. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0888 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0888. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0890 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0890. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0892 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0892. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0894 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0894. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0896 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0896. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0898 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0898. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0900 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0900. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0902 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0902. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0904 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0904. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0906 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0906. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0908 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0908. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0910 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0910. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0912 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0912. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0914 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0914. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0916 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0916. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0918 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0918. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0920 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0920. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0922 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0922. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0924 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0924. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0926 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0926. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0928 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0928. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0930 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0930. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0932 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0932. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0934 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0934. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0936 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0936. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0938 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0938. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0940 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0940. Point-in-time-restore maintenance window observed; no recovery-relevant configuration changed in this lane.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0942 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0942. Checkpoint cadence reviewed; delivery within the governance SLO for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0944 — prod lane
Shift lead logged a routine recovery observation for prod (east) during review window 0944. Quarterly standby recertification touched this lane; no compile-relevant configuration changed.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0946 — lab lane
Shift lead logged a routine recovery observation for lab (north) during review window 0946. Synthetic drift injection verified on-call alert delivery to the containment rotation for this region.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0948 — core lane
Shift lead logged a routine recovery observation for core (east) during review window 0948. Backup-set rollback rehearsal ran clean; no changes to recovery parameters were approved.
Historical CSV exports remain archived and non-authoritative for the JSON reconciler acceptance.

### Review entry 0950 — vault lane
Shift lead logged a routine recovery observation for vault (north) during review window 0950. Change-board reviewed stale replication-slot approvals; owners pinged before the next recovery cycle.
No reconciler semantics changed in this entry; parameters remain as approved by the governance board.

### Review entry 0951 — fabric lane
Shift lead logged a routine recovery observation for fabric (central) during review window 0951. Vendor ticket on replication-callback retries closed; delivery within contractual budget.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

## Late governance close-out (2026-05 recovery review, final)

> **Governance decision (2026-05-28 - #DB-5360)** Yusuf: risk-ledger carry-chain rounding, final. Re-measuring the failover backlog showed the floored carry chain was shedding a partial step at both the idle-gap decay and the carry-in credit, so BOTH now ROUND UP (ceiling): `carry_in_ms = max(previous.carry_out_ms - ceil(idle_gap_ms / 2), 0)` and `ledger_adjusted_actionable_ms = actionable_duration_ms + ceil(carry_in_ms / 4)`. In integer arithmetic ceil(x/n) is -(-x // n). This is final and revises the floored `idle_gap_ms // 2` and `carry_in_ms // 4` recorded in #DB-5313 — and reaffirmed as unchanged in #DB-5346 — on those two rounding points only: the per-env ordering, the idle-gap and carry-in formulas, the 921 ms carry-out cap from #DB-5346, and the carry-out composition are all unchanged. The #DB-5313 and #DB-5314 worked examples predate this correction and floor both terms, so their carry figures are stale on this point. ROUNDING: idle_gap_ms // 2 = CEIL. ROUNDING: carry_in_ms // 4 = CEIL.

> **Governance decision (2026-05-29 - #DB-5362)** Yusuf: ledger pressure rounding, final. The carry-OUT half of the ledger pressure score suffered the same partial-step loss as the carry-in half did in #DB-5338, so it now ROUNDS UP as well and BOTH ledger-pressure halves ceil: `ledger_pressure_score = ceil(carry_out_ms / 80) + ceil(carry_in_ms / 120) + max(alert_count - 1, 0)`. In integer arithmetic ceil(x/80) is -(-x // 80). This is final and revises the floored `carry_out_ms // 80` recorded in #DB-5314 and left floored in #DB-5338, on that one rounding point only: the 80 carry-out divisor, the 120 carry-in ceiling and the alert term are unchanged. The #DB-5314 worked example predates this correction and floors the carry-out half (it shows 450 // 80 = 5, whereas the final ceiling gives 6), so that figure is stale on this point. ROUNDING: carry_out_ms // 80 = CEIL.

> **Governance decision (2026-05-30 - #DB-5364)** Nadia: reopen/rotation precedence extends to the segment COUNT, final. #DB-5354 removed the reopen/rotation intersection from `rotation_overlap_ms` but left `rotation_segment_count` as the full compacted-segment count; that undercharged reopen precedence, because a rotation segment reopen had entirely swallowed still counted toward carry-out, volatility and the zero-rotation priority checks. The count now follows the same precedence: after compacting each window's rotation segments, a segment whose span is ENTIRELY covered by the window's compacted reopen coverage is ceded to reopen and is EXCLUDED from `rotation_segment_count`; a segment reopen covers only partially is RETAINED in full — rotation still owns its uncovered remainder, so it is neither split nor dropped. Concretely: count the compacted rotation segments for which the summed reopen coverage of the segment is strictly less than the segment's own length. `rotation_overlap_ms` is unchanged by this entry — it keeps the #DB-5354 intersection subtraction — and the defer layer stays independent of both. Neither "keep every overlapping segment" nor "drop every segment reopen touches" is correct: only fully-covered segments drop. This revises #DB-5354 on the segment-count point only.
Reviewers should reconcile behavior questions against #DB governance decisions rather than chat excerpts.

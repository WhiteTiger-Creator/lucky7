# Database replication-failover drift incident containment

Act as the platform operations engineer responding to a failed database replication-failover rollout. The failover automation left persistence and escalation paths on the database host: a rogue automation key in root's `authorized_keys`, a passwordless sudoers drop-in, and a world-readable streaming-replication credential. First contain the host to match `/app/docs/containment_runbook.md` — revoke the automation's SSH persistence, remove its privilege escalation, and lock down the exposed credential.

Then restore `/app/workflow/export_report.py`, the control-plane reconciler that converts replication-drift alerts into responder recovery work. Preserve its operational CLI: `--input PATH` and `--output-dir PATH`, defaulting to `/app/data/events.json` and `/app/output`.

This is control-plane reconciliation, not application feature development. The resulting artifacts decide which replication drifts require immediate recovery, which are attenuated by approved policy windows, and how risk carries between repeated drifts in the same environment.

Always read freezes and scoped attenuation policies from their fixed absolute paths:
`/app/data/change_freezes.json`, `/app/data/reopen_windows.json`, `/app/data/rotation_windows.json`, `/app/data/defer_windows.json`, and `/app/data/replica_topology_edges.json`. `--input` changes only the event stream; policy files never become relative to input/output directories.

`/app/docs/report_spec.json` is the output contract: file paths, schemas, required fields, repair tokens, digest payloads, and byte-level checksum serialization. Match it exactly.

How the reconciler actually behaves is not in the contract — canonicalization, deduplication, window merging, the freeze/reopen/rotation/defer attenuation layers and their scope rules, probe scoring, the sequential risk ledger, replica topology traversal, queue admission, priority, and ordering all got settled by the recovery governance board, and `/app/incident/recovery_review_log.md` is where that record lives. It's long, most of it is routine noise, and the February recovery drafts were revisited later and partly reversed — several March interim positions were revised again in May — so read it as a decision record that resolves over time rather than a list of facts each individually true, and follow the latest decision on every point. Every value you emit has to be derived from the operational inputs, and the reconciler must keep working when pointed at a different alert stream.

Write exactly `summary.json`, `drift_windows.json`, and compact `response_queue.jsonl` under the requested output directory. These are operational evidence and responder-queue artifacts: they must generalize to alternate alert streams, remain idempotent across reruns, and derive only from operational sources. Keep the frozen incident snapshot `/app/workflow/.export_report.original` unchanged and never read/import verifier artifacts.

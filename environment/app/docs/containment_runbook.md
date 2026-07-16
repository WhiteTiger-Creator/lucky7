# Post-Rollout Containment Runbook

Required hardened state for database hosts touched by the failed replication-failover rollout. The failover automation provisioned itself with persistence and escalation paths that must be removed during containment; the reconciler restore does not begin until the host matches this runbook.

## SSH persistence

The failover automation appended its deploy key to root's `authorized_keys`, identified by the key comment `replication-failover-automation`. Revoke it: no entry carrying that comment may remain in `/root/.ssh/authorized_keys`. Other entries in the file, if any, are legitimate and stay.

## Privilege escalation

The rollout installed a temporary sudoers drop-in at `/etc/sudoers.d/replication-failover` granting `svc-postgres` passwordless root. Remove the file entirely — do not comment it out or narrow it.

## Credential exposure

The streaming-replication credential at `/app/secrets/replication.cred` was written world-readable. The credential itself remains valid and the database still needs it in place: keep the file, owned `root:root`, mode `0600`.

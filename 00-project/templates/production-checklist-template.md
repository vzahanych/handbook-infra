# <Tool name> — production checklist

Use before go-live and during periodic reviews.

## Architecture & capacity

- [ ] Topology documented (nodes, roles, zones)
- [ ] Capacity plan defined (CPU, memory, disk, network)
- [ ] Single points of failure identified and mitigated or accepted
- [ ] Dependencies mapped (DNS, storage, identity, network)

## Security

- [ ] TLS enabled for client and inter-node traffic where applicable
- [ ] Authentication and authorization configured
- [ ] Secrets stored in vault/KMS, not in plain config
- [ ] Network policies / firewall rules least-privilege
- [ ] Admin interfaces not exposed publicly

## Reliability

- [ ] HA or failover strategy tested
- [ ] Backup schedule defined and tested restore performed
- [ ] RPO/RTO documented
- [ ] Upgrade/rollback procedure documented

## Observability

- [ ] Health endpoints or probes configured
- [ ] Metrics exported and dashboards created
- [ ] Logs centralized with retention policy
- [ ] Alerts defined for SLO-critical signals
- [ ] Runbooks linked from alerts

## Operations

- [ ] On-call ownership defined
- [ ] Change management process agreed
- [ ] Config under version control
- [ ] Disaster recovery drill scheduled

## Sign-off

| Role | Name | Date |
|------|------|------|
| Owner | | |
| Reviewer | | |

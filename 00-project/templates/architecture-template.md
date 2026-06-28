# <Tool name> — architecture

## Overview

Brief description of the system's purpose and major components.

## Component diagram

```mermaid
flowchart LR
  Client --> Gateway
  Gateway --> Service
  Service --> Storage
```

## Components

| Component | Role | Notes |
|-----------|------|-------|
| | | |

## Data flow

1. 
2. 
3. 

## Deployment topologies

### Single node

- Use case: dev, PoC
- Risks: no HA

### Clustered / HA

- Use case: production
- Notes: quorum, split-brain, load balancing

## Dependencies

- **Upstream**: 
- **Downstream**: 

## Storage & state

- What is persisted:
- Where state lives:
- Backup implications:

## Security boundaries

- Trust zones:
- Authentication points:
- Encryption in transit / at rest:

## Scaling dimensions

- Vertical:
- Horizontal:
- Limits:

## Failure modes

| Failure | Impact | Mitigation |
|---------|--------|------------|
| | | |

## References

- Official architecture docs: 

# Mermaid Diagramming Blueprints in StackEdit++

> **Platform**: [StackEdit++](https://stackeditplusplus.meshworld.in) • [Live App](https://stackeditplusplus.meshworld.in/app)  
> **Engine**: Mermaid 11.x (Modern client-side diagramming & charting)

---

## Overview

StackEdit++ natively renders code-defined architecture diagrams, sequence flows, and entity-relationship models via **Mermaid 11.x**. Diagram code blocks are parsed and converted to SVG vectors on the fly directly inside browser memory.

To declare a diagram, fence your code block with ```` ```mermaid ````:

```markdown
```mermaid
flowchart LR
    A[Client Request] --> B[Edge Reverse Proxy]
    B --> C{Authentication}
    C -->|Valid JWT| D[App Service]
    C -->|Invalid| E[401 Unauthorized]
```
```

---

## 1. Production Architecture Patterns

### Distributed System Flow with Subgraphs

```markdown
```mermaid
flowchart TD
    subgraph ClientZone["Client Ingress"]
        Browser["User Browser (PWA)"]
        Mobile["Mobile Web Client"]
    end

    subgraph EdgeZone["Edge & Routing"]
        CDN["Global Edge CDN"]
        Gateway["API Gateway / WAF"]
    end

    subgraph ServiceMesh["Zero-Trust Mesh"]
        AuthSvc["Auth Service"]
        DocSvc["Document Service"]
        SyncSvc["Sync Worker"]
    end

    subgraph StorageLayer["Data & Persistence"]
        DB[("PostgreSQL")]
        Cache[("Redis Cluster")]
    end

    Browser --> CDN
    Mobile --> CDN
    CDN --> Gateway
    Gateway --> AuthSvc
    Gateway --> DocSvc
    DocSvc --> Cache
    DocSvc --> DB
    SyncSvc --> DB
```
```

### Microservice Authentication Sequence

```markdown
```mermaid
sequenceDiagram
    autonumber
    actor User as Client Application
    participant Edge as API Gateway
    participant Auth as Auth Service
    participant Vault as Key Store

    User->>Edge: POST /api/v1/auth/session (Credentials)
    activate Edge
    Edge->>Auth: Validate Credentials
    activate Auth
    Auth->>Vault: Fetch Signing Key (RS256)
    Vault-->>Auth: Private Key Reference
    Auth-->>Edge: Issue Session Token (JWT)
    deactivate Auth
    Edge-->>User: 200 OK + HttpOnly Cookie
    deactivate Edge

    Note over User,Edge: Subsequent Authorized Requests
    User->>Edge: GET /api/v1/data (Bearer Token)
    activate Edge
    Edge->>Edge: Verify Cryptographic Signature (Local RAM)
    Edge-->>User: 200 OK (Protected Payload)
    deactivate Edge
```
```

### State Machine Lifecycle

```markdown
```mermaid
stateDiagram-v2
    [*] --> Draft : Create Note
    Draft --> Staged : Save Local Draft
    Staged --> Validated : Lint & Check Ast
    Validated --> Published : Export HTML / PDF
    Published --> Archived : Archive Note
    Archived --> [*] : Delete from Local DB

    Draft --> [*] : Discard Draft
```
```

---

## 2. Best Practices & Syntax Rules

1. **Quote Strings with Special Characters**: If a node label contains parentheses, brackets, or math symbols, enclose it in double quotes:
   ```mermaid
   nodeA["Processing Data (Batch v2)"] --> nodeB["Storage [Partition 1]"]
   ```
2. **Direction Flags**: Use `TD` (top-down) for deep hierarchies and `LR` (left-right) for timelines or horizontal pipeline stages.
3. **Avoid Raw HTML Tags in Labels**: Stick to plain text and markdown bolding inside labels to maintain cross-browser SVG compatibility.

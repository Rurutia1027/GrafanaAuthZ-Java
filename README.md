# Grafana AuthZ Java 
Java / Spring rewrite of Grafana **Identity & Security** capabilities, based on the extracted Go auth stack ([`Grafana-Identification`](../security-topic/Grafana-Identification)) and upstream [`grafana`](../grafana). 

> **Current stage: plan only -- no application code yet.** Implementation starts after plan review.

## Documentation 
| Document | Description |
|----------|-------------|
| **[PLAN.en.md](./PLAN.en.md)** | Master plan: scope, APIs, storage, CORS, architecture diagrams, phased Java roadmap |
| **[AUTH-README.md](./AUTH-README.md)** | Authentication & authorization overview (concepts, flows, APIs, storage) |
| [docs/capability-matrix.en.md](./docs/capability-matrix.en.md) | Full Identity & Security capability matrix (OSS / Enterprise / extraction gaps) |

Chinese versions: [README.md](./README.md) · [PLAN.md](./PLAN.md) · [docs/capability-matrix.md](./docs/capability-matrix.md)

## Related repositories

| Repository | Role |
|------------|------|
| `security-topic/Grafana-Identification` | Extracted Go auth code + `grafana-authd` (reference / regression baseline) |
| `architecture/grafana` | Upstream Grafana source |
| `architecture/GrafanaAuthZ-Java` | Existing design docs (RBAC, OIDC, schema, etc.) |
| `security-topic/Grafana-RBAC-Insights` | RBAC research notes |


## Principles
- **Behavior aligned with Grafana >= 12** -- identity model, AuthN client priority, RBAC action / scope, session and token semantics first.
- **Spring Security as enforcement layer** -- Filter Chain maps to Go `contexthandler` + `middleware` + `accesscontrol.Middleware`.
- **Classic RBAC before ZanZana** - ship Evaluate / permission loading first; OpenFGA optional later.
- **Multi-tenancy = Org + Namespace** - request context carries `orgId`; cloud scenarios retain namespace claims.


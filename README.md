# Cloud-Native RBAC & Authorization Framework 

## Overview 
This project focuses on designing a cloud-native authorization system inspired by Grafana's (versio >= 12.0) RBAC model.
The main goal is to enable fine-grained access control for APIs, resources, and services, using a Java Spring ecosystem.
It is intended as a foundation for building multi-tenant, secure, and cloud-compatible applications. 

---

## Objectives 
### Role-Based Access Control (RBAC)
- Define roles and permissions for system users and service accounts. 
- Map roles to resources and allowed actions at a granular level (create, read, update, delete, etc.).
- Support hierarchical roles and inheritance where needed. 


### Authorization Mechanism 
- Centralize authentication and authorization logic.
- Enforce policy decisions consistently across services.
- Integrate with Spring Security for web endpoints and API gateway enforcement.


### Token Management 
- Use tokens for user and service account authentication.
- Support long-lived and short-lived tokens for different scenaros.
- Enable token revocation, rotation, and auditing.
- Ensure compatibility with cloud-native, identity providers if needed. 


### API-Level Role Enforcement
- Apply role-based permissions directly on API endpoints
- Differentiate between resource types (dashboards, folders, data sources, etc.).
- Enable per-organization and per-user scoping of API operations. 
- Provide audit logs and visibility for token usage and access patterns. 


### Cloud-Native Design Considerations
- Ensure the system is compatible with Kubernetes and service mesh environments. 
- Support multi-tenant deployments with isolated authorization contexts. 
- Design for observability: logs, metrics, and tracing of authorization decisions.
- Future-proof the system for integration with other cloud-native applications and services. 


---
## Reference Architecture
- **Identity Layer**: Handles authentication, token issuance, and session management. 
- **Policy Layer**: Centralized policy definitions based on roles, permissions, and resources. 
- **Enforcement Layer**: Intercepts API calls and validates tokens and role permissions.
- **Audit & Monitoring**: Tracks access requests, token usage, and policy violations.

---


## Goals for Implementation 
- Enable consistent and centralized RBAC enforcement for all microservices. 
- Provide extensible for new roles, resources, and permissions. 
- Achieve separation of concerns between authentication, authorization, and business logic.
- Prepare the system for cloud-native deployment scenarios and multi-tenant architectures.

---

## Design Documentation

Comprehensive design documents analyzing Grafana's identity, authentication, authorization, and RBAC systems:

### 📚 [Documentation Index](./docs/00-Index.md)

1. **[Identity & Authentication Architecture](./docs/01-Identity-Authentication-Architecture.md)**
   - Core identity model, authentication mechanisms, user management
   - Password, OAuth, LDAP, SAML, JWT, Session authentication
   - Service accounts and multi-tenancy

2. **[Authorization & RBAC System](./docs/02-Authorization-RBAC-System.md)**
   - Role-based access control, permissions, authorization enforcement
   - Role types, permission model, role bindings
   - Zanzana/OpenFGA integration

3. **[Database Schema Design](./docs/03-Database-Schema-Design.md)**
   - Database table structures and relationships
   - Identity, RBAC, and authentication tables
   - Index strategies and query optimization

4. **[OIDC/OAuth Implementation](./docs/04-OIDC-OAuth-Implementation.md)**
   - OAuth 2.0 and OIDC integration patterns
   - Provider support (Azure AD, Google, GitHub, etc.)
   - Role mapping and token management

5. **[Kubernetes & Cloud-Native Integration](./docs/05-K8s-Cloud-Native-Integration.md)**
   - Kubernetes service account integration
   - Workload identity (Azure, GCP, AWS)
   - Service mesh integration and multi-tenancy

6. **[Token Management & JWT](./docs/06-Token-Management-JWT.md)**
   - JWT generation, validation, and signing
   - Key management and rotation
   - Token lifecycle management

7. **[Technology Stack Selection](./docs/07-Technology-Stack-Selection.md)**
   - Complete technology stack for Java/Spring Boot implementation
   - Framework, gateway, database, cache selections
   - Dependencies and configuration recommendations

8. **[Cloud-Native mTLS & Zero-Trust Security](./docs/08-Cloud-Native-mTLS-Security.md)**
   - Platform-level security with mTLS and Istio
   - Kubernetes certificate management
   - Service mesh authorization policies
   - SPIFFE/SPIRE integration
   - Zero-trust architecture implementation

9. **[IDM Service Insights & Additional Design Considerations](./docs/09-IDM-Service-Insights.md)**
   - Additional patterns from enterprise IDM systems
   - Token storage architecture with digest optimization
   - SCIM protocol support for provisioning
   - Advanced authentication methods
   - Audit logging and compliance patterns
   - Token moduleization and filter chain patterns

## Quick Start

1. **Read the [Documentation Index](./docs/00-Index.md)** for an overview
2. **Review design documents** based on your implementation priorities
3. **Follow the implementation roadmap** outlined in the index
4. **Reference Grafana source code** at `/Users/emma/architecture/grafana` for implementation details
5. **Review IDM Service insights** at `/Users/emma/architecture/with-cursor/idm-service` for additional enterprise patterns

## Technology Stack

This project implements Grafana's RBAC and identity system using the following technology stack:

### Core Framework
- **Java** 17+ with **Spring Boot** 3.2.x
- **Spring Security** 6.x - Authentication & Authorization framework
- **Spring Data JPA** - Data persistence layer

### API Gateway
- **Spring Cloud Gateway** 4.x - Reactive API gateway with OAuth2 integration

### Database & Persistence
- **PostgreSQL** 15+ - Primary database with row-level security support
- **Flyway** - Database migration tool
- **HikariCP** - High-performance connection pooling

### Caching
- **Redis** 7.x - Distributed caching and session storage
- **Caffeine** - Local L1 cache for high-frequency data

### Authentication & Authorization
- **Spring Security OAuth2 Client** - OAuth2/OIDC integration
- **Nimbus JOSE + JWT** - JWT generation and validation
- **Spring Security Method Security** - Annotation-based authorization

### Cloud-Native
- **Spring Cloud Kubernetes** - Kubernetes integration
- **Fabric8 Kubernetes Client** - K8s API client
- **Docker** - Containerization

### Monitoring & Observability
- **Micrometer** - Metrics collection
- **Prometheus** - Metrics storage
- **OpenTelemetry** - Distributed tracing

### Development Tools
- **Maven** - Build tool
- **JUnit 5** - Testing framework
- **Testcontainers** - Integration testing
- **SpringDoc OpenAPI** - API documentation

> **Note**: This implementation focuses on reconstructing Grafana's permission system using Java/Spring Boot. Future consideration includes migrating to **Quarkus** for improved startup time, lower memory footprint, and native compilation support. 
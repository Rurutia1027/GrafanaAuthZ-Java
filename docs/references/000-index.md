# Reference Protocols 

## OAuth 2.0 -- Authorization Framework 
- RFC 6749 - OAuth 2.0 Authorization Framework (official IETF stnadard)
- [PDF](./rfc6749.txt.pdf)

## OpenID Connect Core - Authentication Layer on OAuth 2.0 
- OpenID Connect Core 1.0 (final spec from the OpenID Foundation)
- [PDF](./Final_%20OpenID%20Connect%20Core%201.0%20incorporating%20errata%20set%202.pdf)

## SCIM - User Provisioning Protocol 
- RFC 7644 - System for Cross-domain Identity Management (SCIM) Protocol 
- [PDF-1 RFC 7644](rfc7644.txt.pdf)
- [PDF-2 SCIM Core Schema RFC 7643](./rfc7643.txt.pdf)

## NIST RBAC Model - Access Control Standard 
- NIST Role-Based Access Control (RBAC) model overview & standard description 
- [PDF RBAC](./rbac-model.pdf)
- [PDF ABAC](./abac-vs-rbac.pdf)


## Google Anzibar - Large-Scale Authorization System 
- Google Zanzibar research paper (detailed system outline)
- [PDF](./The%20Google%20Zanzibar%20Paper%2C%20annotated%20by%20AuthZed.pdf)

## AWS IAM Policy Model - AWS Authorization Reference 
AWS doesn't hava a single formal RFC, but the offiical AWS documentation describes their policy syntax and model: 
- AWS IAM user guide (policy reference) -- see the AWS site's IAM docs under Policies and JSON policy elements 
- [Link](https://docs.aws.amazon.com/iam/)

## Notes on what these cover 
- OAuth 2.0 (RFC 6749) defines access delegation and scopes - authorization delegation (not authentication).
- OpenID Connect Core 1.0 builds an authentication layer on OAuth 2.0, introducing ID Tokens and standarized identity semantics. 
- SCIM (RFC 7644) standarizes user and group provisioning across domains. 
- NIST RBAC gives a format, consensus model for role-based access control.
- Google Zanzibar describes a highly scalable global authorization system used internally at Google, influencing many modern authorization platforms. (AuthZed) 
- AWS IAM policy model is AWS's production-grade JSON policy language and evaluation logic used for service access control. 


---

# Trust & Key Discovery (related but not RFC)
When identity system publish signing keys for JWT verification, they often use: 

## JWT Set URL (typical OpenID Connect discovery)
- Identity provider exposes: https://example.com/.well-known/jwks.json

This is not a separate RFC but part of **OpenID Connect Discovery**. 

OpenID Connect Discovery spec: https://openid.net/specs/openid-connect-discovery-1_0.html


## Recommended reading path 
Start here in order 
### [OpenID Connect Core (conceptual identity + tokens)](https://openid.net/specs/openid-connect-discovery-1_0.html)

### [JWT (RFC 7519)](https://www.rfc-editor.org/rfc/rfc7519) Token Format 

### [JWS (RFC 7515)](https://www.rfc-editor.org/rfc/rfc7515) Signature of JWT 

### [JWK + JWA (RFC 7517, RFC 7518)]
- [JWK](https://www.rfc-editor.org/rfc/rfc7517) key format
- [JWA](https://www.rfc-editor.org/rfc/rfc7518) algorithm 


### [OIDC Discovery (for published JWKS)](https://openid.net/specs/openid-connect-discovery-1_0.html)

# Reference Protocols 

## OAuth 2.0 -- Authorization Framework 

## OpenID Connect Core - Authentication Layer on OAuth 2.0 

## SCIM - User Provisioning Protocol 


## NIST RBAC Model - Access Control Standard 

## Google Anzibar - Large-Scale Authorization System 

## AWS IAM Policy Model - AWS Authorization Reference 
AWS doesn't hava a single formal RFC, but the offiical AWS documentation describes their policy syntax and model: 
- AWS IAM user guide (policy reference) -- see the AWS site's IAM docs under Policies and JSON policy elements 


## Notes on what these cover 
- OAuth 2.0 (RFC 6749) defines access delegation and scopes - authorization delegation (not authentication).
- OpenID Connect Core 1.0 builds an authentication layer on OAuth 2.0, introducing ID Tokens and standarized identity semantics. 
- SCIM (RFC 7644) standarizes user and group provisioning across domains. 
- NIST RBAC gives a format, consensus model for role-based access control.
- Google Zanzibar describes a highly scalable global authorization system used internally at Google, influencing many modern authorization platforms. (AuthZed) 
- AWS IAM policy model is AWS's production-grade JSON policy language and evaluation logic used for service access control. 


# ZITADEL Product Overview

## Project Purpose
ZITADEL is an open-source identity infrastructure platform that provides comprehensive authentication and authorization services. It serves as a modern alternative to solutions like Auth0 (cloud-based) and Keycloak (open-source), offering the best of both worlds - quick setup with enterprise-grade features.

## Core Value Proposition
- **Multi-tenant architecture** designed for B2B scenarios with self-service capabilities
- **API-first approach** with comprehensive REST and gRPC APIs
- **Event sourcing** foundation providing strong audit trails and data consistency
- **Zero-downtime updates** and high scalability for production environments
- **OpenID Connect certified** with full SAML 2.0 support

## Key Features & Capabilities

### Authentication Methods
- **Single Sign-On (SSO)** across applications and organizations
- **Passkeys/FIDO2/WebAuthN** for passwordless authentication
- **Multi-factor authentication** (OTP, U2F, Email OTP, SMS OTP)
- **Username/Password** with customizable complexity policies
- **External identity providers** and social logins
- **LDAP integration** for enterprise directories
- **Device authorization** for IoT and limited-input devices
- **Machine-to-machine** authentication (JWT profile, PAT, Client Credentials)

### Multi-Tenancy & Organization Management
- **Identity brokering** with templates for popular providers
- **Customizable onboarding** workflows for B2B customers
- **Domain discovery** for automatic organization routing
- **Delegated role management** to third-parties
- **Team management** within organizations
- **Branding customization** per organization

### Integration & APIs
- **GRPC and REST APIs** for all functionality
- **Actions system** for custom workflows and token customization
- **SCIM 2.0 Server** for user provisioning
- **Role-Based Access Control (RBAC)**
- **Audit logging** and SOC/SIEM integration
- **Webhooks and custom code execution**

### Self-Service Capabilities
- **User self-registration** with verification
- **Password reset and profile management**
- **Organization administration** through Console UI
- **Business customer self-service**

### Protocol Support
- **OpenID Connect** (certified implementation)
- **OAuth 2.x** with all standard flows
- **SAML 2.0** for enterprise SSO
- **Token exchange and impersonation**
- **Custom sessions** beyond standard protocols

## Target Users & Use Cases

### Primary Use Cases
1. **B2B SaaS Applications** - Multi-tenant authentication with customer self-service
2. **Customer Identity (CIAM)** - Consumer-facing applications with social login
3. **Enterprise SSO** - Internal applications with LDAP/AD integration
4. **API Security** - Machine-to-machine authentication for microservices
5. **Identity Brokering** - Connecting multiple identity providers

### Target Audiences
- **SaaS Developers** building multi-tenant applications
- **Enterprise IT Teams** modernizing authentication infrastructure
- **DevOps Engineers** seeking scalable identity solutions
- **Security Teams** requiring comprehensive audit trails
- **Product Teams** needing customizable user experiences

## Deployment Options
- **ZITADEL Cloud** - Managed SaaS with global regions (US, EU, Australia, Switzerland)
- **Self-hosted** - Docker, Kubernetes, Linux, macOS deployments
- **Hybrid** - Professional support available for self-hosted instances

## Technology Foundation
- **Go backend** with PostgreSQL database (version 14+)
- **Angular frontend** for administration console
- **Next.js** for login UI and documentation
- **Event sourcing** architecture for data consistency
- **Cloud-native** design with container support
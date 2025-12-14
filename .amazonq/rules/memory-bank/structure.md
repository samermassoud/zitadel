# ZITADEL Project Structure

## Repository Organization
This is a monorepo using **Nx** for build orchestration and **pnpm** for package management, containing multiple applications and shared libraries.

## Top-Level Directory Structure

### Core Applications (`/apps/`)
- **`api/`** - Main ZITADEL backend service (Go)
  - Contains Docker configuration and environment files
  - Production and test configurations
  - Entry point for the ZITADEL server
- **`login/`** - Login UI application (Next.js/React)
  - User-facing authentication interface
  - Customizable themes and branding
  - Multi-language support

### Backend Services (`/backend/`)
- **`v3/`** - Next-generation backend architecture
  - API layer with modern patterns
  - Domain-driven design structure
  - Storage abstractions
  - Telemetry integration
- **`main.go`** - Backend entry point

### Command Line Tools (`/cmd/`)
- **`admin/`** - Administrative utilities
- **`encryption/`** - Key management tools
- **`initialise/`** - Database and system initialization
- **`setup/`** - Migration and setup scripts (66+ migration steps)
- **`start/`** - Application startup logic
- **`mirror/`** - Event mirroring utilities

### Frontend Applications
- **`console/`** - Administrative web interface (Angular)
  - Organization and user management
  - Application configuration
  - Policy and security settings
- **`docs/`** - Documentation site (Docusaurus)
  - API documentation
  - Integration guides
  - Self-hosting instructions

### Core Internal Libraries (`/internal/`)

#### API Layer (`/internal/api/`)
- **`grpc/`** - gRPC service implementations
- **`http/`** - HTTP/REST endpoints
- **`oidc/`** - OpenID Connect implementation
- **`saml/`** - SAML 2.0 provider
- **`scim/`** - SCIM 2.0 server
- **`ui/`** - UI serving logic

#### Business Logic (`/internal/`)
- **`command/`** - Write operations and business commands
- **`query/`** - Read operations and projections
- **`domain/`** - Core business entities and rules
- **`authz/`** - Authorization logic
- **`notification/`** - Email/SMS notification system

#### Infrastructure (`/internal/`)
- **`eventstore/`** - Event sourcing implementation
- **`database/`** - Database abstractions (PostgreSQL/CockroachDB)
- **`crypto/`** - Cryptographic operations
- **`cache/`** - Caching layer (Redis)
- **`static/`** - Static file serving
- **`telemetry/`** - Observability (metrics, tracing, logging)

### Protocol Definitions (`/proto/`)
- **`zitadel/`** - Protocol Buffer definitions
  - gRPC service definitions
  - API contracts
  - Cross-language compatibility

### Package Ecosystem (`/packages/`)
- **`zitadel-client/`** - TypeScript/JavaScript SDK
- **`zitadel-proto/`** - Generated protocol definitions

### Generated Code (`/pkg/`)
- **`grpc/`** - Generated gRPC client/server code
- **`actions/`** - Action system utilities

### Testing & Quality (`/tests/`)
- **`functional-ui/`** - End-to-end UI tests (Cypress)
- Integration test configurations
- Benchmark utilities (`/benchmark/`)

## Architectural Patterns

### Event Sourcing Architecture
- **Event Store** - Central event log for all state changes
- **Projections** - Read models derived from events
- **Commands** - Write operations that generate events
- **Queries** - Read operations against projections

### Multi-Tenancy Design
- **Instance-level** isolation for complete separation
- **Organization-level** grouping within instances
- **Project-level** application scoping
- **Resource-level** fine-grained access control

### API-First Approach
- **gRPC** - Primary internal communication
- **REST** - HTTP API gateway layer
- **Protocol Buffers** - Schema-first API design
- **OpenAPI** - REST API documentation

### Microservice-Ready
- **Domain boundaries** clearly defined
- **Database per service** pattern support
- **Event-driven** inter-service communication
- **Observability** built-in for distributed systems

## Configuration Management
- **YAML-based** configuration files
- **Environment-specific** overrides
- **Feature flags** for gradual rollouts
- **Runtime configuration** updates

## Build System
- **Nx workspace** for monorepo management
- **Go modules** for backend dependencies
- **pnpm workspaces** for frontend packages
- **Docker** containerization
- **Buf** for Protocol Buffer management

## Development Workflow
- **GitHub Actions** for CI/CD
- **Semantic versioning** with automated releases
- **Code generation** from Protocol Buffers
- **Database migrations** with version control
- **Multi-environment** testing (unit, integration, e2e)
# ZITADEL Technology Stack

## Programming Languages & Versions

### Backend
- **Go 1.24.0** (toolchain 1.24.7) - Primary backend language
- **Protocol Buffers** - API schema definition
- **SQL** - Database migrations and queries

### Frontend
- **TypeScript** - Primary frontend language
- **JavaScript** - Legacy and utility scripts
- **Angular** - Console administration interface
- **Next.js/React** - Login UI and documentation
- **SCSS/CSS** - Styling and themes

## Core Dependencies & Frameworks

### Backend (Go)
- **gRPC & Connect** - API communication (`connectrpc.com/connect`)
- **PostgreSQL Driver** - Database access (`github.com/jackc/pgx/v5`)
- **Event Store** - Custom event sourcing implementation
- **Cryptography** - JWT, WebAuthn, encryption (`github.com/go-jose/go-jose/v4`)
- **Authentication** - OIDC, SAML, WebAuthn libraries
- **Observability** - OpenTelemetry, Prometheus metrics
- **Queue System** - River for background jobs (`github.com/riverqueue/river`)

### Frontend (Node.js)
- **Package Manager** - pnpm 10.13.1
- **Build System** - Nx 21.6.1 monorepo tooling
- **Angular** - Console UI framework
- **Next.js** - Login UI and documentation
- **Tailwind CSS** - Utility-first styling
- **Cypress** - End-to-end testing

## Database & Storage

### Primary Database
- **PostgreSQL 14+** - Main data store with event sourcing
- **CockroachDB** - Alternative distributed database support
- **Database Migrations** - Versioned schema management (66+ migrations)

### Caching & Queuing
- **Redis** - Session and data caching (`github.com/redis/go-redis/v9`)
- **River Queue** - Background job processing
- **In-memory caching** - Application-level caching

### File Storage
- **Local filesystem** - Default static file storage
- **S3-compatible** - Cloud storage support (`github.com/minio/minio-go/v7`)
- **Google Cloud Storage** - GCP integration

## Development Tools & Build System

### Monorepo Management
- **Nx** - Build orchestration and caching
- **pnpm workspaces** - Package management
- **Changesets** - Version management and changelogs

### Code Generation
- **Protocol Buffers** - API schema and code generation
- **Buf** - Protobuf toolchain and linting
- **Go generate** - Code generation directives
- **Statik** - Static file embedding

### Testing Framework
- **Go testing** - Unit and integration tests
- **Testify** - Go testing utilities (`github.com/stretchr/testify`)
- **Cypress** - E2E testing for UI
- **Vitest** - Frontend unit testing
- **Docker Compose** - Integration test environments

## Security & Cryptography

### Authentication Protocols
- **OpenID Connect** - Certified implementation
- **OAuth 2.x** - All standard flows
- **SAML 2.0** - Enterprise SSO
- **WebAuthn/FIDO2** - Passwordless authentication

### Cryptographic Libraries
- **Go-JOSE** - JWT and JWE handling
- **WebAuthn** - FIDO2 implementation (`github.com/go-webauthn/webauthn`)
- **Passwap** - Password hashing (`github.com/zitadel/passwap`)
- **TLS/mTLS** - Transport security

## Observability & Monitoring

### Metrics & Tracing
- **OpenTelemetry** - Distributed tracing and metrics
- **Prometheus** - Metrics collection and alerting
- **Google Cloud Profiler** - Performance profiling
- **Structured logging** - JSON-based logging with Logrus

### Health Checks
- **gRPC health checks** - Service health monitoring
- **HTTP health endpoints** - Load balancer integration
- **Database connectivity** - Connection pool monitoring

## Development Commands

### Backend Development
```bash
# Run ZITADEL server
go run cmd/zitadel/main.go start

# Database setup
go run cmd/zitadel/main.go init --config ./cmd/defaults.yaml

# Run tests
go test ./...

# Generate code
go generate ./...
```

### Frontend Development
```bash
# Install dependencies
pnpm install

# Build all projects
pnpm nx run-many --target=build

# Run console in development
pnpm nx serve console

# Run login UI in development
pnpm nx serve login

# Run tests
pnpm nx test
```

### Database Management
```bash
# Run migrations
go run cmd/zitadel/main.go setup --config ./cmd/defaults.yaml

# Initialize database
go run cmd/zitadel/main.go init --config ./cmd/defaults.yaml
```

### Docker Development
```bash
# Build Docker image
docker build -t zitadel .

# Run with Docker Compose
docker-compose up -d

# Development container
docker-compose -f .devcontainer/docker-compose.yaml up
```

## Configuration Management

### Configuration Files
- **YAML** - Primary configuration format
- **Environment variables** - Runtime overrides
- **Feature flags** - Gradual feature rollouts
- **Multi-environment** - Development, staging, production configs

### Key Configuration Areas
- **Database connections** - PostgreSQL/CockroachDB settings
- **Cryptographic keys** - JWT signing, encryption keys
- **External integrations** - SMTP, SMS, storage providers
- **Security policies** - Password, session, rate limiting
- **Observability** - Metrics, tracing, logging configuration

## Deployment Technologies

### Containerization
- **Docker** - Application containerization
- **Multi-stage builds** - Optimized container images
- **Health checks** - Container health monitoring

### Orchestration
- **Kubernetes** - Container orchestration
- **Helm charts** - Kubernetes deployment templates
- **Docker Compose** - Local development environments

### Cloud Platforms
- **Google Cloud Platform** - Primary cloud provider
- **AWS** - Alternative cloud deployment
- **Self-hosted** - On-premises deployment options
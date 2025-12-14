# ZITADEL Development Guidelines

## Code Quality Standards

### Go Code Formatting & Structure
- **Package naming**: Use lowercase, single-word package names that reflect the domain (e.g., `admin`, `oidc`, `command`)
- **File naming**: Use snake_case for file names with descriptive suffixes (`_converter.go`, `_model.go`, `_test.go`)
- **Import organization**: Group imports in standard order (standard library, third-party, internal)
- **Function naming**: Use descriptive names with domain context (`FailedEventToPb`, `AuthMethodTypesToAMR`)
- **Struct embedding**: Leverage Go's embedding for composition (e.g., `*command.CurrentAuthRequest`)

### TypeScript/JavaScript Standards
- **Import organization**: Use explicit imports with proper grouping (Angular, third-party, internal)
- **Function naming**: Use camelCase with descriptive names (`CheckRegisterPwPolicy`)
- **Variable naming**: Use descriptive names with context (`pwNewConfirmationValue`)
- **Export patterns**: Use named exports for utilities, default exports for components

### Naming Conventions
- **Constants**: Use UPPER_SNAKE_CASE for constants and enum-like values
- **Variables**: Use camelCase in TypeScript/JavaScript, camelCase in Go
- **Functions**: Use PascalCase for public Go functions, camelCase for TypeScript/JavaScript
- **Types/Interfaces**: Use PascalCase with descriptive suffixes (`AuthRequestV2`, `RefreshTokenRequestV2`)

## Architectural Patterns

### Domain-Driven Design (DDD)
- **Aggregate boundaries**: Clear separation between domains (auth, admin, user, org)
- **Command/Query separation**: Separate write operations (`command` package) from read operations (`query` package)
- **Domain models**: Rich domain objects with behavior, not just data containers
- **Repository pattern**: Abstract data access behind interfaces

### Event Sourcing Implementation
- **Event-first design**: All state changes captured as events
- **Projection patterns**: Read models built from event streams
- **Command handlers**: Business logic that produces events
- **Eventual consistency**: Accept and design for eventual consistency

### API Design Patterns
- **Protocol-first**: Define APIs using Protocol Buffers
- **Converter pattern**: Separate internal models from API models (`FailedEventToPb`, `AuthRequestV2`)
- **Versioning**: Support multiple API versions (v1, v2, v3alpha)
- **Interface segregation**: Small, focused interfaces for different use cases

### Frontend Architecture
- **Component composition**: Use Angular's component architecture with clear boundaries
- **Animation patterns**: Consistent animation triggers and transitions
- **Provider pattern**: Use React/Angular providers for cross-cutting concerns
- **State management**: Clear separation of local and global state

## Common Implementation Patterns

### Error Handling
- **Structured errors**: Use domain-specific error types with context
- **Error propagation**: Proper error wrapping and context preservation
- **Graceful degradation**: Handle failures without breaking user experience
- **Logging**: Structured logging with appropriate levels and context

### Authentication & Authorization
- **Interface-based design**: Common interfaces for different auth methods
- **Token handling**: Consistent patterns for JWT, refresh tokens, and sessions
- **Multi-factor support**: Extensible patterns for various auth factors
- **Session management**: Clear session lifecycle and state management

### Data Conversion Patterns
```go
// Standard converter pattern
func EntityToPb(entity *domain.Entity) *pb.Entity {
    return &pb.Entity{
        Id:    entity.ID,
        Name:  entity.Name,
        // ... other fields
    }
}

// Batch conversion pattern
func EntitiesToPb(entities []*domain.Entity) []*pb.Entity {
    result := make([]*pb.Entity, len(entities))
    for i, entity := range entities {
        result[i] = EntityToPb(entity)
    }
    return result
}
```

### Time Handling
- **Consistent time types**: Use `time.Time` for Go, proper timestamp conversion for protobuf
- **Zero value checks**: Always check for zero time values before conversion
- **UTC normalization**: Store and process times in UTC, convert for display

### Validation Patterns
- **Input validation**: Validate at API boundaries before processing
- **Business rule validation**: Separate validation logic in domain layer
- **Client-side validation**: Immediate feedback with server-side verification
- **Error messaging**: User-friendly error messages with technical details in logs

## Testing Standards

### Unit Testing
- **Test file naming**: Use `_test.go` suffix for Go tests
- **Test function naming**: Descriptive test names that explain the scenario
- **Table-driven tests**: Use table-driven tests for multiple scenarios
- **Mock usage**: Use interfaces and mocks for external dependencies

### Integration Testing
- **Database testing**: Use test databases with proper cleanup
- **API testing**: Test complete request/response cycles
- **Event testing**: Verify event production and consumption
- **Multi-service testing**: Test service interactions

### Frontend Testing
- **Component testing**: Test Angular components in isolation
- **E2E testing**: Use Cypress for user journey testing
- **Animation testing**: Verify animation states and transitions
- **Accessibility testing**: Ensure WCAG compliance

## Security Guidelines

### Authentication Implementation
- **Secure defaults**: Use secure defaults for all authentication mechanisms
- **Token security**: Proper token generation, validation, and expiration
- **Session security**: Secure session management with proper cleanup
- **Multi-factor enforcement**: Support and encourage MFA usage

### Authorization Patterns
- **Principle of least privilege**: Grant minimal necessary permissions
- **Role-based access**: Clear role definitions and inheritance
- **Resource-level permissions**: Fine-grained access control
- **Audit trails**: Log all authorization decisions

### Cryptographic Standards
- **Key management**: Secure key generation, storage, and rotation
- **Encryption at rest**: Encrypt sensitive data in storage
- **Encryption in transit**: Use TLS for all communications
- **Hashing**: Use appropriate hashing algorithms for passwords and tokens

## Performance Guidelines

### Database Optimization
- **Query optimization**: Use efficient queries with proper indexing
- **Connection pooling**: Manage database connections efficiently
- **Batch operations**: Use batch operations for bulk data processing
- **Caching strategies**: Implement appropriate caching layers

### API Performance
- **Response pagination**: Implement pagination for large result sets
- **Lazy loading**: Load data on demand where appropriate
- **Compression**: Use response compression for large payloads
- **Rate limiting**: Implement rate limiting to prevent abuse

### Frontend Performance
- **Lazy loading**: Load components and modules on demand
- **Animation optimization**: Use efficient animations with proper timing
- **Bundle optimization**: Minimize bundle sizes with tree shaking
- **Caching**: Implement appropriate client-side caching

## Documentation Standards

### Code Documentation
- **Function documentation**: Document public functions with clear descriptions
- **Package documentation**: Provide package-level documentation
- **API documentation**: Generate API docs from Protocol Buffer definitions
- **Architecture documentation**: Maintain up-to-date architecture diagrams

### Comment Guidelines
- **Explain why, not what**: Focus on business logic and decisions
- **TODO comments**: Use structured TODO comments with context
- **Deprecation notices**: Clear deprecation warnings with migration paths
- **Complex logic**: Document complex algorithms and business rules

## Deployment & Operations

### Configuration Management
- **Environment-specific configs**: Separate configs for different environments
- **Secret management**: Secure handling of secrets and credentials
- **Feature flags**: Use feature flags for gradual rollouts
- **Configuration validation**: Validate configuration at startup

### Monitoring & Observability
- **Structured logging**: Use structured logging with consistent fields
- **Metrics collection**: Implement comprehensive metrics collection
- **Distributed tracing**: Use tracing for request flow analysis
- **Health checks**: Implement proper health check endpoints

### Database Management
- **Migration scripts**: Version-controlled database migrations
- **Backup strategies**: Regular backups with tested restore procedures
- **Performance monitoring**: Monitor database performance and optimize queries
- **Schema evolution**: Plan for schema changes and backward compatibility
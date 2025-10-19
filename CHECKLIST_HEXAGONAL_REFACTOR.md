# Hexagonal Refactor Checklist — Authentication Flow Orchestrator

Before closing a pull request, ensure all items are checked:

## Handlers

- [ ] Handler classes are lightweight and only delegate to ports  
- [ ] HTTP paths and methods match OpenAPI documentation  
- [ ] Logging contextual information (userId, correlationId) is included

## Application Layer / Ports

- [ ] Ports are defined as interfaces for all use cases  
- [ ] Business logic resides only in application services  
- [ ] Handlers do not directly call adapters  

## Adapters / Infrastructure

- [ ] GraphAPI adapter uses client credentials and WebClient  
- [ ] SMTP adapter sends OTP via TLS, no business logic  
- [ ] Core API adapter maps external responses to domain DTOs  
- [ ] Retry / Circuit breaker policies applied with Resilience4j  

## Domain & DTOs

- [ ] DTOs separate from external payloads  
- [ ] Validations present (`@NotNull`, `@Email`, etc.)  
- [ ] Entities encapsulate business invariants  

## OpenAPI

- [ ] All public handlers annotated with `@Operation` and `@ApiResponse`  
- [ ] Schemas accurately represent request/response DTOs  

## Logging & Error Handling

- [ ] SLF4J structured logging applied in all layers  
- [ ] Global exception handler converts domain exceptions to structured HTTP responses  
- [ ] No generic catch-all exception handling  

## Testing

- [ ] Unit tests for service layer using Mockito BDD  
- [ ] Integration tests for adapters with WireMock  
- [ ] Coverage ≥ 90%  

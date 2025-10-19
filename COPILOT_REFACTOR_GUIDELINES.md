# GitHub Copilot Refactor Rules – Authentication Flow Orchestrator (Azure Functions Edition)

## 🎯 Objective

Refactor legacy Azure Functions code into a **hexagonal architecture** for authentication and identity flows using **Spring Cloud Function**:

- Login (with and without MFA)
- OTP handling via SMTP
- Password reset and change
- Pre-registration and registration
- Integration with Azure AD B2C via Microsoft Graph (Client Secret)
- Integration with internal User Core API

All code must follow **clean code principles, SOLID, Hexagonal Architecture, and OpenAPI documentation**.

---

## 🧱 Architecture Rules (Mandatory)

| Layer / Responsibility       | Description | Package Convention |
|-------------------------------|------------|------------------|
| **Entry Points (Handlers)** | Azure Functions HTTP Handlers | `function/` |
| **Application Layer (Ports & Use Cases)** | Orchestrators, business logic interfaces | `application/port/`, `application/service/` |
| **Domain Models & DTOs** | Entities, Commands, Events, Request/Response DTOs | `domain/model/` |
| **Driven Adapters (Secondary)** | External Integrations:<br>- GraphAPI<br>- Core API<br>- SMTP Service | `infrastructure/graph/`, `infrastructure/core/`, `infrastructure/smtp/` |
| **Configuration / Factories** | Beans, WebClient factories, secret injection | `config/` |
| **Utilities / Mappers** | Stateless helpers only | `util/` |

---

## ✅ Coding Standards

- Strict **Hexagonal Architecture**: no business logic in handlers or adapters.  
- Use **interfaces for ports**; adapters implement these interfaces.  
- Handlers **call only ports**.  
- **OpenAPI documentation mandatory** on all HTTP-exposed handlers.  
- No static business logic; only pure utility functions allowed.  
- **Logging** via SLF4J with contextual keys.  
- **Error handling** via custom exceptions.

---

## ✅ Testing Rules

- Unit tests using **JUnit 5 + Mockito** (BDD style: Given / When / Then)  
- Service layer tested independently by mocking adapters  
- Adapter tests use **WireMock** for HTTP-based clients  
- Test coverage **≥ 90%**

---

## ❌ Forbidden Practices

- Static methods containing business logic  
- Mixing external API payloads directly with domain DTOs  
- Business logic inside handlers  
- Catch-all Exception handling

---

## ✅ Documentation Rules

- Every public handler must include OpenAPI annotations: `@Operation`, `@ApiResponse`, schemas  
- JavaDoc mandatory for all domain services and ports  
- Package-level README recommended for complex flows

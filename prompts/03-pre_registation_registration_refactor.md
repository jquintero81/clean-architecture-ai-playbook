You are a senior architect.

Refactor the **Pre-Registration and Registration Flows** in Azure AD B2C custom policies. Functions involved:

- PreRegisterUser
- RegisterUser
- SendOtpByEmail
- ActivateMfa
- UpdateUserProperties

**Task:** Refactor the entire flow into a **hexagonal architecture** using **Spring Cloud Function** and the rules in `COPILOT_REFACTOR_GUIDELINES.md`.

Requirements:
- Each function becomes a Spring Cloud Function handler.
- Business logic goes into application services / ports.
- External calls (Graph API, SMTP, Core API) moved to adapters.
- OpenAPI documentation for all HTTP-exposed handlers.
- Logging, correlation ID, and global exception handling included.
- Generate DTOs for all request/responses.
- Identify shared logic and interfaces for ports.

Output:
- Table mapping functions → Handler / Port / Adapter / DTO
- Suggested orchestrator services
- Adapters and responsibilities
- Call sequence of the registration flow

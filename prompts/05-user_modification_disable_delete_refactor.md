You are a senior architect.

Refactor **User Management Flows** for modification, disable, and delete users. Functions involved:

- UpdateUserProperties
- DisableUser
- DeleteUser
- GetUserDataFromCore
- SendOtpByEmail (if needed for verification)

**Task:** Refactor the entire flow into a **hexagonal architecture** using **Spring Cloud Function** and the rules in `COPILOT_REFACTOR_GUIDELINES.md`.

Requirements:
- Each function becomes a Spring Cloud Function handler.
- Business logic moved to application services / ports.
- Graph API, SMTP, Core API calls moved to adapters.
- OpenAPI documentation for all handlers.
- Logging, correlation ID, exception handling applied.
- DTOs for all payloads.
- Identify shared logic and define interfaces for ports.

Output:
- Table mapping functions → Handler / Port / Adapter / DTO
- Suggested orchestrators
- Adapters and responsibilities
- Flow sequence diagram / description

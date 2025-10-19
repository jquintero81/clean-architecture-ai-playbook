You are a senior software architect.
Refactor the **Login Flow** in Azure AD B2C custom policies. Functions involved:

- ActivateMfa
- SendOtpByEmail
- ValidateOtp
- GetUserDataFromCore
- UpdateUserProperties

**Task:** Refactor the entire flow into a **hexagonal architecture** using **Spring Cloud Function** and the rules in `COPILOT_REFACTOR_GUIDELINES.md`.

### Requirements:
1. Each function becomes a **Spring Cloud Function handler** (Entry Point).
2. Business logic extracted to **application service / ports**.
3. External calls (Graph API, SMTP, Core API) moved to **adapters**.
4. OpenAPI documentation added to all HTTP-exposed handlers.
5. Logging (SLF4J), correlation ID, and global exception handling applied.
6. Generate DTOs for all request/response payloads.
7. Identify shared logic and create **interfaces for ports**.
8. Map sequence of calls in the login flow.

### Output:
- Markdown table: each legacy function → Handler / Port / Adapter / DTO
- Suggested application services (orchestrators)
- Adapters needed and their responsibilities
- Call sequence diagram or description

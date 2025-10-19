You are a senior architect.

Refactor the **Password Change and Reset Flows**. Functions involved:

- InitiatePasswordReset
- ValidateOtp
- UpdateUserPassword
- SendOtpByEmail

**Task:** Refactor the entire flow into a **hexagonal architecture** using **Spring Cloud Function** and the rules in `COPILOT_REFACTOR_GUIDELINES.md`.

Requirements:
- Handlers as Spring Cloud Functions.
- Business logic in application services / ports.
- External calls to Graph API, SMTP moved to adapters.
- OpenAPI documentation added.
- Logging, correlation ID, global exception handling applied.
- Generate all necessary DTOs.
- Create interfaces for shared logic (e.g., OTP validation, password rules).

Output:
- Table mapping functions → Handler / Port / Adapter / DTO
- Orchestrator services suggested
- Adapter responsibilities
- Flow sequence of password reset/change

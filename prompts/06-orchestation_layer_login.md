You are a senior architect.

Some functions call other functions as part of a **full login flow**. Generate an orchestration layer that:

1. Wraps the sequence of function calls into a single orchestrator service.
2. Uses **ports/interfaces** for each step (ActivateMfa, SendOtpByEmail, ValidateOtp, GetUserDataFromCore, UpdateUserProperties).
3. Remains independently testable.
4. Adds logging, correlation ID, and global exception handling.
5. Produces OpenAPI documentation for the entry HTTP endpoint of the flow.

**Task:** Refactor the entire flow into a **hexagonal architecture** using **Spring Cloud Function** and the rules in `COPILOT_REFACTOR_GUIDELINES.md`.

Output:
- Orchestrator service class skeleton
- Mapping of each handler to ports/adapters
- Call sequence diagram
- DTOs required

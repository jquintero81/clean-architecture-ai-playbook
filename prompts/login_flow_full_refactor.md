You are a senior software architect.

We have a **complete authentication flow** implemented in Azure AD B2C custom policies, currently as multiple independent Azure Functions. Example functions include:

- ActivateMfa
- SendOtpByEmail
- ValidateOtp
- GetUserDataFromCore
- UpdateUserProperties
- DisableUser
- (and other functions involved in login, MFA, OTP, password reset, registration flows)

**Task:** Refactor the entire flow into a **hexagonal architecture** using **Spring Cloud Function** and the rules in `COPILOT_REFACTOR_GUIDELINES.md`.

### Requirements:

1. Identify all **functions in the flow** and their responsibilities.
2. For each function:
   - Create a **Handler** (Spring Cloud Function)
   - Extract business logic into **Application Service / Port**
   - Move external calls to **Adapters** (Graph API, SMTP, Core API)
   - Generate **DTOs** for request and response
3. Identify **shared logic** across functions and define interfaces for **Ports**.
4. Apply **OpenAPI documentation** to all HTTP-exposed handlers.
5. Apply **structured logging** (SLF4J) with correlation ID.
6. Apply **Global Exception Handling**.
7. For functions calling other functions:
   - Suggest an **Orchestration Layer** to sequence calls
   - Keep each function independently testable
8. Include **tests skeletons** for each service and adapter using JUnit 5 + Mockito (BDD style).
9. Include a **sequence diagram or call flow description** of the entire authentication process.

### Output:

1. Markdown table: each legacy function → Handler / Port / Adapter / DTO
2. Suggested **Application Services / Orchestrators**
3. Adapters needed and their responsibilities
4. DTOs required
5. Skeleton code for:
   - Handlers
   - Ports / Application Services
   - Adapters
6. Call sequence diagram / description of flow
7. Test skeletons (unit tests for services, WireMock tests for adapters)

### Instructions:

- Paste **all legacy Azure Function classes for this flow** below this prompt.
- Copilot should generate the **full refactor plan** and **starter skeleton code** according to Hexagonal Architecture.
- The output must be **ready to copy into VS Code**.

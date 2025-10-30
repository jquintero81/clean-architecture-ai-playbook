Use the context and conventions defined in `COPILOT_CONTEXT.md`.

Explain in detail the **sign-in flow** implemented in our Azure AD B2C custom policies.

Include:
- The XML files involved (e.g., `Base.xml`, `TrustFrameworkExtensions.xml`, `SignIn.xml`, `SignInOrSignUp.xml`).
- The inheritance relationships between them.
- The sequence of **technical steps** (claims exchange, REST API calls, validation).
- A breakdown of each call to Azure Functions, including:
  - The endpoint (HTTP or HTTPS)
  - Example cURL (request/response)
  - The input and output claims mapping
- Any interaction with MFA or external identity providers.

Conclude with a **diagram-like explanation** of the flow, summarizing key steps and dependencies.

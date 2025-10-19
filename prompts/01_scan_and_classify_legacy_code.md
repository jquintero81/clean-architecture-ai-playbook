You are a senior software architect.
Analyze the following Azure Function legacy class that handles authentication flows (login, MFA, OTP, password reset).

Identify:

- Which responsibilities belong to Handlers (Entry Points)
- Which belong to Application Layer / Ports / Use Cases
- Which should be Adapters (Graph API, SMTP, Core API)
- Which DTOs need to be created for request/response

Return:

- A Markdown table mapping old methods to new layers
- Suggestions for splitting business logic from handlers
- List of candidate interfaces for ports

Additionally, consider the following aspects to enrich your analysis:

- Evaluate the current authentication flow for potential security vulnerabilities.
- Suggest improvements for scalability and maintainability of the code.
- Discuss the impact of using dependency injection in the context of this legacy class.
- Provide examples of unit tests that could be implemented for the new structure.


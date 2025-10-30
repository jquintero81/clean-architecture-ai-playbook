Use the full workspace context and the conventions defined in `COPILOT_CONTEXT.md`.

Generate a complete **OpenAPI 3.0 specification** (in YAML format, embedded in Markdown code blocks) for all **RESTful endpoints** used in our **Azure AD B2C Custom Policies** and their related **Azure Functions**.

Include all endpoints that appear in the workspace XMLs (e.g., SignIn, MFA, Password Reset, Pre-Registration, ClientsAPI data retrieval, etc.).

For each endpoint:

1. Extract its **URL**, **HTTP method**, and **function purpose** (e.g., send OTP, validate OTP, change password, get user data, etc.).
2. Define:
   - `summary` and `description`
   - `parameters` (query, path, or header)
   - `requestBody` (with JSON schema and example)
   - `responses` (status codes, JSON schema, and examples)
   - `security` section (if applicable, e.g., Managed Identity, API key, Bearer)
3. Include a **`tags`** section grouping endpoints by flow (e.g., `signin`, `mfa`, `passwordreset`, `preregistration`,).
4. If the endpoint corresponds to an Azure Function, infer its input/output from the code or comments and describe them.
5. Include **example curl commands** for each endpoint in Markdown code blocks.
6. Add a `components:` section defining common schemas (e.g., `OtpRequest`, `OtpValidation`, `UserProfile`, `PasswordChangeRequest`, `GetUserData`).

Format the output as Markdown, like this example:

```yaml
openapi: 3.0.3
info:
  title: Azure AD B2C Custom Policies - API Specification
  version: 1.0.0
  description: >
    This OpenAPI document describes all RESTful endpoints used by Azure AD B2C Custom Policies and related Azure Functions.

tags:
  - name: signin
    description: Sign-in and authentication flows
  - name: mfa
    description: Multi-Factor Authentication (OTP) endpoints
  - name: passwordreset
    description: Password reset flow
  - name: preregistration
    description: User pre-registration flow
  - name: clientsAPI
    description: Core People API integration

paths:
  /api/send-otp:
    post:
      tags: [mfa]
      summary: Send OTP via email
      description: Called by B2C during MFA setup to send an OTP through SMTP.
      requestBody:
        content:
          application/json:
            schema:
              $ref: '#/components/schemas/OtpRequest'
            example:
              email: user@example.com
      responses:
        '200':
          description: OTP sent successfully
          content:
            application/json:
              example:
                message: "OTP sent"
        '400':
          description: Invalid input
  ...

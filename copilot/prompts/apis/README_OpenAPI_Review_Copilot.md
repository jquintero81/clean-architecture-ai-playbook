# 📘 Reviewing OpenAPI Specifications with GitHub Copilot

## 🧩 Overview

This guide explains how to use **GitHub Copilot Chat** in **Visual Studio Code** to review and improve **OpenAPI specifications** written by your team.  
It provides a context file and a structured review process to help Copilot identify missing details, inconsistencies, or non-standard practices in API design.

---

## 🧠 1. Setting the Context for OpenAPI Reviews

To give Copilot the right background, create a file named:

```text
COPILOT_OPENAPI_CONTEXT.md
```

### Example content:

```markdown
# Copilot Context for OpenAPI Reviews

- This project follows the OpenAPI 3.0 or 3.1 specification.
- The goal is to maintain consistent, secure, and well-documented APIs.
- Naming conventions must follow RESTful best practices.
- Use nouns for resources, avoid verbs in paths (e.g., `/users` instead of `/getUsers`).
- Responses must include correct HTTP status codes.
- Each endpoint must have examples for requests and responses.
- All parameters and schemas should include descriptions and data types.
- Reuse components (schemas, parameters, responses) where possible.
- Follow security best practices (OAuth2, bearer tokens, etc.).
- Validate consistency between operations (GET, POST, PUT, DELETE) for the same resource.
```

Keep this file open in VS Code when working with Copilot Chat — it helps Copilot infer your review standards and architectural rules.

---

## 💬 2. Using Copilot Chat to Review OpenAPI Files

### ✅ Step-by-step process

1. Open the **OpenAPI specification** file you want to review (`api.yaml`, `openapi.json`, or similar).  
2. Open **Copilot Chat** and set the scope to **Workspace**.  
3. Ensure `COPILOT_OPENAPI_CONTEXT.md` is open in another tab.  
4. Start with a high-level review prompt (see examples below).  
5. Apply suggestions iteratively to improve clarity, structure, and compliance.

---

## 🧩 3. Example Prompts for Reviewing OpenAPI Specs

### 🔹 Full Specification Review

```markdown
Review this OpenAPI specification according to REST and OpenAPI 3.1 best practices.
Identify missing elements, inconsistencies, or unclear descriptions.
Provide suggestions to improve readability and standardization.
```

### 🔹 Schema Consistency

```markdown
Check that all schemas follow consistent naming conventions and type definitions.
Identify duplicate or inconsistent schema components.
```

### 🔹 HTTP Standards

```markdown
Verify that HTTP status codes and methods follow REST conventions.
Suggest corrections if non-standard or ambiguous codes are used.
```

### 🔹 Security Review

```markdown
Analyze this OpenAPI specification for security best practices.
Ensure endpoints are properly secured with OAuth2 or bearer tokens where required.
Check if sensitive data fields (like passwords or tokens) are properly marked.
```

### 🔹 Documentation Completeness

```markdown
Review this OpenAPI spec for completeness.
Identify missing descriptions, examples, or parameter details that could improve API usability.
```

### 🔹 Response and Error Handling

```markdown
Check that all responses include proper examples and error models.
Suggest improvements for standardizing error codes (e.g., `400`, `404`, `500`).
```

---

## 🧰 4. Example Workflow for a Pre-PR Review

1. Open the branch with the new or modified OpenAPI file.  
2. Run this prompt in Copilot Chat:  

   ```markdown
   Perform a pre-PR review of the OpenAPI specification in this branch.
   Highlight improvements for consistency, structure, and adherence to RESTful standards.
   ```

3. Address Copilot’s suggestions and regenerate documentation if necessary.  
4. Re-run Copilot to confirm that the updated spec is now compliant.

---

## 🧭 5. Example Follow-Up Prompts

| Purpose | Prompt |
|----------|---------|
| Validate resource naming | “Are all paths using plural nouns and consistent naming conventions?” |
| Ensure correct data types | “Identify any incorrect or ambiguous data types in this OpenAPI spec.” |
| Improve readability | “Rewrite schema descriptions to make them clearer and more concise.” |
| Validate examples | “Check that each operation includes at least one example request and response.” |
| Identify unused components | “List components defined in `components/schemas` that are never referenced.” |

---

## ✅ Best Practices

- Keep **`COPILOT_OPENAPI_CONTEXT.md`** open during reviews.  
- Always set **Workspace scope** to allow Copilot to access related schema or YAML files.  
- Use **follow-up prompts** to refine suggestions (e.g., focus on schema design or naming).  
- Encourage developers to maintain examples and consistent structure in every commit.  
- Combine Copilot with linting tools (e.g., **Spectral**, **Redocly CLI**) for automated checks.

---

## 💡 Pro Tip

You can combine Copilot’s reasoning with **OpenAPI linters** for a complete quality workflow:

1. Run Spectral or Redocly CLI to detect syntax and rule violations.  
2. Use Copilot Chat to review **semantic** and **design-level** aspects (clarity, reuse, standards).  
3. Apply fixes and validate again before merging.

---

**Maintainer:** *API Design & Governance Team*  
**Last Updated:** October 2025

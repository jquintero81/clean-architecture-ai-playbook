# 🤖 Using GitHub Copilot with Azure Functions (Java 21 + Spring Cloud Function)

## 🧩 Overview

This guide explains how to use **GitHub Copilot Chat** effectively with this repository of **Azure Functions written in Java 21 using Spring Cloud Function**.

It focuses on:
- How to provide Copilot with proper **context** about the project.
- How to use **targeted prompts** to analyze, explain, and improve your functions.
- How to ensure Copilot can reason about **flows**, **Azure Function interactions**, and **Custom Policies** consistently.

---

## 🧠 1. Set the Context for Copilot Chat

GitHub Copilot Chat uses *context* to understand your project.  
To get the best answers, make sure Copilot knows the project structure and conventions.

### ✅ Steps

1. **Open Visual Studio Code.**
2. **Select the “Workspace” scope** in Copilot Chat.  
    This allows Copilot to read multiple files across your project (Java, XML, YAML, etc.).
3. **Keep open** the following files in tabs:
    - `COPILOT_CONTEXT.md` → contains the master context and conventions.
    - The specific Java file(s) or Azure Function(s) you are working on.
    - Any XML files (if the Function is used by a B2C Custom Policy).

4. **Optional:** Mention the context file explicitly in your prompt:  
    ```markdown
    Use the context defined in `COPILOT_CONTEXT.md` for this explanation.
    ```

---

## 🧠 2. Example Prompts for Copilot Chat

Use these prompts directly inside Copilot Chat (with “Workspace” context enabled):

### 🔹 Understand a Function
```markdown
Explain in detail how the function `OtpValidationFunction.java` works.  
Include:
- Input and output structure.
- How it interacts with Azure AD B2C Custom Policies.
- Any external calls (SMTP, APIs, or ClientsAPI).
```

### 🔹 Generate a Sequence Explanation
```markdown
Using the workspace context, describe the complete flow that calls this function from an Azure AD B2C Custom Policy.  
Show:
1. Which XML policies are involved.
2. The HTTP call made to this function (method, headers, payload).
3. The expected response and claim transformations.
```

### 🔹 Find Security Improvements
```markdown
Analyze `PasswordChangeFunction.java` for possible security or vulnerability issues.  
Suggest improvements following OWASP Java best practices.
```

### 🔹 Summarize All Functions
```markdown
Summarize all Azure Functions in this workspace.  
For each one, include:
- Its purpose
- Trigger type
- Input/output schema
- Related B2C policy flow
```

---

## ⚙️ 3. Recommended Copilot Workflow in VS Code

- Set the chat scope to “Workspace”.

- Open the relevant files (Function classes, context file, policy XMLs).

- Start with a broad prompt like:

```markdown
Explain how this Azure Function fits into the overall B2C sign-in flow.
```

- Then narrow down your next prompt:

```markdown
Show the input/output claims exchanged in step 4.
```

- Keep the chat open to refine iteratively — Copilot will remember your conversation context within the workspace.

---

## 🧩 4. Optional: Improving Copilot Context with a Context File

Create a file named `COPILOT_CONTEXT.md` at the root of your repository.

```markdown
### Example content:

# Copilot Context for Azure Functions Project

- Java 21 project using Spring Cloud Function.
- Functions are invoked by Azure AD B2C Custom Policies through REST API calls.
- Functions include: OTP send/validation, password reset, MFA activation, and user data retrieval.
- Azure Functions are deployed in a private VNet and secured via Managed Identity.
- Use this context when generating flow explanations, OpenAPI specifications, or debugging integrations.
```

Keep this file open when chatting with Copilot — it helps the model infer architecture, dependencies, and terminology consistently.

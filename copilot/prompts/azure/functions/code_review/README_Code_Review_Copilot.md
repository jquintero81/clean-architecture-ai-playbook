# 🧹 Code Review with GitHub Copilot — Clean Code, SOLID & Hexagonal Architecture

## 🧩 Overview

This guide explains how to use **GitHub Copilot Chat** effectively in **Visual Studio Code** to perform **local code reviews** of Java projects before submitting a Pull Request.

It focuses on:
- Clean Code principles.
- SOLID principles.
- Hexagonal Architecture (Ports and Adapters).
- Test coverage and maintainability checks.
- Detecting code smells, bad patterns, or design violations.

You will use Copilot Chat as a **code reviewer** integrated with your local IDE.

---

## 🧠 1. Setting Context for Reviews

To help Copilot understand your project’s architecture and conventions, create and maintain a file named:

```text
COPILOT_REVIEW_CONTEXT.md
```

### Example content:

```markdown
# Copilot Review Context for Java Project

- Java 21 + Spring Boot + Maven project.
- Architecture: Hexagonal (Ports and Adapters).
- Each domain module follows Clean Architecture principles.
- Use SOLID principles:
  - Single Responsibility
  - Open/Closed
  - Liskov Substitution
  - Interface Segregation
  - Dependency Inversion
- Functions should be small, cohesive, and testable.
- Apply clean code naming conventions and avoid duplication.
- Favor immutability and constructor injection.
- Apply best practices for unit and integration testing.
```

Keep this file open in a VS Code tab when reviewing, so Copilot automatically includes it as part of the **workspace context**.

---

## 💬 2. Using Copilot Chat for Local Review

### ✅ Step-by-step process

1. Open the **branch** you want to review.
2. Open **Visual Studio Code** with **Copilot Chat** installed.
3. Make sure the **chat scope** is set to **Workspace**.
4. Open the files or folders you want Copilot to review.
5. Ask Copilot to analyze and summarize the code before you submit the PR.

---

## 🧩 3. Example Review Prompts

You can copy these prompts directly into Copilot Chat.

### 🔹 Full File Review

```markdown
Review this file according to Clean Code and SOLID principles.
Identify any violations or code smells and suggest improvements.
```

### 🔹 Hexagonal Architecture Review

```markdown
Analyze this code to verify compliance with Hexagonal Architecture.
Indicate:
- Whether this class belongs to the domain, application, or infrastructure layer.
- If dependencies point in the correct direction (toward the domain).
- How to decouple infrastructure concerns if any are mixed.
```

### 🔹 Pull Request Pre-Check

```markdown
Perform a pre-PR review of all changes in this branch.
Summarize:
- Violations of SOLID principles.
- Large or duplicate methods.
- Poorly named variables.
- Missing tests or untested paths.
- Any potential refactor suggestions.
```

### 🔹 Code Readability

```markdown
Check this file for readability issues and naming improvements.
Suggest how to make it more expressive and self-documenting.
```

### 🔹 Test Quality

```markdown
Review this test class for completeness and clarity.
Confirm if it follows AAA (Arrange-Act-Assert) and single responsibility per test.
```

---

## ⚙️ 4. Optional: Folder-Level Reviews

If you want to analyze multiple files at once, use:

```markdown
Review all files in `src/main/java/com/example/domain/` for:
- Cohesion and coupling levels.
- Naming consistency.
- Dependency direction (should not depend on infrastructure).
```

Or use:
```markdown
Summarize the main responsibilities and dependencies of each class in this folder.
Highlight any classes that violate clean architecture boundaries.
```

---

## 🧰 5. Review Workflow Example

1. **Before pushing your branch:**
   - Open Copilot Chat.
   - Run a “Full File Review” prompt.
   - Fix issues locally.
2. **Then run:**
   ```markdown
   Summarize the architectural consistency of all changes in this branch.
   ```
3. **After fixing**, re-run Copilot to confirm the changes align with:
   - SOLID principles
   - Hexagonal layering
   - Clean Code readability
4. Finally, commit and push your changes — your PR will already have been “AI-reviewed”.

---

## 🧭 6. Example Follow-Up Prompts

| Purpose | Prompt |
|----------|---------|
| Verify dependency direction | “Does this service depend on infrastructure or is it domain-driven?” |
| Check function size | “Identify any methods that are too long or violate single responsibility.” |
| Analyze package design | “Review if package structure matches the intended hexagonal architecture.” |
| Spot hidden complexity | “Point out places where cognitive complexity can be reduced.” |
| Review for immutability | “Identify mutable state or side effects in this class.” |

---

## ✅ Best Practices

- Always keep **`COPILOT_REVIEW_CONTEXT.md`** open.
- Use **Workspace scope** for multi-file reviews.
- Keep your prompts **precise** and **goal-oriented**.
- Use **follow-up prompts** to iterate deeper on design or naming.
- If Copilot’s review is too shallow, add context like:
  ```markdown
  Use the architectural conventions described in `COPILOT_REVIEW_CONTEXT.md`.
  ```

---

## 💡 Pro Tip

You can combine this local review with your static analysis tools (Kiuwan, Snyk, SonarQube) for a hybrid workflow:

- Run automated analysis → fix technical vulnerabilities.
- Use Copilot Chat → ensure design, clarity, and maintainability.
- Merge confidently.

---

**Maintainer:** *Code Quality & Architecture Team*  
**Last Updated:** October 2025

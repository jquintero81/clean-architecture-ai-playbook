# Clean Architecture AI Playbook — Azure AD B2C Edition

This repository is a **practical guide to migrating legacy projects** (for example, Azure Functions written without patterns, with static classes, etc.) to a **professional hexagonal architecture**, **with the help of artificial intelligence (GitHub Copilot / ChatGPT)**.

The main focus is on **projects that manage identity with Azure AD B2C**, covering:

✅ Login with and without MFA  
✅ Pre-registration and registration flows  
✅ Password change and recovery  
✅ User modification and deletion  
✅ Sending OTP via SMTP (TLS)  
✅ Integration with GraphAPI using Client Secret  
✅ Integration with the company's internal User Core  

---

## 🎯 Objective

Establish **a standard and repeatable methodology** for:

| Phase | Objective | Tool |
|------|----------|-------------|
| 1. Audit | Scan legacy code | Prompts from `01_scan_and_classify_legacy_code.md` |
| 2. Modular Transformation | Migrate to hexagonal architecture | Prompts `02_hexagonal_migration_prompts.md` |
| 3. Hardening | OpenAPI + Global Exception + Logging Decorators | Prompts `03_openapi_exception_logging_prompts.md` |
| 4. Security & Resilience | Secrets, retry, validated CI/CD | Prompts `04_security_resilience_prompts.md` |

---

## 📂 How to use this Playbook?

1. **Clone this repository** or mark it as a *Template* for new projects:

```bash
gh repo create my-new-function --template clean-architecture-ai-playbook
```


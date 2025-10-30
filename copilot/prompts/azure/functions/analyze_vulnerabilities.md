Use the context from `COPILOT_SECURITY_CONTEXT.md`.

Analyze all Maven dependencies in the workspace and check for potential vulnerabilities or outdated versions.

If Kiuwan or Snyk report files exist, summarize:
- Vulnerable packages
- CVE references
- Current vs. fixed versions
- Severity and remediation plan

Then, propose secure dependency updates directly in `pom.xml` (show the diff).

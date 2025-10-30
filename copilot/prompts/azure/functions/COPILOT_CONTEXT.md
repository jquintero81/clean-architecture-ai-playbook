# 🧩 GitHub Copilot Security Context

This project uses **Java 21**, **Apache Maven**, and **Spring Cloud Functions** running on Azure Functions.

Security analysis is performed in CI/CD using:
- **Kiuwan** for code-level vulnerabilities, architecture flaws, and OWASP compliance.
- **Snyk** for dependency and transitive vulnerability scanning.

The following principles must guide all Copilot suggestions:
- Use only **supported LTS versions** of libraries and frameworks.
- Prioritize **CVE-free** dependencies whenever possible.
- Avoid introducing new transitive vulnerabilities when upgrading dependencies.
- Suggest only **secure coding patterns** compliant with OWASP Top 10.
- All proposed code changes must **preserve functional equivalence** unless otherwise requested.

When a vulnerability is mentioned or a `pom.xml` dependency is analyzed, Copilot should:
1. Identify the vulnerable library or code pattern.
2. Explain the **risk and impact** (with CVE or CWE reference if available).
3. Suggest a **remediation**:
   - Upgrade version (show exact version).
   - Replace with a secure library or pattern.
   - Modify code to prevent injection or unsafe deserialization.
4. Generate a **code patch or diff** showing the fix.

When Kiuwan or Snyk report files (`kiuwan-results.json`, `snyk_report.json`) are present, Copilot should:
- Parse them for vulnerabilities.
- Prioritize remediation by severity (Critical > High > Medium > Low).
- Cross-check fixes with Maven Central for available secure versions.

All responses must include a brief summary like:

- Risk: XX (High/Critical)
- Root cause: [library/code]
- Suggested fix: [version or code snippet]
- Reference: [CVE link or CWE ID]
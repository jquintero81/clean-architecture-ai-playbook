Use `COPILOT_SECURITY_CONTEXT.md` as context.

Kiuwan detected a potential SQL injection risk in this function:
```java
public String findUser(String email) {
    return jdbcTemplate.queryForObject("SELECT * FROM users WHERE email='" + email + "'", String.class);
}
```
Refactor it securely using Spring’s prepared statements or parameterized queries.
Explain the risk (CWE-89) and show the fixed version.
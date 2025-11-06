# GitHub Copilot – Smart Unit Test & Refactor Prompt

Use the rules defined in `COPILOT_CONTEXT.md` to generate **unit tests** and **recommend refactoring when needed**.

## 🚀 You must perform the following:

### 1️⃣ Analyze testability
- Identify constructor logic, tight coupling, static calls, or `new` inside methods
- If found, **suggest refactoring before generating tests**

### 2️⃣ Apply refactoring when needed
Examples:
- Replace `new GraphAPI()` with injected Spring bean
- Extract logic into services if SRP is violated
- Replace complex conditionals with Strategy, Template pattern and other desing patterns
- Introduce interfaces when implementation is tightly coupled

### 3️⃣ Generate unit tests (post‑refactor if refactor was needed)
- Mock all injected dependencies
- Apply **BDD: Given → When → Then**
- Use **JUnit 5 + Mockito + AssertJ**
- Achieve **90%+ logical coverage**
- Include:
  - ✅ Positive scenarios
  - ❌ Negative scenarios
  - ⚠️ Edge cases
  - 💥 Error handling
- Verify interactions only when contractually required

### 4️⃣ Output structure
Your response must contain **only these sections in this order**:

1. 🔧 **Refactoring suggestions** (if applicable)
2. ✅ **Improved (refactored) class**
3. ⚙️ **Spring configuration beans** (if required)
4. 🧪 **Unit tests for refactored code**
5. 📌 **Summary of improvements applied**

## 🔍 Rules you must obey
- Do NOT test private methods
- Do NOT mock static, use DI instead
- Do NOT keep `new Class()` inside business methods
- Do NOT generate tests before proposing refactor if the code is not test‑friendly

---

### Example invocation:
> Apply COPILOT_CONTEXT.md and the above rules to generate unit tests for the class below.
> Refactor the implementation if needed before generating tests.
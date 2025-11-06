# GitHub Copilot – Unit Testing & Refactoring Context

## 🎯 Purpose
Provide GitHub Copilot with quality standards to **generate unit tests**, **suggest refactoring**, and **improve design** of Java classes using Spring, focusing on testability, SOLID, and clean architecture.

---

## 🧠 Core Principles

### 🧪 Unit Testing
- Use **JUnit 5, Mockito, AssertJ (preferred)** or JUnit Assertions.
- Follow **BDD style** (`Given`, `When`, `Then`).
- Always mock dependencies and avoid static state.
- Use `@ExtendWith(MockitoExtension.class)` and `@InjectMocks`.
- Test **public behavior**, not private methods or implementation details.
- Ensure **minimum 90% coverage** when possible (logic branches included).
- Include:
  - ✅ Positive cases
  - ❌ Negative cases
  - ⚠️ Edge cases
  - 🔐 Null safety
  - ⏱️ Timeout or async behavior (if applicable)
- Validate interactions using `verify()` when the contract requires it.
- Avoid catch‑all exception tests like `assertThrows(Exception.class)`.

---

## ♻️ Refactoring for Testability (Critical)
Copilot must suggest refactoring when the class contains anti‑patterns that complicate unit testing.

### 🚨 Anti-patterns that require refactoring:
| Anti‑pattern | Must be replaced by |
|---|---|
| `new SomeClass()` inside methods | Constructor or field injection via Spring `@Bean` |
| Static dependencies | Injectable beans or interfaces + DI |
| Hardcoded values | Configurable properties or constructor parameters |
| Multiple responsibilities in one class | Split using SRP, Services, or Strategies |
| `if/else` chains with behaviors | Strategy, Command, or Factory patterns |
| Repeated algorithm steps across methods | Template pattern |
| Direct client instantiation (`GraphAPI api = new GraphAPI()`) | `@Bean GraphApiClient` + Injection |

### ✅ Expected outcome of refactor suggestions:
- Dependencies injectable and mockable
- Smaller, single‑purpose units
- Test code becomes simpler
- Business rules extracted to domain services when possible

---

## 🧱 Design Principles (apply when reviewing code)
- ✅ SOLID
  - **S**: One reason to change
  - **O**: Extend via behavior, not modification
  - **L**: No breaking subtype contracts
  - **I**: Small specific interfaces
  - **D**: Depend on abstractions, not implementations
- ✅ Hexagonal / Ports & Adapters where appropriate
- ✅ Don't depend on infrastructure in domain logic
- ✅ Hide implementation details behind interfaces

---

## 🔍 Signals Copilot must detect and act upon
| Code smell detected | Copilot must respond with |
|---|---|
| Hard to test class | Refactoring proposal + new testable design |
| Many constructor parameters | Builder or parameter object pattern |
| Conditional complexity | Strategy or State pattern |
| Implicit dependencies | Make them explicit + injectable |
| Tight coupling | Introduce interfaces or abstraction layer |

---

## ✅ Refactored Code Requirements
If suggesting refactor, Copilot must:
1. Rewrite the **improved production class**
2. Create or modify **Spring configuration if needed**
3. Generate **updated unit tests for the refactored version**

---

## Unit Test Checklist (Copilot must validate itself)
- [ ] Uses BDD structure
- [ ] Mocks all dependencies
- [ ] No static or internal implementation testing
- [ ] 90%+ logical coverage
- [ ] Includes edge and error cases
- [ ] Uses meaningful test names
- [ ] Verifies interactions only when relevant
- [ ] Suggests refactor if constructor logic is high or contains `new`
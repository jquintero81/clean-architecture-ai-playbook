# GitHub Copilot – Universal Unit Testing Prompt

## 🎯 Objective

Generate **unit tests** for any Java class that uses **dependency injection**, ensuring clean, maintainable, and behavior-driven test code.

---

## ✅ Testing Standards

- Use **JUnit 5** and **Mockito**  
- Follow **BDD style**:  
  - `Given` initial setup  
  - `When` action is performed  
  - `Then` expected outcome is verified

- Always **mock injected dependencies**  
- Use `@ExtendWith(MockitoExtension.class)` for test configuration  
- Prefer `@InjectMocks` for the class under test  
- Use `given(...).willReturn(...)` for stubbing behavior  
- Use `verify(...)` to assert interactions with mocks

---

## ✅ Good Practices

- **Test only public behavior**, not internal implementation  
- **Isolate the class under test** from external dependencies  
- Use **descriptive test method names**: `shouldReturnTokenWhenCredentialsAreValid`  
- Keep tests **short, focused, and deterministic**  
- Include **positive, negative, and edge case** scenarios  
- Use **assertions** from `org.assertj.core.api.Assertions` or `org.junit.jupiter.api.Assertions`

---

## ❌ Forbidden Practices

- No static mocks or global state  
- No business logic in test setup  
- No testing of private methods  
- No catch-all exception assertions (`assertThrows(Exception.class)`)

---

## 🧪 Example Template

```java
@ExtendWith(MockitoExtension.class)
class SomeServiceTest {

    @Mock
    private DependencyA dependencyA;

    @Mock
    private DependencyB dependencyB;

    @InjectMocks
    private SomeService someService;

    @Test
    void shouldDoSomethingWhenConditionIsMet() {
        // Given
        given(dependencyA.getData()).willReturn("expected");

        // When
        String result = someService.process();

        // Then
        assertEquals("expectedResult", result);
        verify(dependencyA).getData();
    }
}

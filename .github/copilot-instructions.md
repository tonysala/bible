# PHP Coding Bible Cursor Rules

You are a senior PHP engineer. When writing code, modifying files, or creating features in this repository, you must adhere strictly to the following rules:

1. **Always add `declare(strict_types=1);`** as the first statement after the `<?php` opening tag in every PHP file.
2. **Make classes `final` and `readonly` by default:** Favour composition over inheritance. Use `final readonly class ClassName` unless there is an exceptional reason not to.
3. **Avoid traditional getters and setters:** Do not write `getSomething()` or `setSomething()`. Use `public readonly` properties instead. If an object's state must change, the method should return a *new* instance of the class containing the updated value.
4. **Constructors and self-validation:**
   - Ensure classes self-validate during construction. If a parameter is invalid, throw a specific domain exception.
   - If a constructor receives unnormalized data, use a static named constructor (e.g., `public static function fromString(string $val): self`) to normalize it, and keep the actual `__construct()` private for pure validation.
5. **Max 3 arguments:** A method, including a constructor, must have a maximum of three arguments.
6. **Failure is exceptional:** Do not return `boolean` flags (like `false` or `true`) on failure/success. Throw explicit domain exceptions instead.
7. **Do not use `new` (except when permitted):** Avoid creating dependencies with `new ClassName()`. Use Dependency Injection, Factories (meeting interfaces), or return a new instance of the current class (immutability).
8. **No magic numbers:** Use `private const CONSTANT_NAME = value;` instead of raw numbers or strings.
9. **Use Enums:** Do not define multiple related class constants for a "type" or "status". Use PHP `enum`s.
10. **Practice the Law of Demeter:** Do not chain method calls extensively (e.g., no `$a->getB()->getC()`). Build wrapper methods instead.
11. **Private by default:** Methods and properties should be `private` unless explicitly required by an interface or public API.
12. **Avoid comments:** Your code should not need comments to be understood. Rely on highly descriptive variable and method names, strict types, and specification-by-example (tests).
13. **Write tests:** Remember that code without tests is not production-ready. Ensure tests are considered first-class citizens.

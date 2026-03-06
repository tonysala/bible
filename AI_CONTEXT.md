# AI Context for PHP Coding Bible

This repository follows a strict "PHP Coding Bible" designed to ensure maintainable, high-quality, and robust code. AI assistants working on this codebase should adhere strictly to the following principles extracted from the project's `README.md`.

## Core Ethos

* **Don't. Ship. Shit.** Code without tests is not production-ready.
* The codebase must be Clean, PSR-12 compliant, SOLID, Testable, and Maintainable.

## Key Coding Principles

1.  **Tests are First-Class Citizens:**
    *   Tests are equally as valuable as application code.
    *   They must be fast, light, atomic, and easily maintained.
    *   Classes that are easy to test are easy to use and maintain.

2.  **Favour Composition over Inheritance:**
    *   Make classes `final` by default and use collaborators instead of inheritance.

3.  **Self-Validating Objects:**
    *   Objects must self-validate on construction to ensure they are created in a valid state.
    *   Throw specific exceptions if validation fails during construction.

4.  **Constructors Should Only Validate (Not Normalize):**
    *   Use private constructors for validation.
    *   Use Static Named Constructors (e.g., `public static function fromString(string $data): self`) to normalize data before passing it to the private constructor.

5.  **The "Rule" of Three:**
    *   Methods (including constructors) should have a **maximum of three arguments**.

6.  **Collaboration & Aggregates:**
    *   Use Aggregates and Value Objects (which self-validate) to group related data.

7.  **Practice the Law of Demeter:**
    *   A principle of least knowledge. Do not chain methods to access deeply nested properties (e.g., avoid `$customer->getProfile()->getHomeAddress()`; use `$customer->getHomeAddress()` instead).

8.  **Failure Should Be Exceptional:**
    *   Classes should do what is expected or throw a specific Exception. Do not return `true`/`false` to indicate success/failure.

9.  **Comments Are a Code Smell:**
    *   Code should be self-documenting. Use strong variable/method names and strict typing instead of comments.

10. **Set is Evil (Immutability):**
    *   Objects should be immutable. If state must change, methods like `setX` should return a *new* instance with the updated value, leaving the original unchanged.

11. **Get is Evil (Readonly Properties):**
    *   Avoid traditional getter methods. Instead, use PHP 8.1+ `public readonly` properties.
    *   Better yet, use `final readonly class` wherever possible.

12. **New is Evil:**
    *   Avoid using `new` except for:
        *   Immutability (an object returning a new instance of itself).
        *   Dedicated factories implementing an interface.
        *   Dependency Injection containers.

13. **Private by Default:**
    *   Make variables and methods `private` by default. Only expose the absolute minimum required for the public API.

14. **No Magic Numbers:**
    *   Prefer class constants over hardcoded magic numbers.

15. **Use Enums:**
    *   Prefer Enums over defining multiple class constants that represent the same type of "thing".

16. **Enforce Strict Typing:**
    *   **Every** PHP file must start with `declare(strict_types=1);`.

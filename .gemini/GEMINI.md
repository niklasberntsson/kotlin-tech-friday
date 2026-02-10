# Lindex.CustomerApp API Rules (Kotlin Ktor)

## 🏗 Architecture & Structure
All new features must follow the established Hexagonal/Clean Architecture pattern:

- **api/**: Presentation layer. Routes, DTOs, and Ktor-specific plugins.
  - Routes should be defined as extension functions on `Route` in `api/routes/`.
- **domain/**: Inner core. Pure business logic, models, and repository interfaces.
  - No dependencies on Ktor or external libraries here.
- **data/**: Infrastructure layer. Implementation of domain repositories, database logic (Exposed), and external API clients.

## 🛠 Design Principles
- **Tell, Don't Ask**: Encapsulate logic within objects rather than pulling data out to make decisions.
- **Fail Fast**: Validate inputs early (e.g., using `require()` or `check()` in Kotlin).
- **No Logic in Routes**: Routes should only handle request parsing and response mapping. Delegate logic to domain services.
- **DI Sorting**: Always match constructor arguments and maintain clean dependency injection patterns.

## 🧪 Testing
- **Convention**: Use `MethodName_Should_ExpectedBehavior`.
- **Framework**: Use `testApplication` for integration tests and standard Kotlin Test for unit tests.
- **Mocking**: Use "Minimal direct mocks" – only mock what is absolutely necessary for the test case.
- **Red-Green-Refactor**: Always create a failing test case before implementing the fix or feature.

## ✅ Implementation Workflow
1. Analyze the request and identify the affected layer (Core, Infrastructure, or UI/API).
2. Create a test case in `src/test/kotlin/`.
3. Implement the minimal code to pass the test.
4. Refactor and verify with `./gradlew test`.

# Protocol: Testing Strategy

## Purpose
To ensure code quality, reliability, and prevent regressions through comprehensive testing practices.

## Guidelines
1.  **Unit Tests:**
    *   Write unit tests for all pure functions, utility functions, and complex logic.
    *   Aim for high code coverage for critical modules.
    *   Use Vitest as the primary unit testing framework.
2.  **Component Tests:**
    *   Write tests for React components to ensure they render correctly, respond to user interactions, and display data as expected.
    *   Focus on testing component behavior rather than internal implementation details.
3.  **Integration Tests:**
    *   Test the interaction between different modules or services (e.g., API calls, data flow through hooks).
    *   Mock external dependencies (e.g., API responses) to ensure tests are fast and reliable.
4.  **End-to-End (E2E) Tests:**
    *   Implement E2E tests for critical user flows to simulate real user interactions.
    *   Use a suitable E2E testing framework (e.g., Playwright, Cypress).
5.  **Test Naming Conventions:** Follow clear and consistent naming conventions for test files and test descriptions.
6.  **Automated CI/CD Integration:** Ensure all tests run automatically as part of the Continuous Integration/Continuous Deployment (CI/CD) pipeline.

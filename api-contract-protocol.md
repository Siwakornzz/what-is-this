# Protocol: API Contract

## Purpose
To ensure accurate API integration, data consistency, and application stability.

## Guidelines
1.  **Always Consult API Documentation:** Before implementing any API-related feature, thoroughly review the relevant API documentation (e.g., `api-admin.md`).
2.  **Verify Request/Response Structures:** Pay close attention to:
    *   **Endpoint:** Use the correct URL and HTTP Method (GET, POST, PUT, DELETE).
    *   **Request:** Verify all required fields, data types, and formats.
    *   **Response:** Accurately map the `data` structure (including nested objects/arrays), field names, data types, and nullability.
    *   **Status Codes:** Understand and handle different HTTP status codes (e.g., 200, 400, 401, 403, 404, 500).
3.  **Accurate Type Definitions:** Ensure TypeScript interfaces (`.ts` files in `src/types/`) precisely reflect API response structures.
4.  **No Assumptions:** Never assume field presence, type, or format if not explicitly documented. Seek clarification if unsure.
5.  **Handle Missing/Unexpected Data:** Implement defensive coding (e.g., optional chaining `?.`, null checks) for potentially missing or malformed API data.
6.  **Documentation Sync:** Ensure API documentation is always synchronized with the backend API.
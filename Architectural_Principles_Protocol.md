# Protocol: Architectural Principles

## 1. Overview
This protocol is the **source of truth** for the application's core architecture. It contains mandatory, enforceable rules that dictate how code MUST be structured and implemented. It must be consulted before any refactoring or new feature implementation to ensure quality and consistency.

---

## 2. API Layer
The API layer is responsible for all communication with the backend.

-   **Rule 2.1: Deprecate `src/services`**: The `src/services` directory and class-based services (e.g., `authService.ts`) are **DEPRECATED**. No new files should be added here, and existing files should be refactored.

-   **Rule 2.2: Use Custom Hooks with SWR**: All data fetching from the backend that is used to display in a component **MUST** be done through a custom hook that utilizes `useSWR`.

-   **Rule 2.3: Centralize API Functions**: The actual API call logic (using `axios`) **MUST** be separated into plain functions and located in `src/api/`. Files should be grouped by domain (e.g., `src/api/authApi.ts`, `src/api/roleApi.ts`). These functions will be called by the SWR fetcher.

-   **Rule 2.4: Use Central `axiosInstance`**: All `axios` calls **MUST** use the central instance exported from `src/api/axiosInstance.ts`. This instance contains the necessary `baseURL` and `interceptors` for handling authentication tokens.

---

## 3. State Management
State management is divided into three distinct categories.

-   **Rule 3.1: Server State**: For any data that comes from the server, **MUST** use `useSWR`. This handles caching, revalidation, and server state synchronization automatically.

-   **Rule 3.2: Global UI State**: For UI state that needs to be shared across many components (e.g., modal visibility, theme), **MUST** use React Context API, placed in `src/contexts/`.

-   **Rule 3.3: Local Component State**: For state that is confined to a single component, use standard React hooks like `useState` or `useReducer`.

---

## 4. Environment Variables
To ensure consistency and prevent runtime errors from missing configurations.

-   **Rule 4.1: Centralized & Validated Config**: All environment variables (`import.meta.env`) **MUST NOT** be accessed directly in components or services. Instead, they **MUST** be imported from a single, validated configuration file located at `src/config/environment.ts`.

-   **Rule 4.2: Validation on Startup**: The `src/config/environment.ts` file **MUST** validate the existence and format of critical environment variables (e.g., `VITE_API_URL`). If a variable is missing, the application should throw an error immediately on startup to fail fast.

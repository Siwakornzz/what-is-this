# Protocol: Code Generation Checklist

## 1. Overview
This protocol defines the **mandatory, sequential checklist** for generating any new code artifact (components, hooks, pages, etc.). It must be followed to ensure every new piece of code is complete, documented, and tested according to project standards.

---

## 2. The Checklist (Must be followed in order)

### ✅ **Step 1: Create State Documentation**
-   **Rule:** Before writing any implementation code, a state documentation file **MUST** be created in the `state/` directory.
-   **Path for Pages:** `state/pages/state_{page_name}.md`
-   **Path for Components:** `state/components/state_{component_name}.md`
-   **Template:** Use `state/state_template.md`.

### ✅ **Step 2: Define Types and Validation Schemas**
-   **Rule:** All reusable or complex TypeScript types and interfaces **MUST** be defined in the `src/types/` directory.
-   **Validation:** For any data that requires validation (forms, API responses), a `zod` schema **MUST** be created alongside the type definition. The TypeScript type should be inferred from the schema to ensure they are always in sync.

### ✅ **Step 3: Implement the Artifact (Component, Hook, Page)**
-   **Rule (Components/Pages):** Must be a Functional Component using hooks.
-   **Rule (Hooks):** File and function name must start with `use`.
-   **Rule (Pages):** Page components **MUST** be lazy-loaded in the routing configuration file (`src/App.tsx` or similar) using `React.lazy()` and wrapped in `<Suspense>`.

### ✅ **Step 4: Create Tests**
-   **Rule:** A corresponding test file (`*.test.ts` or `*.test.tsx`) **MUST** be created for:
    -   All utility functions (`src/utils/`).
    -   All custom hooks (`src/hooks/`).
    -   All complex components that contain significant logic.
-   **Location:** Tests should be placed in a `__tests__` subdirectory next to the file being tested.

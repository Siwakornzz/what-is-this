# Folder Structure

The project follows a feature-based folder structure to keep the codebase organized, scalable, and easy to navigate.

## Root Directory
*   **`public/`**: Static assets that are not processed by Vite.
*   **`src/`**: The main application source code.
*   **`api-docs/`**: Markdown files documenting the backend API endpoints.
*   **`state/`**: The most critical folder, containing state documentation (`state_*.md`) for every component and page.
*   **`whatisthis/`**: Meta-documentation about the project itself.
*   **`.env`**: Environment variables for local development.
*   **`package.json`**: Project dependencies and scripts.
*   **`vite.config.ts`**: Vite configuration file.
*   **`tailwind.config.js`**: Tailwind CSS theme and configuration.
*   **`vitest.config.ts`**: Vitest testing framework configuration.

## `src` Directory Structure

```
src/
├── assets/              # Static assets like images and fonts
├── components/          # Reusable UI components
│   ├── common/          # Generic components (Button, Input, Modal)
│   ├── layout/          # Layout components (Header, Sidebar)
│   └── forms/           # Form-specific components
├── constants/           # Application-wide constants (routes, API endpoints)
├── contexts/            # React Context providers (AuthContext, ModalContext)
├── hooks/               # Custom React hooks (useAuth, useSmoothScroll)
├── pages/               # Page-level components, mapped to routes
├── services/            # DEPRECATED: API service layer (authService). See Architectural_Principles_Protocol.md
├── styles/              # Global CSS and theme files
├── test/                # Test setup and mock files
├── types/               # TypeScript type definitions and Zod schemas
└── utils/               # Utility functions (logger, formatters)
```

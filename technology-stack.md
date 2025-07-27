# Technology Stack

This project is built with a modern, high-performance technology stack organized into distinct layers, each serving a specific purpose to ensure a scalable and maintainable application.

| Layer                        | Technology / Tool                  | Purpose                                                                                                                      |
| :--------------------------- | :--------------------------------- | :--------------------------------------------------------------------------------------------------------------------------- |
| **Core Development**         | React 18                           | The core frontend library for building a reactive and component-based user interface.                                        |
|                              | TypeScript                         | Provides static type-checking to improve code quality, reduce runtime errors, and enhance developer experience.            |
|                              | Vite                               | A next-generation build tool and development server that offers extremely fast Hot Module Replacement (HMR) for rapid development. |
| **Data & State Management**  | SWR (stale-while-revalidate)       | A React Hooks library for efficient remote data fetching, caching, revalidation, and real-time data synchronization.         |
|                              | Axios                              | A promise-based HTTP client for making API calls to the backend services.                                                    |
|                              | React Context API                  | Manages global state that needs to be shared across the application, such as authentication status and modal visibility.     |
| **User Interface & Styling** | Tailwind CSS                       | A utility-first CSS framework for rapidly building custom, responsive designs directly within the markup.                      |
|                              | Framer Motion                      | An animation library for creating fluid, performant, and beautiful user interface animations and transitions.                |
|                              | Heroicons                          | A set of high-quality, consistent SVG icons used throughout the application.                                                 |
|                              | Google Fonts (Noto Sans Thai)      | Provides high-quality fonts for clear and professional Thai language display.                                                |
| **Testing & Quality**        | Vitest                             | A blazing-fast unit testing framework, deeply integrated with Vite, for verifying code logic and functionality.              |
|                              | React Testing Library              | A library for testing components in a way that resembles how users interact with them, focusing on behavior over implementation. |
| **Routing & Navigation**     | React Router                       | The standard library for handling all client-side routing, URL management, and navigation between pages within the application. |

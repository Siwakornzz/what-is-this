# Protocol: Data Transformation

## Purpose
To consistently and efficiently transform raw API data into a UI-ready format.

## Guidelines
1.  **Utilize Utility Functions:** Create and reuse centralized utility functions for data formatting (e.g., dates, times, numbers, strings) to reduce code duplication.
2.  **Transform at Appropriate Layer:** Data transformation should occur in the Hook or Service Layer before data is passed to Components. Components should receive data ready for direct display.
3.  **Maintain Consistency:** All data formatting and transformation across the application must adhere to a consistent standard.
4.  **Handle Incomplete Data:** Transformation functions must safely handle incomplete or potentially null/undefined data.

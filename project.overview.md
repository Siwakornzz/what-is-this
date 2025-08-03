# Project Overview

## Project Name
Condo Management - Admin Frontend

## Project Description
A comprehensive web application designed for condominium administrative staff and management. This platform provides the necessary tools to efficiently manage day-to-day operations, resident information, facility bookings, maintenance requests, and financial records. It serves as a centralized hub to streamline administrative tasks and enhance communication between management and residents.

The system is built with a modern tech stack (React, TypeScript, Vite, Tailwind CSS) focused on performance, scalability, and a clean user experience.

## Target Users
*   **Condo Managers / Juristic Person Officers:** Responsible for overseeing all aspects of the condominium's operations, from financial reporting to staff management.
*   **Administrative Staff:** Handle daily tasks such as managing resident data, processing payments, handling resident inquiries, and managing parcel deliveries.
*   **Facility Management Staff:** Manage the booking and maintenance of common areas and facilities like swimming pools, fitness centers, and function rooms.

## Key Features
*   **Centralized Dashboard:** Provides an at-a-glance overview of key metrics, including resident statistics, pending maintenance requests, financial summaries, and recent activities.
*   **Resident Management:** A complete system to manage resident profiles, contact information, room assignments, and status (e.g., active, pending approval).
*   **Admin & Role Management:** A granular system for Super Admins to create and manage other admin accounts and define their access levels and permissions based on roles.
*   **Billing & Financial System:** Tools to create and manage bill categories, assign bills to residents, and track payment statuses.
*   **Maintenance & Repair Tracking:** A workflow to manage maintenance requests from residents, from initial report to acknowledgment and completion.
*   **Facility & Central Resource Management:** System for managing building information, common areas (centrals), and booking history.
*   **Notification System:** Ability to create and send targeted notifications to residents or specific user groups.
*   **Parcel Management:** A tool to log incoming parcels and notify residents of their arrival.
*   **Reporting:** Generate reports on users, finances, and facility usage.

## Business Objective
To improve the operational efficiency of condominium management by digitizing and centralizing administrative tasks. The project aims to reduce manual paperwork, minimize human error, provide management with real-time data for better decision-making, and ultimately enhance the living experience for residents by providing faster and more transparent services.

## Recent Major Updates (August 2025)

### 1. Internationalization (i18n) Implementation
- **Technology**: react-i18next with modular translation architecture
- **Languages**: Thai (default), English, with extensibility for additional languages
- **Coverage**: Policy permissions, group names, service descriptions, and UI elements
- **Architecture**: Frontend-based translations for optimal performance and instant language switching
- **Structure**: Service-grouped translation files for better maintainability

### 2. API Performance Optimization
- **Role Permissions Management**: Optimized from 3+N API calls to just 2 API calls
- **New Endpoints**:
  - `GET /admin/rolePermissionsMatrix` - Single call retrieves all permission data
  - `PATCH /admin/rolePermissions` - Batch permission updates
- **Performance Impact**: ~90% reduction in network requests for role management
- **User Experience**: Faster loading times and reduced server load

### 3. Enhanced Permission Management
- **New Features**: 
  - SuperAdmin role prioritization
  - Group expand/collapse functionality
  - Inline role creation
  - Role badges with visual hierarchy
- **Technical Improvements**:
  - Fixed expand/collapse bugs
  - Resolved React key duplication warnings
  - Improved error handling and logging

# DatingApp Project Guide

This document provides context and instructions for the **DatingApp** project, a full-stack application consisting of a .NET Web API backend and an Angular frontend.

## Project Structure

The solution is divided into two main directories:

- **`API/`**: The backend Web API project built with .NET 10.0.
- **`client/`**: The frontend Single Page Application (SPA) built with Angular 21.

## Backend (API)

### Technology Stack
- **Framework:** .NET 10.0
- **Database:** SQLite (via Entity Framework Core)
- **ORM:** Entity Framework Core
- **Architecture:** Controller-based Web API

### Key Files
- `API/Program.cs`: Application entry point, service registration (DI), and middleware configuration (CORS, DB connection).
- `API/API.csproj`: Project configuration and dependencies.
- `API/Data/AppDbContext.cs`: Database context definition.
- `API/appsettings.json`: Configuration settings (Connection Strings).

### Development Commands
Run these commands from the `API/` directory:

- **Start the API:**
  ```powershell
  dotnet run
  # OR with hot reload
  dotnet watch
  ```
- **Database Migrations:**
  ```powershell
  dotnet ef migrations add <MigrationName>
  dotnet ef database update
  ```

### Configuration
- **CORS:** The API is configured to accept requests from `http://localhost:4200` and `https://localhost:4200` (the Angular client).
- **Database:** Uses a local SQLite database configured in `appsettings.json` via the `DefaultConnection` string.

---

## Frontend (Client)

### Technology Stack
- **Framework:** Angular 21
- **Styling:** Tailwind CSS 4
- **Build Tool:** Angular CLI
- **Test Runner:** Vitest

### Key Files
- `client/package.json`: Project dependencies and scripts.
- `client/angular.json`: Angular CLI configuration.
- `client/src/main.ts`: Application entry point.

### Development Commands
Run these commands from the `client/` directory:

- **Install Dependencies:**
  ```powershell
  npm install
  ```
- **Start Development Server:**
  ```powershell
  npm start
  # OR
  ng serve
  ```
  The application will be available at `http://localhost:4200/`.
- **Run Tests:**
  ```powershell
  npm test
  ```

### Conventions
- **Code Style:** Prettier is configured in `package.json` (single quotes, 100 print width).
- **Components:** Angular components are likely generated via CLI `ng g c <name>`.

---

## General Workflow

1.  Start the **API** first to ensure the backend services are running.
2.  Start the **Client** in a separate terminal to develop the UI.
3.  Ensure the SQLite database is created and updated using `dotnet ef database update` before interacting with data-dependent features.

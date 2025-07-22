# Project Overview

This repository is a **NestJS-based microservices backend** developed using the **Nx monorepo structure**. It is designed to be scalable, modular, and maintainable. Each microservice handles a specific domain and communicates via NestJS's built-in messaging system.

The backend integrates with **PostgreSQL** via **Prisma ORM**, and the database runs in a Docker container using `docker-compose`. The project uses **GitHub Actions** for continuous integration and delivery, ensuring code quality through automated linting, testing, and building on every push to the `main` branch.

**Note:** The project is already integrated with a frontend client. Therefore, do not modify existing API endpoints (routes, methods, or parameters) unless explicitly required. Any breaking change must be justified.

# Folder Structure

- `/apps`: Microservices managed by Nx (e.g., auth, user, song, gateway)
- `/libs`: Shared modules, DTOs, and utilities across services
- `/prisma`: Prisma schema files and migrations
- `/docker`: Configuration files related to Docker setup
- `/test`: Global tests (integration and e2e)
- `.github/workflows`: CI/CD pipelines using GitHub Actions

# Libraries and Frameworks

- **NestJS** (microservices architecture)
- **Nx DevTools** for monorepo management
- **Prisma ORM** for database access
- **PostgreSQL** (Dockerized)
- **Jest** for testing (unit, integration, e2e)
- **Docker Compose** for local orchestration
- **GitHub Actions** for CI/CD

# Development Environment

- Local development is done on **Windows** using **Docker Desktop**.
- The `docker-compose.yml` file spins up the required services including PostgreSQL.
- Use `nx serve <app-name>` for running services locally in development mode.

# Coding Standards

- Follow NestJS modular architecture strictly: controllers delegate logic to services.
- Place business logic in services, not in controllers.
- Use `camelCase` for variables/functions, `PascalCase` for classes.
- Prefer DTOs for request validation and Swagger documentation.
- Use `const` and `let`, never use `var`.
- Write clean, concise, and maintainable code based on SOLID principles.

# Testing Guidelines

- Write **unit tests** for all services using Jest and mocking dependencies.
- Add **integration tests** to verify service interaction and DB integration.
- Implement **end-to-end tests** (e.g., using `supertest`) for critical API flows.
- All tests are executed as part of the GitHub Actions CI pipeline.

# CI/CD via GitHub Actions

- Workflow triggers on `push` to `main` branch.
- Steps executed:
  1. Run `nx lint` across all apps and libs
  2. Run `nx test` for unit and integration tests
  3. Run `nx build` for all apps
- The pipeline must pass before changes are considered deployable.

# Additional Notes

- Database credentials and environment secrets should be managed via `.env` files or GitHub secrets.
- Prefer `.env.example` for documenting required env vars.
- Containerization is required for reproducible local development and deployment.
# Language Preference

- **Luôn phản hồi và giải thích bằng tiếng Việt.**
- Nếu có gợi ý thay đổi hoặc tạo mới code, nên giải thích ngắn gọn trước, sau đó hiển thị mã nguồn đầy đủ.
# Project Management App API

This repository contains the backend API for the Project Management App. It's built using Java, Spring Boot, and PostgreSQL, providing RESTful endpoints for managing projects, employees, and tasks.

## ✨ Features

*   User Authentication (Signup/Login)
*   CRUD operations for Projects
*   CRUD operations for Employees
*   CRUD operations for Tasks
*   Associating Employees with Projects (Members)
*   Associating Tasks with Projects

## 🛠️ Technology Stack

*   **Language:** Java 17
*   **Framework:** Spring Boot 3.4
*   **Database:** PostgreSQL 16
*   **ORM:** Spring Data JPA / Hibernate
*   **Build Tool:** Maven
*   **Containerization:** Docker & Docker Compose
*   **Other Libraries:** Lombok

## 📋 Prerequisites

Before you begin, ensure you have the following installed:

*   Java Development Kit (JDK) 17 or later
*   Apache Maven
*   Docker
*   Docker Compose

## 🚀 Setup & Installation

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/Far3000-YT/project-management-app-api.git
    cd project-management-app-api
    ```

2.  **Start the PostgreSQL Database:**
    This project uses Docker Compose to manage the PostgreSQL database container.
    ```bash
    docker-compose up -d
    ```
    This command will download the PostgreSQL 16 image (if not already present) and start a container in the background. The database `db` with user `user` and password `password` will be created automatically, as defined in `docker-compose.yml` and referenced in `src/main/resources/application.yaml`. The data will be persisted in the `postgres/` directory within the project.

3.  **Build the Application:**
    Use the Maven wrapper to build the project.
    *   On Linux/macOS:
        ```bash
        ./mvnw clean install
        ```
    *   On Windows:
        ```bash
        ./mvnw.cmd clean install
        ```
    This will compile the code and download necessary dependencies.

## ▶️ Running the API

Once the database is running and the project is built, you can start the Spring Boot application:

*   On Linux/macOS:
    ```bash
    ./mvnw spring-boot:run
    ```
*   On Windows:
    ```bash
    ./mvnw.cmd spring-boot:run
    ```

The API will start and be accessible at `http://localhost:8080`.

## 📡 API Endpoints

Here's a summary of the available endpoints:

*   **Authentication:**
    *   `POST /signup`: Create a new user account.
    *   `POST /login`: Log in an existing user.
*   **Employees:**
    *   `GET /employees`: Get all employees.
    *   `GET /employees/{id}`: Get an employee by ID.
    *   `POST /employees`: Create a new employee (expects name as plain text).
    *   `PUT /employees/{id}`: Update an employee's name (expects name as plain text).
    *   `DELETE /employees/{id}`: Delete an employee by ID.
*   **Projects:**
    *   `GET /projects`: Get all projects.
    *   `GET /projects/{id}`: Get a project by ID.
    *   `POST /projects`: Create a new project (uses request parameters: `name`, `description`, `deadline`, `priority`).
    *   `PUT /projects/{id}`: Update a project (expects JSON body with `name`, `description`, `deadline`, `priority`, `members`).
    *   `DELETE /projects/{id}`: Delete a project by ID.
*   **Tasks:**
    *   `GET /tasks`: Get all tasks.
    *   `GET /tasks/{id}`: Get a task by ID.
    *   `POST /tasks`: Create a new task (uses request parameters: `name`, `description`, `priority`, `dueDate`, `status`, `assigneeId`).
    *   `PUT /tasks/{id}`: Update a task (uses request parameters: `name`, `description`, `priority`, `dueDate`, `status`, `assigneeId`, `projectId`).
    *   `DELETE /tasks/{id}`: Delete a task by ID.

---
*This API serves as the backend for the [Project Management App (JavaFX)](https://github.com/Far3000-YT/project-management-app).*

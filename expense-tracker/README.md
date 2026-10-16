# Expense Tracker REST API

A Spring Boot REST API for recording and retrieving personal expenses. This project is being developed as a hands-on learning project for automated builds, testing, and application deployment on Oracle Cloud Infrastructure (OCI).

## 1. Technology Stack

- **Java:** 21
- **Spring Boot:** 4.1.1
- **Build Tool:** Apache Maven
- **Web Framework:** Spring MVC
- **Database:** H2
- **Persistence:** Spring Data JPA
- **Input Validation:** Jakarta Bean Validation
- **Testing:** JUnit and Spring Boot testing support
- **Version Control:** Git and GitHub

## 2. Current Features

- Create a new expense.
- Retrieve all recorded expenses.
- Validate expense input.
- Persist expense records in a file-based H2 database.
- Run the application using an embedded Tomcat server.

## 3. Expense Data Model

Each expense contains the following fields:

| Field | Type | Description |
|---|---|---|
| `id` | Long | Automatically generated expense ID |
| `amount` | BigDecimal | Expense amount; must be greater than zero |
| `category` | String | Expense category |
| `description` | String | Optional description |
| `expenseDate` | LocalDate | Date on which the expense occurred |

## 4. REST API Endpoints

Base URL: `http://localhost:8080`

### Create an Expense

**Endpoint:** `POST /api/expenses`

Content-Type: `application/json`

Request body:

```json
{
  "amount": 250.50,
  "category": "Food",
  "description": "Dinner",
  "expenseDate": "2026-10-17"
}
```

Expected response: `201 Created`

The response contains the saved expense, including its generated ID.

### Retrieve All Expenses

**Endpoint:** `GET /api/expenses`

Expected response: `200 OK`

Returns all recorded expenses as a JSON array.

## 5. Prerequisites

Install the following software:

- JDK 21
- Git
- An IDE such as IntelliJ IDEA or Eclipse (recommended)

Maven can be run through the Maven Wrapper if one is included in the project, or through a local Maven installation.

## 6. Build and Run

Clone the repository:

```bash
git clone git@github.com:krishnaprasadakella/oci-devops.git
cd oci-devops/application_code/oci-devops
```

Compile the application:

```bash
mvn clean compile
```

Run the application:

```bash
mvn spring-boot:run
```

The API will be available at:

`http://localhost:8080`

## 7. Database Configuration

The application uses a file-based H2 database.

Configured JDBC URL:

```text
jdbc:h2:file:./data/expensedb
```

Database configuration is maintained in `src/main/resources/application.properties`.

The database files are created relative to the application's working directory. They should be excluded from Git; only the application code and database configuration belong in the repository.

The H2 console is enabled for local development at:

`http://localhost:8080/h2-console`

Use the JDBC URL above and the credentials configured in `application.properties`.

**Note:** The H2 console is intended for local development and should not be exposed in a production deployment.

## 8. Project Structure

```text
oci-devops/
└── application_code/
    └── oci-devops/
        ├── pom.xml
        ├── README.md
        └── src/
            ├── main/
            │   ├── java/
            │   │   └── com/example/expense_tracker/
            │   │       ├── ExpenseTrackerApplication.java
            │   │       ├── controller/
            │   │       │   └── ExpenseController.java
            │   │       ├── entity/
            │   │       │   └── Expense.java
            │   │       ├── repository/
            │   │       │   └── ExpenseRepository.java
            │   │       └── service/
            │   │           └── ExpenseService.java
            │   └── resources/
            │       └── application.properties
            └── test/
                └── java/
```

## 9. DevOps Learning Objectives

This project will be extended incrementally to practise:

1. Version control and Git branching.
2. Automated Maven builds triggered by code changes.
3. Unit and integration testing as pipeline quality gates.
4. Packaging the application as a deployable artifact.
5. Containerizing the application using Docker.
6. Deploying the application to an OCI virtual machine.
7. Implementing application health checks and monitoring.
8. Exploring OCI DevOps build and deployment pipelines.
9. Evaluating container orchestration and deployment automation.

## 10. Planned Enhancements

- Retrieve an expense by ID.
- Update an existing expense.
- Delete an expense.
- Filter expenses by category and date.
- Generate monthly expense summaries.
- Add automated unit and integration tests.
- Configure continuous integration.
- Containerize and deploy the application on OCI.

## 11. Project Status

**Current stage:** Initial REST API and persistence implementation.

This repository is maintained as a practical learning project focused on building, testing, delivering, and operating a Java application using DevOps practices.


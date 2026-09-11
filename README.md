# Automatic Grading System for Java OOP Practical Exams

Java backend for exam administration, automated grading, grading appeals, and wallet transactions.

## Live demo

**[Open the live application](https://autograding.103-77-243-209.sslip.io/login)**

**[Hướng dẫn trải nghiệm và tài khoản cho tất cả vai trò](docs/DEMO_GUIDE.md)** — Admin, Exam Staff, Lecturer and three sample Students. Includes the exam paper, student ZIP downloads and a step-by-step walkthrough.

Use **DEMO - Recruiter Playground → Practice Grading** to run grading on the three supplied submissions and inspect the results. The original **DEMO - Trial Test 01** remains a reference dataset. Paper code: **TRIAL01**. See the walkthrough above for public role credentials and sample downloads.

| Sample submission | Score | Test cases passed |
|---|---:|---:|
| SE173222 | 7.77 / 10 | 8 / 9 |
| SE173333 | 10 / 10 | 9 / 9 |
| SE173444 | 0 / 10 | 0 / 9 |

This demonstration uses **MODE_3** with 36 rubric criteria across three questions, weighted at **2.5 / 3.75 / 3.75** points. Test-case and hardcode guards can reduce a question score to zero. These are system-generated results under this configuration.

Hosted on an **Ubuntu VPS** using **Docker Compose, Nginx, PostgreSQL, MinIO and Caddy with HTTPS**. The exam-upload, student-submission and grading workflow was verified through the API on **12 September 2026**. Email and payment integrations are not part of the verified demo. Please use the supplied sample data; this deployment is intended for trusted demonstrations.

## Project overview

The system manages exams and exam sessions, accepts student submissions, analyzes Java source structure, executes submitted JARs against test inputs, and records grading outcomes. Staff and lecturers can review appeals and monitor exam activity.

## Features

- Exam, session, submission, and user administration, including Excel student imports.
- JavaParser source analysis and configurable grading criteria.
- Student JAR execution in child Java processes with timeouts and JVM heap limits.
- Concurrent batch grading with CompletableFuture and Semaphore.
- A deterministic grading mode combining test results and structural checks.
- Role-based access, JWT authentication, and audit logging.
- Appeal assignment, review, confirmation, wallet payments, and withdrawal requests.
- Dashboard APIs for administrators, staff, and lecturers.
- Object storage and optional AI-assisted review integrations.


## Technology stack

| Area | Technologies |
|---|---|
| Runtime | Java 17, Spring Boot 3.2.3, Maven |
| API and persistence | Spring MVC, Spring Data JPA/Hibernate, PostgreSQL, Flyway |
| Security and cross-cutting concerns | Spring Security, JWT, Spring AOP |
| Grading | JavaParser, Java Reflection, Java child processes |
| Integrations | PayOS, SMTP, MinIO/S3-compatible storage, AI provider adapters |
| Documentation and testing | Springdoc OpenAPI, JUnit, Mockito, Spring Security Test |
| Packaging | Docker, Docker Compose |

## Repository structure

```text
src/main/java/agsfjope/backend/
  application/       Services, DTOs, and ports
  core/              Entities, enums, and repository interfaces
  domain/            Grading calculations and domain logic
  infrastructure/    Storage, payment, grading, email, and persistence adapters
  presentation/      HTTP controllers
  configuration/     Security, database, and framework configuration
src/main/resources/db/migration/   Flyway migrations
src/test/                          Automated tests
docker/                            Local service configuration
```

## Local setup

1. Install JDK 17 and Maven. Use a separate compatible JDK for student JARs compiled with a newer Java version.
2. Prepare an empty PostgreSQL database and the object-storage backend required by your selected services. Inspect `docker/docker-compose.yml` before starting local dependencies. Set `DB_PASSWORD` and `MINIO_SECRET_KEY` in the process environment before running Docker Compose.
3. Supply environment variables using `.env.example` as a reference. Never commit real credentials. Required values include `DB_URL`, `DB_USERNAME`, `DB_PASSWORD`, `JWT_SECRET`, `APP_ENCRYPTION_SECRET_KEY`, and `ALLOWED_ORIGINS`. Storage uses `MINIO_*` and/or `SUPABASE_S3_*`; email uses `MAIL_USERNAME` and `MAIL_PASSWORD`.
4. Set `SANDBOX_JAVA` if student JAR execution needs a different JDK. Configure payment and AI settings through the application's configuration mechanisms.
5. From the repository root:

```powershell
mvn clean verify
mvn spring-boot:run
```

Default server: `http://localhost:8080` (override with `PORT`).
Swagger UI: `http://localhost:8080/swagger-ui.html`.
OpenAPI JSON: `http://localhost:8080/api-docs`.

Seed accounts are disabled by default. For a local demo only, set `APP_SEED_ENABLED=true` and a `SEED_PASSWORD` of at least 12 characters. Flyway manages database migrations; review migration and seeding behavior before using an existing database. Configure a fresh local environment rather than pointing the application at a shared production database.

## Grading limitations

Child-process execution and JVM limits are not a complete security boundary for hostile student code. Review operating-system/container isolation before accepting untrusted uploads. Structural rules and scoring vary by grading mode; no claim of perfect scoring accuracy or benchmarked throughput is made.

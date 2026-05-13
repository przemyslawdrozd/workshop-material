# Prompt — Generate Workshop TODOs for a Similar REST API App

Use this prompt in another repository to generate language-neutral workshop TODO files for a similar application, even if the backend or frontend uses a different technology stack.

```text
Analyze this codebase and create a `todos/` directory with workshop-style markdown TODO files for further development of a REST API application.

The TODOs must be generic and language-neutral. Do not write tasks that depend on a specific framework, programming language, ORM, test runner, frontend framework, or package name unless you put those details only in an optional "In this repo" note. Write the main task descriptions in terms of behavior, architecture, API contracts, validation rules, persistence, security, testing, and frontend integration.

First inspect the codebase and identify:

1. The current REST API resources and endpoint groups.
2. The implemented CRUD-style and custom operations.
3. The request and response model patterns.
4. The persistence approach and database/schema conventions.
5. The validation and error response approach.
6. The API documentation or OpenAPI conventions.
7. Existing tests, sample requests, API collections, and CI workflows.
8. Existing frontend routes, services, models, forms, and API integration points, if a frontend exists.
9. Current gaps that are useful for workshop participants.

Then create these markdown files:

- `todos/README.md`
- `todos/01-tests.md`
- `todos/02-auth.md`
- `todos/03-resource-lifecycle.md`
- `todos/04-backend-improvements.md`
- `todos/05-frontend-integration.md`
- `todos/06-stretch-goals.md`

Requirements for `todos/README.md`:

- Explain how to use the workshop TODOs.
- Include a difficulty legend: Beginner, Intermediate, Advanced.
- Include a track table linking to each TODO file.
- Include a suggested sequencing diagram or list.
- Explain the generic wording rule:
  - Say "the API framework" instead of a framework name.
  - Say "the route registration mechanism" instead of a specific routing method.
  - Say "the request validation library" instead of a specific package.
  - Say "the test framework" instead of a specific test runner.
  - Say "the database access layer" instead of a specific ORM.
  - Put local implementation details only under "In this repo" notes.

Requirements for `todos/01-tests.md`:

- Add tasks for creating an API test suite.
- Add tasks for testing resource creation validation.
- Add tasks for testing important business rules.
- Add tasks for testing resource lifecycle guards.
- Add tasks for testing health/readiness endpoints.
- Add tasks for adding sample error-case requests.
- Keep the main wording independent of test framework names.

Requirements for `todos/02-auth.md`:

- Add tasks for auditing anonymous access.
- Add tasks for protecting resource and mutation endpoints.
- Add tasks for adding a simple workshop login/token/session flow.
- Add tasks for ownership and role checks.
- Add tasks for documenting authenticated API usage.
- Add tasks for frontend token/session integration if a frontend exists.
- Keep the main wording independent of any specific auth library.

Requirements for `todos/03-resource-lifecycle.md`:

- Add tasks for defining allowed resource statuses.
- Include a reversible inactive/deactivate/reactivate flow.
- Include terminal closed/deleted behavior.
- Add tasks for state transition rules.
- Add tasks for lifecycle audit/history.
- Add tasks for frontend status badges and status-aware actions if a frontend exists.
- Use the app's domain vocabulary, but keep the structure generic.

Requirements for `todos/04-backend-improvements.md`:

- Add tasks for request validation.
- Add tasks for pagination and filtering.
- Add tasks for global error handling.
- Add tasks for structured logging and correlation IDs.
- Add tasks for concurrency protection around sensitive mutations.
- Add tasks for idempotency on mutation endpoints.
- Add tasks for database migrations/schema evolution.
- Add tasks for CORS, rate limiting, or other API hardening as applicable.

Requirements for `todos/05-frontend-integration.md`:

- Include only if the repository has a frontend. If no frontend exists, create the file but mark it as optional and describe what a future frontend could integrate.
- Add tasks for wiring incomplete UI fields to backend behavior.
- Add tasks for replacing raw IDs with human-friendly pickers.
- Add tasks for displaying API error details.
- Add tasks for adding a shared frontend error handling mechanism.
- Add tasks for exposing backend detail endpoints in UI routes.
- Add tasks for filtering/searching list or history screens when backend support exists.

Requirements for `todos/06-stretch-goals.md`:

- Add advanced tasks such as API client/Postman collection generation, asynchronous status processing, export/download endpoints, real-time updates, local full-stack orchestration, configurable database provider, API versioning, and CI.
- Keep these optional and clearly marked as advanced or stretch work.

Formatting rules:

- Use GitHub-flavored Markdown.
- Use checkboxes for tasks.
- Use clear headings and acceptance criteria.
- Prefer concise task descriptions.
- Include "In this repo" notes only when they help participants find the local implementation.
- Do not create separate status files.
- Do not track progress in a separate `status/` directory.
- If the repository already has a plan file, keep status inside that plan and make the `todos/` directory workshop-oriented only.

Output expectation:

Create the files directly in the repository if file editing is allowed. If file editing is not allowed, output the full markdown content for each file.
```


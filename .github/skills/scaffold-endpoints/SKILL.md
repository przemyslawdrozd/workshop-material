---
name: scaffold-endpoints
description: Create new API endpoints following the project's documented API conventions, including routing, request/response models, validation, and API documentation metadata. Use this when asked to add or scaffold new endpoints.
---

# Scaffold API Endpoints

Create new API endpoints following the conventions used in the current project, regardless of programming language, framework, or API style.

## Capabilities

- Detect the API style used in the project, for example:
  - REST API
  - Minimal API
  - Controller-based API
  - Function-based routes
  - Serverless handlers
  - GraphQL resolvers
  - RPC-style endpoints
- Register new endpoints using the routing mechanism already used by the project.
- Follow the existing route naming and prefix conventions.
- Use the existing request and response model patterns.
- Add validation using the validation approach already present in the codebase.
- Add error handling consistent with existing endpoints.
- Add API documentation metadata when the project supports it, for example:
  - route name or operation ID
  - tags or groups
  - summary
  - description
  - request body schema
  - response schemas
  - success status codes
  - error status codes
- Update example request files, API collections, OpenAPI specs, or tests when the project uses them.

## Context Discovery

Before scaffolding a new endpoint, inspect the existing project structure and conventions.

Look for:

- existing endpoint registration files
- route modules
- controllers
- handlers
- routers
- request DTOs or schemas
- response DTOs or schemas
- validation patterns
- error response patterns
- authentication or authorization middleware
- API documentation annotations or metadata
- test files for existing endpoints
- sample request files such as:
  - `.http`
  - `.rest`
  - Postman collections
  - OpenAPI / Swagger files
  - API client examples

## General Endpoint Requirements

When creating an endpoint, include the project-equivalent of:

- route path
- HTTP method or operation type
- request input model, when needed
- response output model
- success status code
- error responses
- validation
- authorization, when required by similar endpoints
- API documentation metadata, when supported
- tests or sample requests, when the project has them

## API Documentation Metadata

When the framework supports API documentation, include metadata equivalent to:

- unique operation name or operation ID
- tag, group, or category
- short summary
- full description
- request schema
- success response schema
- error response schemas

Do not skip documentation metadata if similar endpoints include it.

## Conventions

- Follow the existing file organization.
- Follow the existing naming style.
- Follow the existing route prefix conventions.
- Follow existing request and response model naming.
- Prefer named request and response models over anonymous or inline response objects when the project uses models.
- Keep handler logic consistent with the surrounding code.
- Do not introduce a new framework, architecture, or validation library unless explicitly requested.
- Do not change unrelated endpoints.
- Do not invent business rules that are not requested or visible in existing code.
- If required information is missing, scaffold the endpoint with clear TODO comments.

## Output Format

When asked to scaffold an endpoint, provide:

- files changed or created
- endpoint route and method
- request model, if applicable
- response model
- validation behavior
- documented success and error responses
- sample request, if applicable
- tests added or recommended

## Example Output

```md
## Endpoint Scaffolded

### Route

`POST /api/resources`

### Changes

- Added a new create-resource endpoint using the existing router pattern.
- Added a named request model for incoming payload validation.
- Added a named response model for successful responses.
- Added validation consistent with existing create endpoints.
- Added API documentation metadata including operation ID, tags, summary, description, and response schemas.
- Updated sample API requests.

### Validation

- Returns a bad request response when required fields are missing or invalid.

### Responses

- Success response uses the project’s standard response model.
- Error responses follow the existing error response convention.

### Follow-up

- Add integration tests if the project already contains endpoint test coverage.
```

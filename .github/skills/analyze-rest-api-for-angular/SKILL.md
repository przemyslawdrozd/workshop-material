---
name: analyze-rest-api-for-angular
description: Inspect a codebase with a REST API and derive the UI-relevant API contract needed to build Angular features. Use this before planning or scaffolding Angular UI from backend code.
argument-hint: "[backend folder, frontend folder, resource, or API notes]"
---

# Analyze REST API for Angular

Use this skill to inspect a backend codebase and derive the current REST API contract in a form that is useful for Angular UI generation.

This skill is for discovery first. Do not start scaffolding Angular code until the API contract is clear enough to support a reliable UI plan.

## Goal

Produce an accurate, UI-oriented understanding of the REST API as it exists today, regardless of backend language, framework, or folder layout.

## When to use

Use this skill when the user asks to:

- build Angular UI from an existing backend
- connect an Angular app to the current REST API
- infer screens, forms, or routes from backend endpoints
- understand a backend API before creating Angular services or components

Do not use this skill for:

- frontend-only tasks with no API discovery work
- GraphQL-only, gRPC-only, or event-only backends with no REST API
- purely visual design conversion tasks

## Required workflow

1. Confirm that the repository exposes a REST API.
2. Detect the backend stack, framework, and endpoint registration style.
3. Discover the API from the most reliable source available, in this order:
   - code-derived OpenAPI or Swagger definitions
   - route, controller, handler, or endpoint declarations in source code
   - request tests, `.http` files, `.rest` files, Postman collections, or API docs as supporting evidence
4. Group endpoints into UI-relevant resources or domains.
5. Derive the details Angular code will need, including:
   - HTTP methods and paths
   - path params and query params
   - request bodies
   - response shapes
   - validation rules
   - authentication and authorization requirements
   - pagination, sorting, filtering, and search behavior
   - upload, download, or async workflow behavior
   - common error responses when derivable
6. Identify backend patterns that affect frontend architecture, such as:
   - resource-oriented CRUD flows
   - nested resources
   - wizard or multi-step flows
   - server-side filtering or search
   - role-based endpoint differences

## Discovery checklist

Look for the project-equivalent of:

- route registration
- controllers or handlers
- versioned API prefixes
- request DTOs, schemas, serializers, or models
- response DTOs, schemas, serializers, or models
- validation rules
- auth middleware, policies, or annotations
- OpenAPI or Swagger documents
- sample requests
- API tests

Do not assume conventional folder names. Follow the real registration path and type definitions used by the repository.

## Output expectations

When using this skill, provide:

- detected backend stack
- authoritative API sources that were used
- the discovered resources or endpoint groups
- UI-relevant contract details for each group
- known gaps or assumptions

The output should be detailed enough that an Angular planner or scaffolder can continue without redoing the same discovery.

## Failure behavior

If the repository does not expose a REST API, stop and explain that Angular UI cannot be derived from the current codebase with this skill.

If only part of the API can be derived, capture the reliable parts first and clearly label the uncertain parts.

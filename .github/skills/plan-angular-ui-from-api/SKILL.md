---
name: plan-angular-ui-from-api
description: Turn a REST API contract into an Angular UI plan with routes, pages, services, models, and interaction patterns. Use this after API discovery and before scaffolding Angular code.
argument-hint: "[resource, feature area, route prefix, or API summary]"
---

# Plan Angular UI from API

Use this skill to translate a REST API contract into a concrete Angular implementation plan before code generation starts.

## Goal

Create a route and feature plan that maps backend capabilities to Angular screens, services, models, and interactions while preserving a clean separation of responsibilities.

## When to use

Use this skill when the user asks to:

- plan Angular screens from an API
- design Angular routes and feature structure from backend resources
- decide how API endpoints should map to components and services
- prepare a feature plan before scaffolding Angular code

## Planning rules

1. Plan from the current API contract, not from assumed product behavior.
2. Follow the repository's Angular conventions when they already exist.
3. If the repository has no strong Angular conventions, prefer a feature-oriented structure.
4. Keep business logic in services. Services should own:
   - API orchestration
   - request and response mapping
   - reusable domain rules
   - caching or mutation coordination when needed
5. Keep route-aware UI logic in components. Route components should own:
   - route params and query params
   - page composition
   - page-specific loading, empty, and error states
   - page-level action wiring and navigation
6. Keep shared child components presentation-focused unless the project already uses a different pattern.
7. Do not invent screens, filters, or actions that are not supported by the API or the user's request.

## Required workflow

1. Review the discovered API resources and operations.
2. Identify the user-facing pages implied by the API, for example:
   - list pages
   - detail pages
   - create and edit forms
   - search and filter views
   - dashboards or summary pages when supported by dedicated endpoints
3. Map those pages to route definitions and feature boundaries.
4. Define the service surface for each feature, including which service methods should back each route or action.
5. Define the component structure for each route, including:
   - route component
   - reusable child components
   - form components when needed
   - table or detail views
6. Define the shared models, DTO mappings, and any adapters needed between API responses and UI models.
7. Identify cross-cutting concerns such as auth, guards, interceptors, error presentation, and shared filters.

## Default feature layout

If the repository does not already use a stronger convention, prefer a layout similar to:

- `feature.routes.ts`
- `pages/`
- `components/`
- `services/`
- `models/`

Use standalone components when the Angular project already uses them or when creating new Angular code with no existing pattern to follow.

## Output expectations

Provide:

- proposed routes
- page and component breakdown
- service responsibilities
- model or adapter responsibilities
- loading, empty, and error state expectations
- assumptions or unanswered questions

The plan should be concrete enough that Angular scaffolding can start immediately.

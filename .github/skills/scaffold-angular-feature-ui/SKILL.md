---
name: scaffold-angular-feature-ui
description: Scaffold or update Angular routes, components, services, and models from an API-backed feature plan while keeping business logic in services and route-aware UI logic in components.
argument-hint: "[feature name, target folder, route, or API summary]"
---

# Scaffold Angular Feature UI

Use this skill to implement Angular UI that is backed by a REST API and already has enough API or feature context to scaffold safely.

## Goal

Create or update Angular feature code that follows repository conventions and keeps responsibilities cleanly split between services and components.

## When to use

Use this skill when the user asks to:

- scaffold Angular pages from an API-backed feature
- create Angular routes, components, and services for a REST resource
- connect Angular UI to backend endpoints
- implement a planned Angular feature from an API contract

## Required workflow

1. Inspect the target Angular project and determine:
   - standalone components versus NgModules
   - routing conventions
   - folder layout
   - naming patterns
   - service and HttpClient patterns
   - state management approach
   - form approach
   - test conventions
2. Find nearby feature examples and mirror them.
3. Create or update the project-equivalent of:
   - routes
   - route components or page components
   - reusable child components
   - services
   - models or interfaces
   - mappers or adapters when needed
   - tests when similar features already have them
4. Wire the route components to services without moving business logic into components.
5. Update shared exports, navigation, or route registration when the project already uses them.
6. Run the existing Angular validation commands used by the project after code changes.

## Responsibility split

Services should own:

- HttpClient calls
- request building
- response mapping
- data normalization
- reusable domain rules
- mutations and reusable async workflows

Route components should own:

- reading route params and query params
- page-level composition
- page-level loading, empty, and error presentation
- handling user actions and delegating work to services
- navigation after successful actions

Reusable child components should stay focused on presentation and local interaction unless the repository already uses a different convention.

## Angular implementation rules

- Prefer typed service methods and explicit models.
- Keep templates lean and readable.
- Use reactive forms for non-trivial forms unless the project already favors template-driven forms.
- Reuse interceptors, shared UI components, and error handling patterns that already exist.
- Do not introduce a new state library unless it is already used or explicitly requested.
- Do not create a brand-new Angular workspace unless the user explicitly asks for it or confirms where it should live.

If there is no stronger existing pattern, prefer a feature-oriented structure with standalone route components and dedicated services.

## Output expectations

When work is complete, provide:

- files created or updated
- routes added or changed
- the service and component split
- any assumptions made because the API or existing frontend patterns were incomplete

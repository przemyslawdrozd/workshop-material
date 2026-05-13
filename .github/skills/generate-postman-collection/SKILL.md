---
name: generate-postman-collection
description: Analyze a backend repository with a REST API, generate or refresh a repository-language script in the skill folder, and use it to keep the Postman collection assets up to date with the latest API changes.
argument-hint: "[backend folder, base URL, or API notes]"
---

# Generate Postman Collection

Use this skill when a repository is a backend application with a REST API and you want a reproducible Postman collection generated from the current implementation.

## Goal

Inspect the codebase, understand the REST API as it exists today, write or update the generator script in `.github/skills/generate-postman-collection/scripts/`, and generate fresh assets in `.github/skills/generate-postman-collection/assets/`.

The generated script must be written in the primary language already used by the repository, for example TypeScript, JavaScript, Python, C#, Java, Go, PHP, or Ruby.

## When to use

Use this skill when the user asks to:

- generate a Postman collection from a backend repository
- refresh an existing Postman collection after API changes
- replace placeholder collection assets with real generated assets
- create a reusable generator script so the collection can be regenerated later

Do not use this skill for:

- frontend-only repositories
- GraphQL-only, gRPC-only, or message-driven projects with no REST API
- manual endpoint implementation tasks unless collection generation is also required

## Required workflow

1. Inspect the repository and confirm that it contains a REST API.
2. Detect the primary backend language, framework, and route declaration style.
3. Discover the current API surface from the most reliable source available, in this priority order:
   - existing OpenAPI or Swagger definitions when they are generated from code or kept current
   - route, controller, handler, or endpoint definitions in source code
   - request tests, HTTP examples, or existing API collections as supporting context
4. Infer collection structure, request methods, paths, parameters, request bodies, authentication, and environment variables from the current codebase.
5. Generate or update the generator script (see "Script file naming" below).
6. Use that script to generate:
   - `.github/skills/generate-postman-collection/assets/collection.json`
   - `.github/skills/generate-postman-collection/assets/collection-env.json`
7. Overwrite stale generated outputs so the assets always match the latest API state.

## Script file naming

The script lives at `.github/skills/generate-postman-collection/scripts/`.

- On the **first run**, the placeholder file `postman-generate.placeholder` exists. Replace it with a real generator script and **rename the file extension** to match the repository's primary language (e.g., `postman-generate.php`, `postman-generate.ts`, `postman-generate.py`, `postman-generate.cs`). Delete the `.placeholder` file so only the correctly-named script remains.
- On **subsequent runs**, find and update the already-renamed script (the one with the language-appropriate extension). If only `.placeholder` exists, treat it as a first run.

## First-run behavior

If this is the first run and the script or assets still contain placeholders:

- replace the placeholder script with a real generator script using the correct language extension
- delete the `.placeholder` file
- replace placeholder asset files with real generated Postman assets
- do not preserve placeholder content

## Subsequent-run behavior

On every later run:

- start from the latest repository state, not from assumptions or older API snapshots
- inspect newly added, renamed, changed, and removed endpoints
- update the generator script when the API discovery logic needs to change
- regenerate both asset files so the collection stays current
- overwrite previous generated assets instead of merging stale endpoints forward

Never treat the existing collection as authoritative when the codebase has changed. The backend source of truth is the current API implementation.

## API discovery checklist

Look for the project-equivalent of:

- route registration
- controllers, handlers, endpoints, or HTTP functions
- versioned prefixes and base paths
- path parameters and query parameters
- request DTOs, models, schemas, or serializers
- response DTOs, models, schemas, or serializers
- validation rules
- authentication and authorization requirements
- OpenAPI / Swagger documents
- sample `.http` or `.rest` files
- existing Postman collections or API test suites
- environment variables such as base URL, tokens, tenant IDs, or example IDs

## Script requirements

The generator script must:

- be written in the repository's primary implementation language
- use the correct file extension for that language (not `.placeholder`)
- follow the repository's existing conventions and tooling
- avoid introducing a new runtime or dependency unless it is clearly necessary and appropriate for the project
- be deterministic so repeated runs produce stable asset output when the API has not changed
- derive collection data from the current codebase, not manual hardcoded endpoint lists unless the repository already uses that pattern
- be safe to rerun as part of normal repository maintenance

## Asset requirements

### Request descriptions

Every request in `collection.json` must include a `description` field that explains:

- what the endpoint does
- what parameters it expects
- what response codes it returns
- any business rules or constraints (e.g., "balance cannot go below 0")

### Example responses

Every request must include at least one saved example response in the `response` array. Each example response should contain:

- a descriptive `name` (e.g., "Success - Account Created", "Error - Validation Failed")
- the expected `status` and `code`
- realistic `body` content matching the API's documented response envelope
- appropriate `header` entries (at minimum `Content-Type: application/json`)

Include both success and error examples when the endpoint has documented error cases (e.g., 404, 422).

### Data flow and variable chaining

The collection must be **fully executable in sequence without manual copy-pasting of values**. Achieve this by:

1. **Test scripts (post-response scripts):** Add `event` blocks with `"listen": "test"` scripts that extract dynamic values from responses and store them as collection or environment variables. For example, after a resource creation request, extract the returned `id` and set it as a collection variable so subsequent requests use it automatically.

2. **Pre-request scripts** when needed: Use `"listen": "prerequest"` scripts to set up dynamic data (e.g., generate unique names, timestamps).

3. **Variable propagation:** Design the request order within folders so that:
   - Creation endpoints (POST) run first and capture generated IDs
   - Read/update/delete endpoints reference those captured variables
   - Transfer or cross-resource endpoints reference variables set by earlier resource-creation requests

4. **Recommended execution order:** Arrange folders and requests so running the entire collection top-to-bottom with Postman's Collection Runner produces a complete, valid workflow without errors (assuming the server is running and clean).

5. **Pre-request scripts for POST requests:** Every POST request must include a `"listen": "prerequest"` script that prepares dynamic body data before sending. For example, generate unique names with timestamps, set default amounts, or prepare any fields that should vary per run. This ensures the collection produces distinct data on each execution and avoids duplicate-name or stale-data issues.

The goal is: import the collection, set the base URL, click "Run Collection", and every request succeeds in order.

### Base URL and path prefix deduplication

The `baseUrl` variable must include the full API prefix (e.g., `http://localhost:8000/api`), and individual request paths must **not** repeat that prefix. For example, if `baseUrl` is `http://localhost:8000/api`, a request to the accounts endpoint should use path segments `['accounts']`, not `['api', 'accounts']`. Before writing the collection, inspect the route definitions to determine the common API prefix (e.g., `/api`) and include it in `baseUrl` once. Request URLs should be relative to `baseUrl` — never duplicate a path segment that already appears in the base variable.

### Base URL and port discovery

Do not assume a default base URL or port. Before generating assets, inspect the repository to determine the actual configured host and port:

1. **Check server and project configuration files** — look for:
   - `.env` or `.env.example` for variables like `APP_URL`, `APP_PORT`, `HOST`, `PORT`, `SERVER_PORT`, `ASPNETCORE_URLS`, or similar
   - `docker-compose.yml` / `Dockerfile` for exposed ports and host mappings
   - server configuration files (e.g., `launchSettings.json`, `application.properties`, `application.yml`, `appsettings.json`, `config/server.*`, `vite.config.*`, `server.ts`)
   - build or run scripts (`package.json`, `Makefile`, `Procfile`, `Taskfile`, etc.) that specify `--port`, `--host`, or `--urls` flags

2. **Derive the `baseUrl`** from the discovered configuration. Use the scheme, host, and port that the project actually configures. For example, if `.env` contains `APP_URL=http://localhost:8000`, use that. If `docker-compose.yml` maps port 3000, use `http://localhost:3000`. If `launchSettings.json` specifies `https://localhost:5001`, use that.

3. **If no explicit configuration is found**, fall back to the most common default for the detected framework and note in the collection description that the value was inferred and may need adjustment.

4. **Include guidance in the collection description** on how to adjust `baseUrl` if the user's setup differs — mention updating the environment variable in Postman and that the scheme (`http` vs `https`) should match their local server.

### Collection structure

`collection.json` should include, when derivable:

- collection metadata with a description of the API
- folders or grouping by resource or domain
- request name, HTTP method, and URL
- request descriptions explaining the endpoint
- path and query parameters
- headers
- authentication setup
- example request bodies based on known schemas
- saved example responses for success and error cases
- test scripts for variable extraction and data flow
- useful example variables such as `{{baseUrl}}`

### Environment structure

`collection-env.json` should include, when derivable:

- base URL variables with the value discovered from project configuration
- auth-related variables such as tokens or API keys with example placeholder values (e.g., `your-api-token-here`)
- common identifier placeholders used by multiple requests — use descriptive example values (e.g., `example-resource-uuid`) rather than empty strings, so the user understands what format is expected even before running the collection

Never leave environment variable values as empty strings. Every variable must have either a realistic default or a self-documenting placeholder value that indicates the expected format.

## Update rules

- remove endpoints from generated assets when they no longer exist in the API
- reflect renamed routes and changed HTTP methods
- keep auth configuration aligned with the current implementation
- keep environment variables aligned with current configuration conventions
- update test scripts and data flow when response shapes change
- update example responses when response envelopes or status codes change
- prefer code-derived truth over stale generated files

## Failure behavior

If the repository does not expose a REST API, stop and explain that the skill cannot generate a Postman collection from the current codebase.

If only part of the API can be derived automatically, generate the best complete collection possible from available evidence and clearly identify any assumptions or placeholders.

## Final response behavior

When responding after using this skill, include:

- the detected backend stack
- the files created or updated (including the renamed script with correct extension)
- how the collection was derived
- the data flow chain (which requests set which variables for downstream use)
- any gaps, assumptions, or placeholders that still need manual confirmation

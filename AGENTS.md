# Coding Agent Instructions

## Purpose

You are a coding agent working in a training and reference monorepo. Make safe, focused, repository-aware changes and validate them with the commands that actually exist in the affected template.

## Repository model

- This repository is **not** a single application.
- There is **no root build, test, or lint workflow**.
- Executable code lives in independent templates under `project-templates/`.
- Workshop and learning content lives outside the templates and should usually be treated as documentation, not runnable software.

## How to work here

1. Identify the target area before editing anything.
2. If the task touches executable code, identify the exact template in `project-templates/` first.
3. Inspect nearby files and mirror the repository's existing conventions.
4. Make the smallest complete change that solves the task.
5. Update related docs or navigation only when the change makes them inaccurate.
6. Validate with the relevant existing commands for the affected template.

## Repository layout

- `szkolenie/` - step-by-step workshop flow in Polish
- `study-materials/` - deeper reference material
- `quiz/` - short knowledge checks
- `mock-questions/` - longer practice questions
- `project-templates/` - independent coding sandboxes
- `materials/` - shared screenshots and images
- `.github/agents/` - specialized agent definitions
- `.github/skills/` - focused reusable skills
- `mcp/` - MCP workflow notes

## Agent and skill routing

Prefer the most specialized agent or skill that matches the task instead of handling everything as one generic prompt.

### Agents

- `technical-documentation` - maintain evidence-based technical docs and README content
- `readme-creator` - create or improve README-focused documentation only
- `scaffolding` - scaffold code that matches the current repository conventions
- `angular-rest-ui` - build Angular UI from an existing REST API

### Skills

- `analyze-rest-api-for-angular` - derive the current API contract before Angular work
- `plan-angular-ui-from-api` - convert the API contract into routes, pages, services, and models
- `scaffold-angular-feature-ui` - implement Angular UI from an approved or derived plan
- `convert-stitch-design` - reproduce a Stitch design in Angular or React with high visual fidelity
- `generate-postman-collection` - generate or refresh Postman assets from the current backend implementation
- `scaffold-endpoints` - add new API endpoints using existing project conventions
- `pr-description` - write PR text; do not use it as a substitute for code changes

### Preferred Angular workflow

For Angular UI backed by a REST API, follow this order:

1. `analyze-rest-api-for-angular`
2. `plan-angular-ui-from-api`
3. `scaffold-angular-feature-ui`

Use `convert-stitch-design` when visual fidelity to an existing design matters. Use `generate-postman-collection` when the repository needs current API collection artifacts.

## Repository conventions

- Match the language already used in the file you edit:
  - Polish for workshop content, study materials, quizzes, and most top-level docs
  - English for template READMEs and template-specific technical content already written in English
- Use relative links for repository files.
- Keep `README.md` aligned with the actual repository structure.
- Prefer editing the correct existing file over creating parallel documentation.
- Do not reorganize directories or rename files unless explicitly asked.
- Do not introduce new frameworks, libraries, or tooling unless the task clearly requires it.

## Template-specific rules

- Many files under `project-templates/` are teaching scaffolds. Inspect the real implementation before assuming the README describes the current code.
- In `project-templates/dotnet-web-api`, the current implementation is the default minimal API scaffold in `Program.cs`.
- In `project-templates/nodejs-api` and `project-templates/react-native-app`, `package.json` scripts are the source of truth for build, run, and test commands.
- In `project-templates/python-data-analysis`, notebook work and environment verification matter more than packaged application structure.

## Build, run, test, and validation commands

Run commands from the target template directory, not from the repository root.

### `project-templates/nodejs-api`

- Install: `cd project-templates/nodejs-api && npm install`
- Run in dev mode: `npm run dev`
- Build: `npm run build`
- Run built app: `npm start`
- Lint: `npm run lint`
- Full tests: `npm test`
- Single test file: `npm test -- --runTestsByPath src/path/to/file.test.ts`
- Coverage: `npm run test:coverage`
- Prisma helpers: `npm run db:migrate`, `npm run db:generate`, `npm run db:seed`, `npm run db:reset`
- Optional docs generation when API docs are affected: `npm run docs:generate`

### `project-templates/react-native-app`

- Install: `cd project-templates/react-native-app && npm install`
- Start Metro: `npm start`
- Run on Android: `npm run android`
- Run on iOS: `npm run ios`
- Lint: `npm run lint`
- Type-check: `npm run type-check`
- Full tests: `npm test`
- Single test file: `npm test -- --runTestsByPath __tests__/path/to/file.test.tsx`
- Coverage: `npm run test:coverage`
- Platform builds when relevant: `npm run build:android`, `npm run build:ios`

### `project-templates/react-todo-app`

- Install: `cd project-templates/react-todo-app && npm install`
- Run locally: `npm start`
- Build: `npm run build`
- Full tests: `npm test`
- Single test file: `npm test -- --runTestsByPath src/path/to/file.test.tsx`

### `project-templates/dotnet-web-api`

- Restore: `cd project-templates/dotnet-web-api && dotnet restore`
- Build: `dotnet build`
- Run: `dotnet run`

There is currently no test project in this template. Do not invent one; validate with the existing build and any task-specific runtime checks that are actually needed.

### `project-templates/python-data-analysis`

- Install: `cd project-templates/python-data-analysis && pip install -r requirements.txt`
- Minimal install: `pip install -r requirements-minimal.txt`
- Verify environment: `python verify_environment.py`
- Start notebook/lab: `jupyter lab copilot-data-analysis-starter.ipynb`
- Full tests if tests exist: `pytest`
- Single test file if tests exist: `pytest path/to/test_file.py`
- Formatting and lint tools available from requirements: `black .`, `flake8 .`

## Validation workflow

### Documentation-only changes

- Verify paths, links, filenames, and commands against the repository state.
- Do not run template build or test commands unless the documentation change depends on confirming executable behavior.

### Code changes

1. Identify the affected template.
2. Run the relevant existing commands for that template.
3. Make the change using nearby patterns.
4. Re-run the smallest complete validation set for the touched area.
5. Only run extra commands when the change affects them.

### Minimum expected validation by template

- `nodejs-api`: usually `npm run lint`, `npm test`, and `npm run build`
- `react-native-app`: usually `npm run lint`, `npm run type-check`, and `npm test`
- `react-todo-app`: usually `npm test` and `npm run build`
- `dotnet-web-api`: usually `dotnet build`
- `python-data-analysis`: usually `python verify_environment.py`; add `pytest`, `black .`, or `flake8 .` only when relevant

### Runtime verification

- Start the app or service only when the task affects runtime behavior, API behavior, UI behavior, or integration flow.
- Use the template's existing run command.
- Do not claim validation you did not perform.

## Change safety

- Do not modify unrelated files.
- Ask for clarification instead of guessing when scope is ambiguous.
- Prefer existing patterns for routing, models, validation, tests, and docs.
- If commands or docs conflict with implementation, trust the implementation.
- If a requested workflow does not exist in the target template, say so plainly instead of inventing new commands.

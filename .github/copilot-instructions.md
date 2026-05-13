# Copilot instructions for this repository

This repository is a **training and reference monorepo**, not a single application. There is **no root build, test, or lint workflow**. When a task touches executable code, first identify the target template in `project-templates/` and run commands from that template's directory.

## High-level architecture

- `szkolenie/` is the primary workshop path. The numbered `etap-*.md` files are meant to be read in sequence and form the guided curriculum.
- `study-materials/` expands the workshop path with deeper topic notes. These files complement `szkolenie/` rather than replacing it.
- `quiz/` and `mock-questions/` are assessment content. Keep them consistent with the workshop/study material terminology and difficulty.
- `project-templates/` contains **independent practice sandboxes** for different stacks (`dotnet-web-api`, `nodejs-api`, `python-data-analysis`, `react-native-app`, `react-todo-app`). They are not wired together and should be treated as separate mini-projects.
- `materials/` contains shared screenshots and image assets used by setup guides and workshop documentation.
- `.github/agents/` and `.github/skills/` contain Copilot-specific agent and skill definitions used by this repository.
- `mcp/` contains integration notes for MCP-based workflows and points back to the relevant skills in `.github/skills/`.

## Build, test, and lint commands

There is no root command set. Use the commands for the specific template you are editing.

### `project-templates/nodejs-api`

- Install: `cd project-templates/nodejs-api && npm install`
- Dev server: `npm run dev`
- Build: `npm run build`
- Lint: `npm run lint`
- Full test suite: `npm test`
- Single test file: `npm test -- --runTestsByPath src/path/to/file.test.ts`
- Coverage: `npm run test:coverage`
- Prisma helpers: `npm run db:migrate`, `npm run db:generate`, `npm run db:seed`, `npm run db:reset`

### `project-templates/react-native-app`

- Install: `cd project-templates/react-native-app && npm install`
- Metro: `npm start`
- Android: `npm run android`
- iOS: `npm run ios`
- Lint: `npm run lint`
- Type-check: `npm run type-check`
- Full test suite: `npm test`
- Single test file: `npm test -- --runTestsByPath __tests__/path/to/file.test.tsx`
- Coverage: `npm run test:coverage`

### `project-templates/react-todo-app`

- Install: `cd project-templates/react-todo-app && npm install`
- Dev server: `npm start`
- Build: `npm run build`
- Full test suite: `npm test`
- Single test file: `npm test -- --runTestsByPath src/path/to/file.test.tsx`

### `project-templates/dotnet-web-api`

- Restore: `cd project-templates/dotnet-web-api && dotnet restore`
- Build: `dotnet build`
- Run: `dotnet run`

### `project-templates/python-data-analysis`

- Install: `cd project-templates/python-data-analysis && pip install -r requirements.txt`
- Minimal install: `pip install -r requirements-minimal.txt`
- Verify environment: `python verify_environment.py`
- Start notebook/lab: `jupyter lab copilot-data-analysis-starter.ipynb`
- Full test suite if tests are added in this template: `pytest`
- Single test file if tests are added: `pytest path/to/test_file.py`
- Formatting/lint tools available from requirements: `black .`, `flake8 .`

## Key repository conventions

- Match the language already used in the file:
  - **Polish** for workshop content, study materials, quizzes, and most top-level documentation.
  - **English** for project template READMEs and template-specific technical content that is already in English.
- Use **relative links** for files inside the repository.
- Keep `README.md` aligned with repository structure. If you add a new top-level learning asset or major section, update `README.md`.
- Prefer editing the **existing** Markdown file in the right area instead of creating duplicate docs that cover the same topic.
- Preserve the tone and structure of the target file. The workshop materials are concise and instructional; template READMEs are more explanatory and exercise-oriented.
- Make the **smallest complete change** and avoid reorganizing directories or renaming files unless the task explicitly requires it.

## Template-specific conventions

- Many files under `project-templates/` are **teaching scaffolds**, not fully implemented applications. Their READMEs often describe the intended end state of an exercise. Inspect the actual files before assuming the documented architecture already exists.
- For the `.NET` template, the current implementation is the default minimal API scaffold in `Program.cs`, even though the README describes a richer target structure to build toward.
- For the Node.js and React Native templates, treat `package.json` scripts as the source of truth for runnable commands.
- For the Python template, the repository emphasizes notebook-based exploration and environment verification over a packaged application layout.
- When changing educational content, keep examples practical for workshop use and avoid duplicating concepts that are already covered in nearby materials.

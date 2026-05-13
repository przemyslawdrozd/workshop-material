# Stitch + Angular + Copilot CLI

![Docs](https://img.shields.io/badge/docs-setup-blue)
![Angular](https://img.shields.io/badge/framework-Angular-DD0031)
![MCP](https://img.shields.io/badge/integration-MCP-7C3AED)

This folder documents how to use the Stitch design from the public project below in an Angular workflow and how to connect GitHub Copilot CLI to Stitch through MCP.

- **Stitch project:** <https://stitch.withgoogle.com/projects/1595810958064881950?pli=1>
- **Stitch MCP setup guide:** <https://stitch.withgoogle.com/docs/mcp/setup>
- **Project skill for design conversion:** [../../.github/skills/convert-stitch-design/SKILL.md](../../.github/skills/convert-stitch-design/SKILL.md)

## Overview

Use this flow when you want Copilot CLI to help turn a Stitch design into Angular code:

1. Open the Stitch project and review the generated design.
2. Configure Stitch as an MCP server for GitHub Copilot CLI using the Stitch setup page.
3. Start Copilot CLI in your Angular workspace.
4. Ask Copilot to implement the screen in Angular while treating Stitch as the visual source of truth.
5. Refine the generated component structure, styling, and bindings as needed.

## Prerequisites

Before you start, make sure you have:

- access to the Stitch project linked above
- GitHub Copilot CLI installed and authenticated
- an Angular project or Angular workspace where the screen will be implemented
- any frontend styling dependencies expected by the exported design, such as Tailwind if the Stitch output uses Tailwind utility classes

## How to use the Stitch design in Angular

The Stitch project is the design source of truth. In practice, the Angular implementation usually follows this pattern:

1. Review the design in Stitch and identify the target screen or section to build.
2. Extract the key layout structure, spacing, typography, colors, and component hierarchy.
3. Move the markup into Angular component templates.
4. Convert repeated UI blocks into reusable Angular components.
5. Replace static content with Angular bindings such as `{{ value }}`, `[input]`, and `(click)` where needed.
6. Keep the first pass focused on matching the design before adding real data flows or API wiring.

### Recommended Angular integration approach

- Put the exported or adapted markup into a component template such as `*.component.html`.
- Keep component behavior in `*.component.ts`.
- Move reusable visual rules into shared styles, theme tokens, or your existing design system.
- If Stitch output uses Tailwind classes, either keep them in a Tailwind-enabled Angular app or translate them into your existing styling approach.
- Avoid changing the visual hierarchy until the initial design match is complete.

## Connect Copilot CLI to Stitch with MCP

Follow the Stitch instructions from the official setup page and add Stitch as a custom MCP server in Copilot CLI.

### Option 1: Add the server interactively

Start Copilot CLI:

```bash
copilot
```

Then add the MCP server:

```text
/mcp add
```

Fill the form with values like these:

| Field | Value |
| --- | --- |
| Server Name | `stitch` |
| Server Type | `HTTP` |
| URL | `https://stitch.googleapis.com/mcp` |
| HTTP Headers | `{"X-Goog-Api-Key":"YOUR_STITCH_API_KEY"}` |
| Tools | `*` |

Use your real Stitch API key locally, but do not commit it into the repository or share it in docs.

After saving, inspect the configured server:

```text
/mcp show stitch
```

### Option 2: Configure the server in a config file

If you prefer file-based configuration, add Stitch to your Copilot CLI MCP config file and provide the HTTP endpoint plus the API key header required by Stitch.

Example HTTP configuration:

```json
{
  "servers": {
    "stitch": {
      "type": "http",
      "url": "https://stitch.googleapis.com/mcp",
      "headers": {
        "X-Goog-Api-Key": "YOUR_STITCH_API_KEY"
      }
    }
  }
}
```

Use your real Stitch API key locally, but do not commit it into the repository or share it in docs.

After saving the config, restart `copilot` if needed and confirm the server is available:

```text
/mcp show stitch
```

If your environment uses a different Copilot CLI config filename or location, keep the same `stitch` server block and place it in the MCP config file that your local CLI installation reads.

## Suggested Copilot CLI workflow

Once MCP is configured and you are inside your Angular project:

```bash
copilot
```

Use prompts like:

```text
Use the connected Stitch design as the visual source of truth and implement this screen in Angular.
Start with the layout only and keep the existing project styling conventions.
```

```text
Use the skill at ../../.github/skills/convert-stitch-design/SKILL.md to convert the selected Stitch screen into Angular components in this folder.
```

```text
Create Angular components for the repeated cards, actions, and sections from the connected Stitch design, but do not connect them to the API yet.
```

## Recommended implementation sequence

1. Build a static Angular version of the screen.
2. Verify visual structure against the Stitch project.
3. Extract reusable components.
4. Add bindings and input models.
5. Connect data and events only after the UI matches the design.

## Notes and limitations

- This README documents the workflow, not the full design specification.
- If the Stitch project includes exportable code, use it as a starting point, then adapt it to Angular conventions.
- If the design includes a `DESIGN.md` or similar design-system notes, use those tokens and rules to keep Angular output consistent.
- If Copilot cannot access the design through MCP, reopen the Stitch setup page and verify the server configuration and authentication details.

## Related links

- [Repository root README](../../README.md)
- [Convert Stitch Design skill](../../.github/skills/convert-stitch-design/SKILL.md)
- <https://stitch.withgoogle.com/projects/1595810958064881950?pli=1>
- <https://stitch.withgoogle.com/docs/mcp/setup>

---
name: convert-stitch-design
description: Use this skill when converting a Stitch MCP design into Angular or React UI with the goal of matching the source design as closely as possible.
argument-hint: "[screen name, target framework, target folder]"
---

# Convert Stitch Design Skill

Use this skill when implementing a frontend screen from Stitch MCP into Angular or React.

## Goal

Convert a Stitch design into working frontend code while preserving the visual result as closely as possible.

The Stitch design must be treated as the visual source of truth.

## Core rules

1. Do not redesign the screen.
2. Do not simplify the layout unless explicitly asked.
3. Do not replace the visual system with generic framework defaults.
4. Preserve section order, hierarchy, spacing proportions, and alignment.
5. Preserve typography scale, font weight, line height, border radius, shadows, and color usage.
6. Keep the first pass focused on visual fidelity, not business logic.
7. Do not connect the screen to the API unless explicitly requested.
8. Do not invent new UI patterns if the design already defines one.
9. If something cannot be reproduced exactly, report it explicitly.
10. Work on one screen or one section at a time.

## Required workflow

### Step 1: Extract design specification first

Before writing application code:

- read the Stitch MCP design context for the selected screen
- extract the exact visual specification
- create or update a local design spec file if missing

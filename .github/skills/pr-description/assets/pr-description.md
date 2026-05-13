# Hello reviewers

**Generated:** 2026-05-07T22:25:43.223+02:00  
**Commit author:** drozdp  
**Branch:** agents-skills

---

## Summary

Adds a large new set of GitHub Copilot workshop assets, including study materials, project templates, Copilot agent and skill definitions, and MCP workflow notes. The repository entry points are also updated so the expanded structure is easier to navigate.

## Motivation

This branch expands the training and reference monorepo beyond the initial workshop scaffold so it can support guided learning, hands-on practice across multiple stacks, and reusable Copilot workflows in one repository.

## Changes

- Added repository-level Copilot guidance in `AGENTS.md` and `.github/copilot-instructions.md`
- Added four custom agents and seven reusable skills under `.github/agents/` and `.github/skills/`
- Added MCP workflow documentation under `mcp/`, including Angular/Stitch guidance and a TODO placeholder for GitLab MCP notes
- Expanded `README.md` to reflect the current repository layout and Copilot-specific configuration areas
- Added new study materials covering fundamentals, prompting, advanced features, responsible AI, planning, data handling, testing, privacy, developer use cases, emerging features, quick reference, and troubleshooting
- Added new project templates and supporting assets for `.NET Web API`, `Node.js API`, `Python data analysis`, `React Native`, and `React Todo`
- Added template-specific starter files such as package manifests, lockfiles, notebook assets, sample datasets, and minimal application scaffolds

## Testing

- [ ] Unit tests
- [ ] Integration tests
- [ ] Manual testing
- [ ] Existing behavior verified

No test execution evidence was available in the repository context. This repository also does not define a root validation workflow.

## Risk / Impact

Medium. This PR adds a large volume of documentation, training content, and starter template assets across many directories. Reviewers should confirm that the documented commands match the template files and that the included datasets, lockfiles, and placeholder MCP content are intentional.

## Reviewer Focus

- Accuracy of `README.md`, `AGENTS.md`, and `.github/copilot-instructions.md` against the current repository layout
- Completeness and consistency of the new study materials and template READMEs
- Scope and naming of the new custom agents, skills, and MCP notes
- Intentional inclusion of large sample data files and generated lockfiles

## Related Work

N/A

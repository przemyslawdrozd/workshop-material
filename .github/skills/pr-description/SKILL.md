---
name: pr-description
description: Write clear, review-ready pull request descriptions from code diffs, git commits, issue context, or a user's summary. Use this when the user asks to create, improve, review, rewrite, or generate a PR description, PR body, merge request description, changelog-style PR summary, reviewer notes, testing notes, or a risk/impact section. Do not use this for writing code changes unless the user also asks for implementation.
argument-hint: "[diff, branch, issue, or summary]"
---

# Pull Request Description Writer

Use this skill to produce high-quality pull request descriptions that help reviewers understand what changed, why it changed, how it was tested, and what risks or review focus areas exist.

## Goal

Create a pull request description that is specific, honest, concise, and useful for code review.

Prefer concrete details from the repository over generic filler.

Do not invent implementation details, tests, screenshots, ticket IDs, metrics, or results.

## When to use

Use this skill when the user asks for any of the following:

- Create a pull request description
- Create a PR body
- Improve or rewrite a PR description
- Summarize changes for a pull request
- Generate reviewer notes
- Generate testing notes for a PR
- Create a GitHub, GitLab, or Bitbucket merge request description
- Fill a PR template
- Explain what should be included in a PR description

## Inputs to inspect

When available, inspect the most relevant project context before writing:

1. Git context, for example:
   - `git diff main...HEAD`
   - `git diff origin/main...HEAD`
   - `git status --short`
   - `git log --oneline --decorate -n 20`
2. Related issue or ticket references from branch names, commit messages, or user-provided text
3. Test files, CI config, package scripts, or README instructions if testing details are unclear

If repository access or diff context is unavailable, ask for the diff, commit list, issue summary, or a short explanation of the change.

If the user wants a best-effort version without more context, produce one and clearly mark unknown areas as placeholders.

## Required output structure

Default to this structure unless the repository already has a PR template:

```md
## Summary

<!-- 1-3 sentences explaining what changed. -->

## Motivation

<!-- Why this change is needed. Mention the problem, ticket, feature request, or bug. -->

## Changes

<!-- Concrete technical changes. Use bullets. -->

-
-
-

## Testing

<!-- Explain exactly how this was verified. Do not invent tests. -->

- [ ] Unit tests
- [ ] Integration tests
- [ ] Manual testing
- [ ] Existing behavior verified

## Risk / Impact

<!-- Mention migrations, infrastructure changes, permissions, API changes, data impact, backward compatibility, performance, security, or operational risks. -->

## Reviewer Focus

<!-- Tell reviewers what deserves the closest attention. -->

## Related Work

<!-- Link issues, tickets, docs, or follow-up PRs. -->
```

## Writing rules

- Be specific. Replace vague phrases like "updated logic" with the actual logic that changed.
- Keep the summary short, usually 1-3 sentences.
- Use bullets for technical changes.
- Keep reviewer focus actionable.
- Do not claim tests passed unless there is evidence.
- If tests were not run, say so plainly and explain why if known.
- If information is missing, use clear placeholders such as `TODO: add ticket link` or `Not tested yet`.
- Mention breaking changes clearly.
- Mention infrastructure, data migration, security, IAM, environment variable, deployment, or API contract changes when relevant.
- Prefer plain language over marketing language.
- Avoid excessive implementation detail unless it helps review.
- Do not include irrelevant sections. If a section has no useful content, either omit it or write `N/A`.

## Asset update requirement

After every skill invocation, update `.github/skills/pr-description/assets/pr-description.md` with the latest generated PR description.

The asset file should contain:

1. A short greeting
2. A metadata block with:
   - generation timestamp
   - latest commit author when available
   - branch name when available
3. The final PR description body

If the latest commit author cannot be determined from the repository context, use `Unknown author`.

## Quality checklist

Before finalizing, verify that the PR description answers:

1. What changed?
2. Why was it changed?
3. How was it tested?
4. What could break?
5. What should reviewers focus on?
6. Are there related tickets, docs, screenshots, logs, or follow-up tasks?

## Common examples

### Small bug fix

```md
## Summary

Fixes CSV ingestion failing when headers contain spaces or unsupported SQLite characters.

## Motivation

CSV files from users often contain columns such as `Invoice Number` or `Customer Name`. The previous table creation logic used raw headers directly, which could generate invalid SQL.

## Changes

- Added SQLite-safe column name normalization
- Preserved a mapping between original CSV headers and normalized column names
- Added validation for empty or duplicate headers

## Testing

- Manually tested ingestion with a CSV containing headers with spaces
- Verified the SQLite table is created successfully
- Verified queries can use the normalized columns

## Risk / Impact

Low. Existing CSV ingestion behavior changes only for column normalization. Review compatibility with any code that expects raw column names.

## Reviewer Focus

Please check the normalization logic and duplicate header handling.
```

### Infrastructure change

```md
## Summary

Adds an SQS dead-letter queue for the ingestion worker and configures the main queue redrive policy.

## Motivation

Failed ingestion messages were previously retried without a durable failure destination, making debugging and replay harder.

## Changes

- Added a DLQ resource in Terraform
- Configured `maxReceiveCount` for the main queue
- Exposed queue ARNs as module outputs

## Risk / Impact

Medium. This changes queue infrastructure and failure handling. Existing messages should continue to process normally, but failed messages will now move to the DLQ after the configured retry limit.

## Reviewer Focus

Please verify the retry count, queue naming, IAM permissions, and module outputs.
```

## Final response behavior

When responding to the user:

- If enough context exists, provide the finished PR description only, unless explanation is requested.
- If context is partial, provide the best PR description plus a short note listing assumptions or missing information.
- If the repository has a PR template, follow that template exactly.
- If the user asks for multiple versions, provide concise, detailed, and release-note-style variants.

After generating the PR description, add a brief next-steps section that:

1. Asks for approval and shows a generated `gh` command to create or update the PR description using `.github/skills/pr-description/assets/pr-description.md`
2. Invites the user to request wording or content changes
3. Recommends the best next action based on the available context

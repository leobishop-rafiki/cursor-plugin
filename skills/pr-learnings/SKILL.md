---
name: pr-learnings
description: Reviews PR comments to identify reusable learnings for our agent rules.
disable-model-invocation: true
---

# PR Learnings

## Purpose

Review the comments on an open PR to identify generalisable learnings that can be adopted for agents going forward.

## Workflow

1. **Access the PR**. 
  - Use the following tools in order or precience: Github MCP server; `gh` and `git` cli tools; Github API.
2. **Review the PR comments** and associated code in the PR, creating a list of each class of comment, unifying duplicates and similar comments.
3. **Identify generalisable learnings** review the comments and identify if what generalisable learnings can be taken from these comments. The learnings should not be work specific but generalisable coding standards, best practice, anti-patterns to avoid, stylistic conventions, architectural design practices, etc...
4. **Propose learnings** to the user following the output format.

## Output format

Concise numbered list of the proposed learnings. Each learning should be able to be added to a cursor rule as is.

### Example

1. Avoid panic in `init` for configuration issues, prefer explicit fail fast during package, class, object, etc... initialisation.
2. Use package-level sentinel errors for expected outcomes that callers may inspect.
3. Represent absent enum values explicitly. Prevent missing or null data from silently becoming a valid zero-valued status or operator.
  - Reserve an explicit unknown or undefined zero value for wire enums. Handle null, empty, etc... deliberately. 
  - Never allow absent input to default to success or a real provider capability.
4. HTTP clients model the provider API and return domain-specific responses/errors. Keep application status mapping, capability policy, integration decisions, etc... in the service adapter.
  - Do not expose internal HTTP response types to callers.

---
name: github-pull-request
description: Generate GitHub pull request titles and descriptions from code changes. Use when creating PR, updating PR, generating PR content for output, or when user mentions pull request, PR, merge request, create PR, update PR, write PR description, PR text, generate PR, prepare PR, GitHub workflow, code review.
license: Unlicense
---

# GitHub Pull Request

## Critical: Source of Changes

**ALWAYS analyze ALL changes in the entire branch that will be merged**, not just:

- ❌ The last commit
- ❌ Previous chat context
- ❌ Individual file changes mentioned earlier

**Required approach:**

1. Request full branch diff or complete changeset
2. Review every modified file in the branch
3. Understand the cumulative impact of all commits
4. Base PR title and description on the complete picture

This ensures PR descriptions accurately reflect the total scope of changes being merged into the target branch.

## Language Requirement

Always write PR content in English only

## Output Format for Chat

When user requests PR content to be sent to chat (e.g., "send PR to chat", "show me the PR", "generate PR description"):

**ALWAYS wrap the complete PR content in a markdown code block:**

````markdown
[PR Title Here]

[Full PR Description Here]
````

This allows user to easily copy the entire PR content with proper formatting preserved.

**DO NOT** output PR content as rendered markdown in chat - it must be in a copyable code block.

## PR Title

- ≤50 characters, imperative mood ("Add feature" not "Added" or "Adds")
- Accurately reflect main purpose of changes
- No issue numbers in title (use description)
- For monorepos, consider a scoped title (e.g., `feat(scope): description`)

**Examples:**

- Add dark mode support to theme package
- Fix input validation in text field component
- Refactor build configuration for better performance

## PR Description

**Required sections:**

1. **Summary** - What changed (bullet points, mention affected packages/modules)
2. **Motivation** - Why these changes were necessary, impact on project
3. **Related Issues** - `Fixes #123`, `Closes #456`, `Related to #789`

**Optional sections:**

- Testing Notes
- Breaking Changes (with migration guide)
- Performance Impact

**Example:**

```markdown
## Summary

Adds dark mode support to the theme package:

- Added dark color palette with semantic tokens
- Updated CSS variables for theme switching
- Added theme toggle component

## Motivation

Users requested dark mode to reduce eye strain and improve accessibility.

## Related Issues

Fixes #42
```

## Writing Style

Write engaging, conversational descriptions - not boring technical documents!

- Use clear, simple language
- Explain the "why" behind decisions
- Emojis in description body OK ✅ (NOT in title)
- Show enthusiasm for clever solutions
- Be honest about challenges and trade-offs

See [references/pr-examples.md](references/pr-examples.md) for boring vs engaging examples.

## Edge Cases

- **Large changesets**: Group changes by component in summary
- **Updating existing PR**: Preserve metadata, add update comment
- **Breaking changes**: Mark clearly, provide migration guide
- **Monorepo**: Clearly indicate affected packages

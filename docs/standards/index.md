# Code Standards

This section documents the conventions visible in the supplied source. It does not invent rules that the project is not currently following.

## Variables and functions

The JavaScript source primarily uses camelCase:

- `imageDetector`
- `authManager`
- `sessionManager`
- `messageHandler`

## React components

React components use PascalCase:

- `AccountButton.jsx`
- `AccountMenu.jsx`
- `ReaderControls.jsx`
- `Stats.jsx`

## Files

The project generally uses:

- PascalCase for React components;
- camelCase for JavaScript modules.

## Folders

Feature/responsibility folders are lowercase:

```
api, background, commands, components, content, metrics, pages, speech, utils
```

## New-code rule

When adding functionality:

1. Identify which existing responsibility owns the behaviour.
2. Place the new code in that responsibility's folder.
3. Avoid creating a new architectural layer for a small feature.
4. Keep DOM code out of React UI.
5. Keep backend request routing in the existing background/API pattern.

## Branch naming

A formal branch naming convention is **not confirmed** in the supplied extension materials.

The team does use Jira for work tracking — see the [Jira timeline](https://andylaique.atlassian.net/jira/software/projects/MATRIX/boards/34/timeline).

!!! warning
Do not document a mandatory branch format until the team's actual Git workflow confirms one.

## Commit messages

A formal commit-message convention is **not confirmed** in the supplied materials.

!!! warning
Do not invent a Conventional Commits requirement unless the repository actually uses it.

## Pull requests

A formal PR checklist/approval rule is **not confirmed** in the supplied extension materials. The final GitHub documentation should be updated once the team confirms its real PR workflow.

## Linting

The project uses ESLint. Configuration: `eslint.config.js`.

Run:

```bash
npm run lint
```

## Current lint status

The supplied project currently has lint errors. Reported categories include:

- Chrome extension globals not recognised in some files;
- unused parameters;
- empty catch blocks;
- error-handling/lint issues.

!!! danger
The documentation should not claim that lint is currently clean.

## Comments and docstrings

A strict team-wide comment/docstring format is not confirmed. The practical convention should be:

- comment non-obvious decisions;
- explain why a workaround exists;
- avoid comments that merely repeat the code;
- update comments when behaviour changes.

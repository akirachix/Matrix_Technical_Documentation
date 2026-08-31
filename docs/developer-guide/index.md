# Developer Guide

This section is the practical guide for developers joining the SecureReader project. It explains how the repository is organised, where new code belongs, and the conventions used when making changes.

## Development workflow

1. Create or switch to the appropriate feature branch.
2. Make the smallest focused change that solves the task.
3. Run the relevant tests and validation commands.
4. Review the changed files before committing.
5. Open a pull request using the team's normal review process.

## Repository structure

The documentation repository is organised by product area:

```text
docs/
├── overview/
├── architecture/
├── frontend/
├── chrome-extension/
├── backend/
├── ai/
├── developer-guide/
├── assets/
└── stylesheets/
```

## Where new code goes

- Web frontend documentation belongs under `docs/frontend/`.
- Chrome extension documentation belongs under `docs/chrome-extension/`.
- Backend documentation belongs under `docs/backend/`.
- AI documentation belongs under `docs/ai/`.
- Cross-project developer conventions belong under `docs/developer-guide/`.
- Shared images and diagrams belong under `docs/assets/`.
- Shared documentation styling belongs under `docs/stylesheets/`.

## Naming conventions

Use clear, descriptive names that match the existing project conventions. Keep filenames lowercase and use hyphens for documentation pages where appropriate.

## Formatting and linting

Markdown is the primary documentation format. Shared visual customisation is maintained in `docs/stylesheets/extra.css`, while site navigation and theme configuration are maintained in `mkdocs.yml`.

## Testing conventions

Test the area affected by a change rather than relying only on a full-site build. Existing QA evidence and project-specific test instructions are available in the [Testing and QA](../testing/) documentation.

## Git workflow

Use focused branches and commits that describe the change clearly. Pull requests should explain what changed, why it changed, and how it was tested.

## Related standards

The existing project standards are available in [Standards](../standards/).

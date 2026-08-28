# Deployment

## Extension build

```bash
npm run build
```

Output: `dist/`

## Local deployment

Use Chrome:

1. Extensions
2. → Developer Mode
3. → Load unpacked
4. → select `dist/`

## Chrome Web Store

A production Chrome Web Store publishing process is **not confirmed** in the supplied project materials.

!!! warning
    Do not claim that SecureReader is publicly distributed through the Chrome Web Store unless that has been verified.

## Backend deployment

The extension currently communicates with:

```
https://secure-reader-e8d40157a540.herokuapp.com
```

The exact backend deployment procedure is not contained in the supplied extension materials. Use the backend repository and [API documentation](https://secure-reader-e8d40157a540.herokuapp.com/docs) for backend deployment details.

## GitHub Pages deployment (this documentation site)

The technical documentation itself must be published on GitHub Pages. A documentation folder sitting in the repository does not satisfy the project requirement — it needs to be built and served as a live site.

This site uses **MkDocs** with the **Material** theme, deployed via **GitHub Actions**.

### 1. Repository layout

```
your-repo/
├── docs/                     # all markdown content
│   ├── index.md
│   ├── overview/
│   ├── getting-started/
│   ├── architecture/
│   ├── frontend/
│   ├── ai/
│   ├── backend/
│   ├── database/
│   ├── metrics/
│   ├── security/
│   ├── integrations/
│   ├── standards/
│   ├── testing/
│   ├── deployment/
│   ├── current-status/
│   └── references.md
├── mkdocs.yml
└── .github/
    └── workflows/
        └── deploy-docs.yml
```

### 2. Install MkDocs locally (optional, for previewing)

```bash
pip install mkdocs-material
mkdocs serve
```

Then open `http://127.0.0.1:8000` to preview before pushing.

### 3. Push the repository to GitHub

```bash
git init
git add .
git commit -m "Add SecureReader technical documentation site"
git branch -M main
git remote add origin https://github.com/<your-org>/<your-repo>.git
git push -u origin main
```

### 4. Enable GitHub Pages with GitHub Actions as the source

1. Go to your repo on GitHub → **Settings** → **Pages**.
2. Under **Build and deployment**, set **Source** to **GitHub Actions**.

### 5. Add the deploy workflow

The workflow file at `.github/workflows/deploy-docs.yml` builds the MkDocs site on every push to `main` and deploys it to GitHub Pages automatically. (This file is included in the project scaffold — see below.)

### 6. Verify

- Push to `main`.
- Open the **Actions** tab in GitHub and watch the `Deploy Docs` workflow run.
- Once it succeeds, the site is live at:

```
https://<your-org>.github.io/<your-repo>/
```

!!! danger
    The final GitHub Pages URL is **not confirmed yet** — replace the placeholder above with the live URL once deployed, and update it in [References](../current-status/index.md).

    Do not submit the repository folder URL as the final documentation URL — the requirement is a published, navigable site.
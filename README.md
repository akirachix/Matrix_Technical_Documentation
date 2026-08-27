# SecureReader Technical Documentation (Source)

This folder is a ready-to-deploy [MkDocs](https://www.mkdocs.org/) + [Material](https://squidfunk.github.io/mkdocs-material/) documentation site for SecureReader.

## Preview locally

```bash
pip install -r requirements.txt
mkdocs serve
```

Open http://127.0.0.1:8000

## Deploy

1. Push this folder (or merge it) into your GitHub repository, at the repo root.
2. In GitHub: **Settings → Pages → Source → GitHub Actions.**
3. Push to `main`. The workflow at `.github/workflows/deploy-docs.yml` builds and deploys automatically.
4. Site goes live at `https://<your-org>.github.io/<your-repo>/`.

## Before going live

- [ ] Update `repo_url` in `mkdocs.yml` to your real repository URL.
- [ ] Add the FigJam design link in `docs/references.md` and `docs/integrations/index.md` (currently a placeholder).
- [ ] Confirm the final live GitHub Pages URL and record it in `docs/deployment/index.md`.
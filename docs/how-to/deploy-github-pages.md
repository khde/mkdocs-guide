# Deploy MkDocs to Github Pages
This page describes how to deploy your MkDocs documentation to Github Pages.

## Github pages
[Github Pages](https://pages.github.com/) is a static site hosting service that allows you to publish your documentation directly from a GitHub repository.

!!! info "Plan Availability and Usage"
    GitHub Pages is available for free in public repositories. GitHub Pages is not allowed for commercial use. See [GitHub Pages limits](https://docs.github.com/en/pages/getting-started-with-github-pages/github-pages-limits) for more details.

## Deploying to Github Pages

To automate your MkDocs deployment to GitHub Pages, you can use GitHub Actions. This workflow automatically builds and deploys your documentation whenever you push changes to your repository.

### Setting up GitHub Actions

Create a new workflow file at `.github/workflows/deploy-docs.yml` in your repository with the following content:

```yaml
name: deploy-docs

on: # (1)
  workflow_dispatch:
  push:
    branches:
      - master
    paths:
      - 'docs/**'
      - 'mkdocs.yml' 

permissions:
  contents: write

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - name: Git Credentials
        run: |
          git config user.name github-actions[bot]
          git config user.email 41898282+github-actions[bot]@users.noreply.github.com
      - uses: actions/setup-python@v5
        with:
          python-version: 3.x
      - run: echo "cache_id=$(date --utc '+%V')" >> $GITHUB_ENV 
      - uses: actions/cache@v4
        with:
          key: mkdocs-material-${{ env.cache_id }}
          path: ~/.cache 
          restore-keys: |
            mkdocs-material-
      - run: pip install -r requirements.txt
      - run: mkdocs gh-deploy --force
```

1. It can be freely choosen, when to trigger the workflow

### Enabling GitHub Pages

After the first successful workflow run, you need to configure your repository:

1. Go to your repository **Settings** → **Pages**
2. Under "Build and deployment", select "Deploy from a branch"
3. Choose `gh-pages` as the branch and `/ (root)` as the folder

Your documentation will now be automatically deployed to GitHub Pages at `https://<username>.github.io/<repository>/` whenever you push changes to the `master` branch.

## How it works
Any trigger, whether manual or caused by a push, starts the workflow. MkDocs then builds the documentation. After the build, the workflow pushes the generated site to the `gh-pages` branch, which is why write permission for repository contents is required. Finally, GitHub Pages serves the site from that branch.
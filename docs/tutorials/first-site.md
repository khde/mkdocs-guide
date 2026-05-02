# Your first site

This tutorial guides you through creating a new documentation site, starting the local development server, editing a page, and building the static output.

## Create a new project

The `mkdocs new` command creates a new project directory with a default `mkdocs.yml` file and a single `index.md` page.

```bash
mkdocs new my-project
cd my-project
```

Your folder now contains:

```text
my-project/
├─ docs/
│  └─ index.md
└─ mkdocs.yml
```

- `mkdocs.yml`: This is your main configuration file. You'll use it to set your site's title, choose a theme, and configure navigation.
- `docs/`: This directory contains all of your documentation content, written as Markdown files. `index.md` is the default home page.

## Start the local server

The `mkdocs serve` command starts a local development server that watches for file changes and automatically rebuilds your site.

```bash
mkdocs serve
```

Open `http://127.0.0.1:8000` in your browser.

!!! success "Expected result"
    You should see a simple documentation site with a single home page.

## Edit your first page

Open `docs/index.md` in your editor and replace the default content:

```markdown title="docs/index.md"
# Hello, world!

This is my first MkDocs site.
```

When you save the file, the browser will automatically reload to show the new content.

!!! tip "What to notice"
    The page updates immediately because the development server watches your files for changes.

## Build the static site

When you are ready to publish, use the `mkdocs build` command to generate the static HTML, CSS, and JavaScript files.

```bash
mkdocs build
```

This creates a `site/` directory containing the complete, self-contained website.

---

You have now created, previewed, and built your first documentation site.

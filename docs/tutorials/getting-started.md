# Getting started

This guide explains how to install Material for MkDocs. You will set up a Python environment, install the required packages, and verify that the `mkdocs` command is ready to use.

## Prerequisites

- Python 3.8+
- `pip`

!!! note "Create a virtual environment first"
    Using a virtual environment is highly recommended to isolate project dependencies.

    === "Linux / macOS"

        ```bash
        python3 -m venv .venv
        source .venv/bin/activate
        ```

    === "Windows"

        ```powershell
        python.exe -m venv .venv
        .venv\Scripts\activate
        ```

## Install Material for MkDocs

The `mkdocs-material` package includes MkDocs, Material for MkDocs, and all of their dependencies. Install it from PyPI using `pip`:

```bash
pip install mkdocs-material
```

## Verify the installation

Check that the `mkdocs` command is available and see which version you installed:

```bash
mkdocs --version
```

!!! bug "Fixing live reload"
    A recent dependency update in MkDocs can prevent the live-reloading from working. This is a known issue (see [#4032](https://github.com/mkdocs/mkdocs/issues/4032)). If you run `mkdocs serve` and your browser does not automatically refresh after you change a file, you most likely need to downgrade the `click` package:

    ```bash
    pip install "click==8.2.1"
    ```

---

You are now ready to create your first site.


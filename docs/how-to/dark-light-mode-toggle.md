# Implementing a Dark/Light Mode Toggle
This page describes how to add a dark and light mode toggle to your Material for MkDocs documentation.

## Color Scheme Preferences

Material for MkDocs supports multiple color schemes, allowing users to choose between light and dark modes based on their preference. You can configure these schemes to automatically respect the users system preference while providing a manual toggle to switch between them.

## Setting up the Color Scheme Toggle

To add a dark and light mode toggle to your documentation, configure the `palette` section in your `mkdocs.yml` file. This section defines the available color schemes and how users can switch between them.

### Basic Configuration

Add the palette configuration to your `theme` section in `mkdocs.yml`:

```yaml
theme:
  name: material
  
  palette:
    - media: "(prefers-color-scheme: light)"
      scheme: default
      primary: white
      accent: blue
      toggle:
        icon: material/weather-night
        name: Dark mode
    - media: "(prefers-color-scheme: dark)"
      scheme: slate
      primary: black
      accent: blue
      toggle:
        icon: material/weather-sunny
        name: Light mode
```
# The Zero-Trust Outpost (`bluetiller.github.io`)

Welcome to the **Zero-Trust Outpost**, a hardened, zero-dependency personal blog built on systems-engineering principles and hosted on GitHub Pages. 

This repository contains raw content and assets for [bluetiller.github.io](https://bluetiller.github.io). It is designed to be lightweight, secure, and easily parseable by both humans and AI agents.

---

## 🤖 Instruction Set for Autonomous Agents

If you are an AI developer agent tasked with editing, maintaining, or adding content to this repository, you **must** adhere to the following rules and structural guidelines.

### 1. File Structure and Naming Conventions
*   **Posts**: Blog posts are written in Markdown (`.md`) and placed directly in the root directory.
*   **Sequential Naming**: Filenames must be three-digit zero-padded sequential integers.
    *   Example: The next post after [002.md](file:///Users/stark/workspaces/antigravity/bluetiller.github.io/002.md) **must** be named `003.md`.
*   **Assets**: All images, figures, and media assets must be placed in the [images/](file:///Users/stark/workspaces/antigravity/bluetiller.github.io/images/) directory.
*   **Static Documents**: Large static PDFs or supplementary papers (e.g., [taxon.pdf](file:///Users/stark/workspaces/antigravity/bluetiller.github.io/taxon.pdf)) must reside in the root directory.

### 2. Front Matter Schema
Every post file must start with a YAML front matter block. The schema is strict and requires the following fields:

```yaml
---
title: "Title of the Post"             # Enclosed in double quotes
date: YYYY-MM-DD                      # Publication date
draft: false                          # Always set to false for production
number: X                             # Integer sequence matching the filename (e.g., 3 for 003.md)
tags: ["Tag1", "Tag2"]                # Array of strings
categories: ["Category"]              # Array of strings
author: "BlueTiller"                   # Must always be "Architect"
description: "A short summary..."     # Short post summary
images: ["/images/your-image.png"]    # Array containing the primary image path
twitter_card: "summary_large_image"  # Static value
---
```

### 3. Content and Formatting Rules
*   **Zero Local JavaScript**: Do not introduce any `npm`, `yarn`, or client-side JavaScript frameworks. The site relies entirely on HTML, CSS, and GitHub Pages' native processing.
*   **Absolute Asset Paths**: Images within posts must be referenced using absolute URLs relative to the domain root (e.g., `![Alt Text](/images/image-name.png)`).
*   **Math Equations**: Write mathematical formulas using LaTeX block (`$$...$$`) or inline (`$...$`) notation.
*   **Link Integrity**: When referencing internal files in descriptions or markdown, use absolute file URLs to keep them accessible to tools.

---

## 🎨 Theme and Styling Configuration

GitHub Pages automatically compiles and serves Markdown files using **Jekyll**. By default, if no custom Jekyll configuration is present, GitHub Pages serves pages as unstyled HTML/Markdown.

### How to Apply a Theme
To enable or change the Jekyll theme for this blog, create or update a `_config.yml` file in the root directory:

#### Option A: Native GitHub Pages Themes (Recommended)
Add the `theme` configuration targeting one of the supported Jekyll themes (e.g., `jekyll-theme-architect` to match the "Architect" persona):
```yaml
theme: jekyll-theme-architect
```

*Supported Native Themes:*
*   `jekyll-theme-architect` (Sleek, developer-focused, top-bar navigation)
*   `jekyll-theme-cayman` (Vibrant header gradients, clean layout)
*   `jekyll-theme-hacker` (Terminal-style dark mode)
*   `jekyll-theme-minimal` (Clean, simple, typography-focused)
*   `jekyll-theme-midnight` (Neon on dark backgrounds)
*   `jekyll-theme-slate` (Professional, cool-toned gray styling)
*   `jekyll-theme-time-machine` (Browser-frame, retro styling)

#### Option B: Remote GitHub-Hosted Themes
If using a theme hosted on GitHub that is not built into Pages natively, use `remote_theme`:
```yaml
remote_theme: pages-themes/architect@v0.2.0
plugins:
  - jekyll-remote-theme
```

### Customizing Styles (CSS/SCSS)
To override theme defaults or apply custom styling without bloated frameworks:
1. Create a file at `/assets/css/style.scss`.
2. Add front matter blocks and import the theme's core styles at the top:
   ```scss
   ---
   ---
   @import "{{ site.theme }}";

   /* Add custom CSS rules here */
   ```

---

## 🛠️ Local Development and Previewing

Before committing and pushing changes, you can preview the site locally using Jekyll:

### Prerequisites
*   Ruby (and Bundler) installed on your system.

### Steps
1. Create a `Gemfile` in the root directory:
   ```ruby
   source "https://rubygems.org"
   gem "github-pages", group: :jekyll_plugins
   ```
2. Run Bundler to install the exact Jekyll versions used by GitHub Pages:
   ```bash
   bundle install
   ```
3. Launch the local development server:
   ```bash
   bundle exec jekyll serve
   ```
4. Open your browser and navigate to `http://localhost:4000`.

---

## 🚀 Deployment

The site is automatically built and deployed via **GitHub Pages** whenever changes are pushed to the `main` branch of the `BlueTiller/bluetiller.github.io` repository. No manual build steps or deployment commands are required.

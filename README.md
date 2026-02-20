# novelsystems.tech

Website for Novel Systems Engineering, LLC.

## Tech Stack
- [Hugo](https://gohugo.io/) static site generator
- Hosted on GitHub Pages
- Deployed automatically via GitHub Actions on push to `main`

## Local Development
**Prerequisites**: Hugo installed ([installation guide](https://gohugo.io/installation/))

```bash
hugo server
```

Site will be available at `http://localhost:1313`

## Deployment
Pushing to `main` triggers the GitHub Actions workflow, which builds the site and deploys to GitHub Pages. The custom domain (`novelsystems.tech`) is configured via `static/CNAME`.

## Structure
```
content/             # Page content in Markdown
themes/novelsystems/  # Custom theme (layouts, CSS)
static/              # Images and static assets
.github/             # GitHub Actions deploy workflow
```

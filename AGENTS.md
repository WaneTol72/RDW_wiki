# AGENTS.md

## Project type
Docusaurus 3.9.2 documentation site (Russian locale, dark mode default)

## Quick commands
- `npm start` - local dev server (port 3000)
- `npm run build` - production build
- `npm run typecheck` - TypeScript check (editor-only config)

## Repository structure
- `/docs/` - main documentation (auto-generated sidebar from filesystem)
- `/blog/` - news/posts (RSS/Atom feeds enabled)
- `/src/` - custom React components/styles
- `/static/` - static assets (images, favicon)

## GitHub workflow
- **All issues**: assign to `WaneTol72`
- **Issue templates**: use `/github/ISSUE_TEMPLATE/*.md` (отчёт-об-ошибке, запрос-фичи, запрос-документации)
- **PRs**: target `master` branch, assign to `WaneTol72` for review
- **Deployment**: GitHub Pages via `npm run deploy`

## Content rules
- Write in Russian (defaultLocale: `ru`)
- Use Docusaurus admonitions: `:::tip`, `:::note`, `:::danger`, `:::info`
- Single H1 per page, include `sidebar_position` in frontmatter
- Add `title` and `description` metadata to doc pages
- Link to style guide: `/docs/site/style_guide.md` contains detailed examples
- Markdown with JSX support (Docusaurus MDX)

## Configuration notes
- Production URL: `https://wanetol72.github.io/RDW_wiki/`
- Edit URLs point to `https://github.com/WaneTol72/rdw-test-docs/tree/master/`
- Theme: dark mode with `dracula` prism theme

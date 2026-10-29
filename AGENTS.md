# AGENTS.md

## Project

- Website for Creative Code Kortrijk (CCK), a new creative coding club in Kortrijk, Belgium.
- Audience: artists, designers, programmers and curious beginners of every skill level who want to explore art and code through workshops, events and meetups.
- Built by Thijs Pattyn, Jarne Huyghe and Milan Demol as the Web 3 "Git Party" assignment, using GitHub Flow (feature branches + pull requests into `main`).
- Design: Figma file "CCK" (based on the Positivus landing page community design); illustrations from pixels.market Doodledo. Links in `README.md`.
- Pages: `/` (index, Hero), `/news`, `/about` (Markdown page). Planned: detail pages per collection item and a `/code` page.

## Stack & constraints

- Astro 7 (`astro@^7.4.0`), ES modules (`"type": "module"`), default `astro.config.mjs` with no integrations.
- TypeScript via `astro/tsconfigs/base` with `strictNullChecks`.
- Content collections in `src/content.config.ts`, using the `glob` loader and `astro/zod` schemas:
  - `workshops` (`title`, `image`), `team` (`name`, `function`, `bio`, `pic`), `foundations` (`title`, `description`).
  - Markdown lives in `src/content/<collection>/`, images in `src/content/<collection>/img/`.
  - A missing frontmatter field fails the build. A `news` collection is planned but not defined yet.
- No CSS framework: plain CSS in `src/styles/` (`reset.css`, `global.css`, `markdown.css`) with custom properties for colors (`--color-primary: #B9FF66`, ...), a fluid type scale (`--fs-*`) and spacing (`--sp-*`).
- Font: Space Grotesk via `@fontsource-variable/space-grotesk`, imported in `src/layouts/Base.astro`.
- Layouts: `Base.astro` (header, main, footer) and `Markdown.astro`. Components are `.astro` files in `src/components/`.
- Starter code has placeholders of the form `##WHAT-SHOULD-BE-HERE##`. Starter files for detail pages and news live in `src/assets/resources/`.
- Markdown is linted with markdownlint (`MD013` and `MD041` disabled).
- Scripts: `npm run dev` (`astro dev --host`), `npm run build`, `npm run preview`.
- Deployment target: GitHub Pages via GitHub Actions (planned).

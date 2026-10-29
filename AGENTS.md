# AGENTS.md

## Project



- Website for **Creative Code Kortrijk (CCK)**, a new creative coding club in Kortrijk, Belgium.
- Audience: people interested in creative coding who want to discover the club's workshops,
  foundations, team and news.
- Built as a team exercise for the Web 3 "Git Party" (Devine), managed with Git and GitHub Flow.
- Team: Thijs Pattyn, Jarne Huyghe, Milan Demol. Three people, each with their own clone and
  agent session, working in the same repository.
- Design: [Figma – CCK](https://www.figma.com/design/Qepjp5d40858EedDBt96Yu/CCK?node-id=403-244&t=3JWw8tYXLN9YaCl4-0),
  based on the [Positivus Landing Page (Community)](https://www.figma.com/design/qW7Tw8hShAFHv5dTmii0oX/Positivus-Landing-Page-Design-(Community)?node-id=25-145&t=LUJ628fwqGa3p4g6-0).
  Illustrations from [Doodledo](https://pixels.market/illustrations/doodledo?c=technology).
- Site sections:
  - **Workshops**: list on `/index`, detail page per workshop (id as dynamic route parameter).
  - **Foundations**: list on `/index`, detail page per foundation (id as dynamic route parameter).
  - **Team**: list on `/index`, detail page per member (id as dynamic route parameter).
  - **News**: all items with full content on `/news`, sorted by date, newest first.
  - **Code**: a `/code` page using the `Code` component, where visitors enter the 4-digit code
    whose digits are hidden across the site. Hiding places are documented in `README.md`.
- Deployed to GitHub Pages, automatically on every change to `main`.

## Stack & constraints

- [Astro](https://astro.build) 7 (`astro.config.mjs` is the default config), npm as package manager.
  - `npm run dev` / `npm start`: dev server; `npm run build`: production build; `npm run preview`.
- Content lives in Astro content collections, defined in `src/content.config.ts` with the `glob`
  loader and Zod schemas:
  - `workshops` (`src/content/workshops`): `title`, `image`.
  - `foundations` (`src/content/foundations`): `title`, `description`.
  - `team` (`src/content/team`): `name`, `function`, `bio`, `pic`.
  - `news` (`src/content/news`): `title`, `date` (`YYYY-MM-DD` in frontmatter, use `z.coerce.date()`).
    Not defined yet; still to be added and exported. Each team member adds one item from
    `src/assets/resources/news`.
  - A missing frontmatter field in a markdown file makes the build fail.
- Components in `src/components` (`Header`, `Hero`, `Footer`, `Workshops`/`WorkshopCard`,
  `Foundations`/`FoundationsCard`, `Team`/`TeamCard`, `ArrowLink`, `Code`), layouts in
  `src/layouts` (`Base`, `Markdown`), pages in `src/pages`.
- Starter files for detail pages and news items are in `src/assets/resources`.
- Placeholders in the code look like `##WHAT-SHOULD-BE-HERE##` and must be replaced with real content.
- No CSS framework: plain CSS in `src/styles` (`reset.css`, `global.css` with custom properties
  for colors, fluid type and spacing, `markdown.css`). Font: Space Grotesk Variable via Fontsource.
- CSS and plain HTML are provided; the work is mainly component logic and content.
- Git workflow: GitHub Flow with one feature branch per task (`feature/<name>`) and pull requests
  into `main`. Conflicts are resolved and pull requests are merged by the team members, not by agents.

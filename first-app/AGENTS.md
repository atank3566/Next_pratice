# Repository Guidelines

## Project Structure & Module Organization
This project follows the Next.js App Router layout. Page-level routes live under `app/`; the root entry is `app/page.tsx` and feature routes (for example, `app/awesome/page.tsx`) should group their assets alongside the page file. Shared styles are defined in `app/globals.css`, while static assets belong in `public/`. Configuration and tooling live at the repo root: `next.config.ts`, `tsconfig.json`, `eslint.config.mjs`, and PostCSS/Tailwind config files. Keep new modules co-located with the feature that owns them to preserve the flat routing model.

## Build, Test, and Development Commands
Run `npm run dev` to start a local server with Turbopack hot reloading. Ship-ready bundles are created with `npm run build`, and `npm run start` serves the compiled output. Use `npm run lint` before every commit; it runs ESLint with the Next.js configuration. Prefer `npm install` for dependency updates so the generated `package-lock.json` stays authoritative.

## Coding Style & Naming Conventions
Author UI in TypeScript React components. Use PascalCase for component files and default exports (`Home`, `AwesomePage`) and camelCase for hooks, utilities, and CSS class helpers. Maintain two-space indentation and single quotes inside JSX class strings as enforced by the existing lint rules. Tailwind v4 utilities are available globally; when custom tokens are needed, extend them in `app/globals.css` rather than ad-hoc inline styles. Keep modules focused—split reusable pieces into lightweight components under `app/(shared)` when they emerge.

## Testing Guidelines
Automated testing is not yet wired in. When adding features, include unit or integration tests using Testing Library + Vitest (preferred) under `app/**/__tests__/` or `tests/`. Mirror the route or component name in the test filename (for example, `page.test.tsx`). Document how to run the suite in the pull request and add the supporting `npm test` script when you introduce the first tests. Until then, rely on `npm run lint` and manual verification in `npm run dev` to catch regressions.

## Commit & Pull Request Guidelines
Use imperative, present-tense commit subjects capped near 50 characters (`feat: add awesome route`). Group related changes per commit and avoid mixing formatting churn with logic. Pull requests should describe the problem, solution, and testing performed; link any relevant issues. Include screenshots or screen recordings for UI changes and mention accessibility checks (keyboard navigation, color contrast) when applicable. Request a review before merging and wait for CI (once available) to pass.

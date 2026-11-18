# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Status

Freshly scaffolded `create-next-app` project (Next.js App Router, TypeScript, Tailwind v4). Only `app/layout.tsx`, `app/page.tsx` and `app/globals.css` exist; there is no app logic, test setup, or data layer yet.

## Commands

- `npm run dev` — dev server at http://localhost:3000
- `npm run build` / `npm run start` — production build / serve
- `npm run lint` — ESLint (flat config in `eslint.config.mjs`, uses `eslint-config-next`)
- No test runner is configured.

## Next.js version caveat

`AGENTS.md` warns that this Next.js (16.x) has breaking changes versus what you may know. Before writing Next.js code, read the relevant guide in `node_modules/next/dist/docs/` and heed deprecation notices.

## Configuration notes

- `next.config.ts` enables `cacheComponents` and `partialPrefetching`, which change caching/rendering semantics for App Router pages and components — consult the bundled docs before writing data fetching or dynamic code.
- Tailwind v4 is wired through Turbopack: `next.config.ts` has a `turbopack.rules` entry running `@tailwindcss/turbopack` on `*.css`. Styling is configured in CSS (`@import "tailwindcss"` and `@theme inline` in `app/globals.css`), not in a `tailwind.config` file.
- Path alias `@/*` maps to the project root (not `src/`); source lives in `app/`.

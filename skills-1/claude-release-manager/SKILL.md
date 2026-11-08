\---

name: claude-release-manager

description: Automates release validation, GitHub Pages subpath base verification, and release tag creation.

\---



\# Release \& Deployment Checklists



When executing release tasks or preparing production builds:



1\. \*\*GitHub Pages Base Path Safety\*\*:

&#x20;  - Ensure `vite.config.ts` sets `base: '/Sunny/'` (or relative `'./'`) for production builds. Never allow absolute `/` paths on GitHub Pages deployment builds.



2\. \*\*Pre-Release Quality Gate\*\*:

&#x20;  - Before recommending `git tag`, automatically run type checks (`npm run typecheck`) and verification builds (`npm run build`).

&#x20;  - Generate release notes categorizing changes into `Features`, `Accessibility \& Security`, and `Bug Fixes`.


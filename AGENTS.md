# AGENTS.md

Project: **shanhai-kitchen** — a Vue 3 + Vite frontend for a restaurant menu site (山海食集).

## Workflow Conventions

- Use Vue single-file components with `<script setup>`; put global styles in `src/styles.css`, not scoped blocks.
- Keep user-facing copy in Chinese (zh-CN); write code and identifiers in English.
- Reuse the design tokens in `:root` (`--ink`, `--cream`, `--coral`, ...) instead of hardcoding colors.
- Keep dish images referenced from `src/App.vue` data (local files under `public/images/` or Unsplash photo IDs).
- Commit with short imperative messages, optionally prefixed (`fix:`, `add`, `update`, `remove`, ...).

## Verification Commands

```sh
npm run dev      # start the local dev server
npm run build    # required check before committing; output goes to dist/
npm run preview  # preview the production build
```

There is no lint or test script — a clean `npm run build` is the required verification.

## Risk Boundaries

- Never hand-edit or commit generated/ignored paths: `dist/`, `node_modules/`, `.idea/`.
- Update `package-lock.json` only through `npm install` when dependencies change.
- The site loads Google Fonts and Unsplash images at runtime; keep those external URLs intact unless a local replacement is provided.
- Keep all source files UTF-8 encoded — this repo is read on a GBK-default Windows shell, so non-UTF-8 saves corrupt Chinese text.
- No secrets, tokens, or credentials belong in this repository.

Owner note: 魅影凌云 likes new technologies.

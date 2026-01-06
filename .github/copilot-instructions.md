<!-- Copilot instructions for local coding agents in this repo -->
# Copilot Instructions — social-bingo

## Development checklist (required)
- [ ] `npm run lint` — fix lint errors
- [ ] `npm run build` — TypeScript + Vite build
- [ ] `npm run test` — run unit tests (Vitest)

Purpose: Minimal, actionable guidance for agents working on this React + Vite SPA.

Highlights
- Entry: [src/main.tsx](src/main.tsx). UI components live in [src/components](src/components).
- Core logic: [src/utils/bingoLogic.ts](src/utils/bingoLogic.ts); questions live in [src/data/questions.ts](src/data/questions.ts).
- State: `useBingoGame` persists to localStorage under key `bingo-game-state` (see `STORAGE_VERSION`). Update the version or write a migration when changing the schema.

Important conventions
- Board is 5×5 with a fixed free center (`FREE_SPACE`). Do not allow toggling or persisting the center square.
- UI flow: `start` → `playing` → `bingo`. Respect `showBingoModal` and `winningLine` to avoid race conditions when updating state.

Agent hints
- Use prompts in [.github/agents](.github/agents) (`quiz-master`, `pixel-jam`, TDD flows) as task templates.
- Run the setup prompt [.github/prompts/setup.prompt.md](.github/prompts/setup.prompt.md) to ensure `dev`, `lint`, and `test` are functional before making changes.

Quick tasks
- Small UI change: edit component, run `npm run dev`, verify in browser preview.
- Logic change: bump `STORAGE_VERSION` in `src/hooks/useBingoGame.ts` and add migration.
- Questions: edit `src/data/questions.ts` (plain strings only).

Quick refs
- `npm run dev` | `npm run build` | `npm run test` | `npm run lint`
- Key files: `src/hooks/useBingoGame.ts`, `src/utils/bingoLogic.ts`, `src/data/questions.ts`

If you want more examples (PR templates, migration snippets, or TDD examples), tell me which area to expand.

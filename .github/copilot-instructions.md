<!-- Copilot instructions for local coding agents in this repo -->
# Copilot Instructions — social-bingo

Purpose: Give AI coding agents the minimal, actionable context they need
to be productive in this React + Vite TypeScript project.

Big picture
- Frontend-only single-page app (React + Vite). Entry is [src/main.tsx](src/main.tsx).
- UI is small and componentized: `StartScreen`, `GameScreen`, `BingoBoard`,
  `BingoSquare`, `BingoModal` under [src/components](src/components).
- Game logic lives in [src/utils/bingoLogic.ts](src/utils/bingoLogic.ts) and
  uses the question bank in [src/data/questions.ts](src/data/questions.ts).
- Persistent client state is saved to localStorage by
  [src/hooks/useBingoGame.ts](src/hooks/useBingoGame.ts) (key: `bingo-game-state`,
  includes a `version` field). Preserve the version or add migrations when
  changing stored schema.

Key developer workflows
- Start dev server: `npm run dev` (Vite). See [package.json](package.json).
- Build: `npm run build` runs `tsc -b && vite build`.
- Tests: `npm run test` (Vitest). Unit tests are under [src/utils](src/utils)
  and [test/setup.ts](test/setup.ts).
- Lint: `npm run lint`.

Project-specific conventions & notes
- Use TypeScript types defined in [src/types/index.ts](src/types/index.ts).
- Board size is fixed to 5x5; center is a free space (`FREE_SPACE` in
  [src/data/questions.ts](src/data/questions.ts)). Generating the board takes
  24 questions + the free space (see `generateBoard()` in
  [src/utils/bingoLogic.ts](src/utils/bingoLogic.ts)).
- Do not toggle or persist the free space; the hook treats it as always
  marked. Refer to `toggleSquare` and `CENTER_INDEX` in
  [src/utils/bingoLogic.ts](src/utils/bingoLogic.ts).
- UI state transitions: `start` → `playing` → `bingo` tracked in
  `useBingoGame`. When adding or changing modal behavior, respect the
  `showBingoModal` flag and `winningLine` handling to avoid race conditions.

Agent / automation hints
- There are curated agent prompts in [.github/agents](.github/agents):
  `quiz-master.agent.md`, `pixel-jam.agent.md`, and TDD agents. Use them
  as examples for specialized agent behavior.
- The lab guide is [.lab/GUIDE.md](.lab/GUIDE.md); it contains workflow
  expectations (dev server running, browser preview open) and links to
  agent prompts.
- The setup prompt is [.github/prompts/setup.prompt.md](.github/prompts/setup.prompt.md)
  — agents should ensure `dev`, `lint`, and `test` tasks run successfully.

What to change and how
- Small UI tweaks: edit the component, run `npm run dev`, and confirm in
  browser preview. Keep changes atomic and reversible.
- Logic or schema changes: update `STORAGE_VERSION` in
  `useBingoGame.ts` and implement a migration when needed.
- Questions dataset: edit [src/data/questions.ts](src/data/questions.ts).
  Strings there are treated as display text — keep them simple.

What not to do
- Do not change persisted schema without bumping `version` or providing a
  clear migration path — otherwise users may get invalid local state.
- Avoid heavy refactors across many files in a single agent run. Prefer
  small, test-covered steps (TDD agents exist in [.github/agents](.github/agents)).

Quick references
- Dev server: `npm run dev`
- Build: `npm run build`
- Test: `npm run test`
- Lint: `npm run lint`
- Key files: [src/hooks/useBingoGame.ts](src/hooks/useBingoGame.ts),
  [src/utils/bingoLogic.ts](src/utils/bingoLogic.ts), [src/data/questions.ts](src/data/questions.ts)

If anything here is unclear or you want me to include additional examples
(e.g., common PR labels, branch naming, or test snippets), tell me what to
add and I'll update this file.

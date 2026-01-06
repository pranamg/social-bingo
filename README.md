# Social Bingo — Soc Ops

Welcome to Social Bingo: a playful, customizable icebreaker for teams and meetups. Spin up the app, generate a board, and start finding teammates who match the prompts — get five in a row to win.

Why you'll love it
- Fast setup: runs locally with one command.
- Customizable questions: tailor the board to your event or team culture.
- Lightweight: single-page React + Vite app that deploys to GitHub Pages.

Get started

Prerequisites:
- Node.js 22 or higher

Quick start:

```bash
npm install
npm run dev
```

Build for production:

```bash
npm run build
```

Features
- 5×5 bingo board with a fixed free center.
- Persisted game state so players can return to their board.
- Simple theming and question set stored in `src/data/questions.ts` for quick edits.

Contribute
- Update the question list at `src/data/questions.ts` to add new themes.
- Open issues or PRs with ideas, themes, or accessibility improvements.

Resources
- Lab guide and developer instructions: [.lab/GUIDE.md](.lab/GUIDE.md)

License
- MIT

Have fun! If you want, I can polish the start screen or create a theme selector next.

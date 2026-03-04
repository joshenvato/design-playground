# Design Playground

A Storybook starter kit for scaffolding UI pages with the Envato Design System. Open this repo in Cursor and use the included layout examples as starting points — describe the page you want to Cursor and it will scaffold a new story for you.

## Prerequisites

- Node.js >= 22
- A GitHub personal access token with `read:packages` scope (to install `@envato/design-system` from GitHub Packages)

## Setup

```bash
# 1. Configure your GitHub token for the npm registry
export GITHUB_TOKEN=your_token_here
printf "//npm.pkg.github.com/:_authToken=%s\n@envato:registry=https://npm.pkg.github.com\n" "$GITHUB_TOKEN" >> .npmrc

# 2. Install dependencies
# --legacy-peer-deps is required because react-slider declares React 16–18 as a peer
npm install --legacy-peer-deps

# 3. Start Storybook
npm run storybook
```

Storybook opens at [http://localhost:6006](http://localhost:6006) (or 6007 if 6006 is already in use).

## Layout examples

Three ready-to-use page layouts live in `app/examples/`. Open any of them in Cursor as a reference when scaffolding a new page.

| Story | File | Use when… |
|---|---|---|
| **App Shell** | `app/examples/AppShell.stories.tsx` | Any page with a sidebar nav |
| **Content Grid** | `app/examples/ContentGrid.stories.tsx` | Browse, search results, galleries |
| **Settings Page** | `app/examples/SettingsPage.stories.tsx` | Forms, preferences, account pages |

## Adding a new page

1. Copy the closest example from `app/examples/` into `app/routes/your-page/`
2. Open it in Cursor and describe the UI you want — paste in a Figma URL or describe the layout in plain English
3. Run `npm run storybook` and check your story at [http://localhost:6006](http://localhost:6006)

Storybook auto-discovers any file matching `app/**/*.stories.tsx`.

## What's included

### Design System
- Full Envato Design System with light/dark mode toggle (toolbar top-right)
- PolySans font family
- Icon sprite

### Layout components (from `@envato/design-system/components`)
- `Box` — the base building block for all layout and spacing
- `Stack` — vertical layout with spacing tokens
- `Columns` — responsive grid with `minColumnWidth`
- `Bleed` — escape a parent's padding (needed for fullscreen layouts)
- `Hidden` — show/hide content at responsive breakpoints
- `Text` — typography (variants: `title-1`–`title-4`, `subheading`, `body-large`, `body-small`, `label-large`, `label-small`, `micro`)
- `Button`, `IconButton` — actions

### Navigation
- `app/components/Navigation/` — collapsible sidebar (drawer on narrow, panel on wide)
- `app/components/Navigation/storyData.ts` — ready-made nav item and accordion fixtures

### Story infrastructure (applied globally — no setup needed per story)
- React Router memory router
- All app context providers
- i18n with locale switcher (EN, ES, PT-BR, DE, FR)
- Light/dark color scheme switcher
- Accessibility checks via a11y addon

## Build for static hosting

```bash
npm run build-storybook
```

Output goes to `storybook-static/`.

# Integrations Page

A modern, fully client-side **app integrations directory** — think a Zapier-style catalog where users can browse, search, and filter hundreds of third-party app integrations by category. Built with Next.js and shadcn-style UI components.

> Built by Girish Lade — https://ladestack.in

## What it does

The app renders a searchable grid of integration cards (name, description, category, icon) with:

- **Live search** across integration names and descriptions
- **Category filter sidebar** (CRM, marketing, payments, productivity, communication, developer tools, and more)
- **Pagination** (30 items per page) with page controls
- **Integration detail cards** with icons from Lucide and color-coded categories

All data is local (`app/data/integrations.ts`) — no backend, no API calls, no login required.

## Features

- Instant client-side search with memoized filtering
- Category sidebar filter with counts
- Responsive integration card grid
- Paginated browsing (30 per page)
- Dark-mode-ready theming via `next-themes`
- Built on Radix UI primitives (dialog, dropdown, tabs, toast, etc.)
- Fully static-exportable — deploys to any static host

## Tech stack

- **Framework:** Next.js 15 (App Router) — static export (`output: 'export'`)
- **UI:** React 19, Tailwind CSS 3.4, Radix UI, shadcn-style components
- **Icons:** lucide-react
- **Charts:** recharts (available for analytics views)
- **Forms:** react-hook-form + zod
- **Fonts:** Geist
- **Language:** TypeScript

## Quick start

### Prerequisites

- Node.js 18+ (20 recommended)
- npm, pnpm, or yarn

### Install & run

```bash
# install dependencies
npm install
# or
pnpm install

# start dev server
npm run dev
```

Open http://localhost:3000 — the integrations directory lives at `/integrations`.

### Build (static)

```bash
npm run build
```

The build produces a fully static site in `out/` (static export). Serve it with any static server:

```bash
npx serve out
```

## Project structure

```
app/
├── layout.tsx                      # root layout (fonts, theme provider)
├── globals.css                     # Tailwind + global styles
├── data/
│   └── integrations.ts             # integration catalog data (categories, icons)
└── integrations/
    ├── page.tsx                    # main directory page (search/filter/pagination)
    └── components/
        ├── CategoryFilter.tsx       # sidebar category list
        ├── SearchBar.tsx            # search input
        ├── IntegrationGrid.tsx      # card grid
        ├── IntegrationCard.tsx      # single card
        └── Pagination.tsx          # pager
components/
├── ui/                             # shadcn-style primitives (button, card, input…)
└── theme-provider.tsx
lib/
└── utils.ts                        # class-name helpers
public/                             # static assets
styles/                             # extra styles
```

## Customizing the catalog

Edit `app/data/integrations.ts` — add entries to the `integrations` array:

```ts
{ id: "slack", name: "Slack", description: "...", category: "Communication", icon: MessageSquare }
```

Categories are derived from the `categories` export in the same file.

## Environment variables

None required. The app is fully static and runs without any secrets or backend services.

## Deployment

Any static host works: GitHub Pages, Cloudflare Pages, Netlify, Vercel.

This repo also ships as a static export on GitHub Pages — see the repo's Website field.

> Note: `next.config.mjs` uses `basePath: '/integrations-page'` for the GitHub Pages subpath deploy. If you deploy to a root domain or Vercel, remove the `basePath` line.

## Notes

- Generated originally with v0.app and refined for static hosting.
- Next.js 15.2.8 (patched against CVE-2025-55182 / React2Shell).
- `next-themes` provides dark mode; toggle via your own theme switcher.

---

Built with ❤ by [Girish Lade](https://github.com/girishlade111) — [ladestack.in](https://ladestack.in)

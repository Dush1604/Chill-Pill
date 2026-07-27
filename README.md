# Chill Pill

A medication reminder and calendar web application that helps users (and their families) stay on top of medication schedules.

Created by Dushyant Saini, Jack Koskie, and Eric Du for ICS4U.

## Features

- Track when medications need to be taken, with a calendar view
- Monitor remaining medication supply and get reminded to refill
- View a family member's medication history to help them stay up to date
- Google OAuth sign-in
- Multi-language support (English, Spanish, French, Traditional Chinese, Simplified Chinese)

## Tech stack

[SvelteKit](https://kit.svelte.dev/) · TypeScript · [Drizzle ORM](https://orm.drizzle.team/) · Cloudflare D1 (SQLite) · Cloudflare Pages/Workers · Tailwind CSS + [daisyUI](https://daisyui.com/) · [Paraglide](https://inlang.com/m/gerre34r/library-inlang-paraglideJs) for i18n

## Getting started

### 1. Install dependencies

```bash
npm install
```

### 2. Set up environment variables

Copy `.env.example` to `.env` and fill in your own values:

```bash
cp .env.example .env
```

You'll need a [Google OAuth client ID/secret](https://console.cloud.google.com/apis/credentials) for sign-in to work locally. The Cloudflare variables are only needed for production database migrations.

### 3. Set up the local database

This project uses Cloudflare D1 (SQLite) via Drizzle ORM. For local development, Wrangler emulates D1 automatically:

```bash
npm run dev
```

To generate or run migrations after changing the schema (`src/lib/db/schema/`):

```bash
npm run db:generate
npm run db:migrate
```

You can also inspect the database visually with:

```bash
npm run db:studio
```

### 4. Run the dev server

```bash
npm run dev
```

The app will be available at `http://localhost:5173`.

## Other useful scripts

| Command | Description |
|---|---|
| `npm run build` | Build for production |
| `npm run preview` | Build and preview locally via Wrangler |
| `npm run deploy` | Build and deploy to Cloudflare Pages |
| `npm run check` | Type-check the project |
| `npm run lint` | Check formatting and lint rules |
| `npm run format` | Auto-format the codebase with Prettier |

## Project structure

```
src/
├── lib/
│   ├── auth/       # Google OAuth + session handling
│   ├── db/schema/  # Drizzle schema: users, medications, history, family
│   └── utils/
├── routes/
│   ├── dashboard/  # Main medication overview
│   ├── calendar/   # Calendar view of medication schedule
│   ├── history/    # Medication history log
│   ├── settings/   # User + family settings
│   └── login/      # Google OAuth login flow
messages/           # i18n translation files (en, es, fr, zh-Hant, zh-cn)
drizzle/            # Generated SQL migrations
```

## Known bugs

None currently tracked.

## Support

For support, please open a GitHub issue or pull request.

## License

MIT — see [LICENSE](LICENSE).

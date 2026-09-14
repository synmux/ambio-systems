# Ambio

> _Something is listening._

A teaser landing page featuring an animated WebGL particle background, dark/light theme support with [Catppuccin](https://catppuccin.com/) colors, and email subscription capture.

## Tech Stack

- **[Nuxt 4](https://nuxt.com/)** – Vue 3 meta-framework with SSR/SSG
- **[Tailwind CSS v4](https://tailwindcss.com/)** – Utility-first CSS
- **[DaisyUI v5](https://daisyui.com/)** – Component library for Tailwind
- **[Three.js](https://threejs.org/)** – WebGL particle effects
- **[Cloudflare D1](https://developers.cloudflare.com/d1/)** – SQLite database with Drizzle ORM
- **[Node.js](https://nodejs.org/)** – Local JavaScript runtime (version pinned in `mise.toml`)
- **[pnpm](https://pnpm.io/)** – Package manager (version pinned in `package.json`)

## Quick Start

Install Node.js using the version in `mise.toml` and pnpm using the `packageManager` version in `package.json`.

```bash
# Install dependencies
pnpm install

# Build and start the local Cloudflare development server
pnpm run dev
```

Open the URL printed by Wrangler (normally [http://localhost:8787](http://localhost:8787)) to view the site. `pnpm run dev` builds the application before starting Wrangler; rerun it after source changes to rebuild.

Use pnpm for dependency changes and commit updates to `pnpm-lock.yaml`. Dependency build permissions and installation settings are configured in `pnpm-workspace.yaml`.

`pnpm install` also runs the post-install scripts to prepare Nuxt, generate Cloudflare types, and format the repository.

## Scripts

| Command                      | Description                                  |
| ---------------------------- | -------------------------------------------- |
| `pnpm run dev`               | Build and start Wrangler locally             |
| `pnpm run build`             | Build for production                         |
| `pnpm run generate`          | Generate static site                         |
| `pnpm run deploy`            | Build and deploy to Cloudflare               |
| `pnpm run cf-typegen`        | Generate Cloudflare Worker types             |
| `pnpm run format`            | Format code using Prettier and Trunk         |
| `pnpm run lint`              | Run Trunk checks across all files            |
| `pnpm run lint:types`        | Run TypeScript checks without emitting files |
| `pnpm run db:generate`       | Generate DB migrations                       |
| `pnpm run db:migrate:local`  | Apply migrations to local D1                 |
| `pnpm run db:migrate:remote` | Apply migrations to remote D1                |
| `pnpm run db:studio`         | Open Drizzle Studio                          |

## Theming

The site supports dark and light themes using the Catppuccin color palette:

- **Dark** – Catppuccin Macchiato
- **Light** – Catppuccin Latte

Theme preference is persisted to localStorage and respects system preferences on first visit. The WebGL background particles also update their colors when the theme changes.

## Linting

This project uses [Trunk](https://trunk.io/) for linting and formatting:

```bash
pnpm run lint        # Run all linters
pnpm run lint:types  # Check TypeScript types
pnpm run format      # Auto-format code
```

## Project Structure

```plaintext
app/
├── app.vue           # Root layout with WebGL background
├── components/       # Vue components (EmailForm, ThemeToggle, etc.)
├── composables/      # Shared state (useTheme)
├── plugins/          # Client-side plugins
└── assets/css/       # Tailwind + DaisyUI theme configuration
server/
├── api/              # Nitro server routes (subscribe, unsubscribe, admin)
├── database/         # Drizzle schema definitions
└── utils/            # Server utilities (auth, rate limiting, db)
public/
└── images/           # Static assets
drizzle/              # Database migrations
```

## License

[MIT](LICENSE) © 2025 Dave Williams

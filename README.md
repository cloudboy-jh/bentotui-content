# bentotui-content

Marketing site and docs content for BentoTUI, built with Astro.

## Stack

- Astro 5
- Bun / Node
- Cloudflare Wrangler

## Local Development

```bash
bun install --frozen-lockfile
bun run dev
```

## Build

```bash
bun run build
```

Clean build:

```bash
npm run build:clean
```

## Deploy

Recommended (Pages):

```bash
npm run deploy
```

Explicit main branch deploy:

```bash
npm run deploy:prod
```

`wrangler.toml` is configured so Worker-style `wrangler deploy` can still find static assets if needed.

## Scripts

- `dev` - start Astro dev server
- `build` - production build
- `clean` - remove `.astro` and `dist`
- `build:clean` - clean then build
- `preview` - preview production build
- `deploy` - clean build + `wrangler pages deploy`
- `deploy:prod` - same deploy pinned to `main`
- `lock:frozen` - install with frozen lockfile

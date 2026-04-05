# Folio

A **portFOLIO website** built with [Astro](https://astro.build/). Almost everything visitors see—welcome text, navbar, social links, CV timeline, project cards, images—comes from [Sanity](https://www.sanity.io/). You **connect your Sanity project, add content in the studio, and go**: no need to edit page markup for routine updates.

## What you get

- **Front end (repo root):** static Astro site that fetches content at **build** time.
- **CMS (`Backend/`):** Sanity Studio with schemas for each section of the site.

Presentation stays in code; copy, media, and structure of lists live in the CMS.

## Quick start: connect Sanity and go

1. **Create a Sanity project** at [sanity.io](https://www.sanity.io/) (or use an existing one) and note the **project ID** and **dataset** name (often `production`).

2. **Point the studio and site at that project**
   - In **`Backend/sanity.config.ts`** and **`Backend/sanity.cli.ts`**, set `projectId` and `dataset` to match your project.
   - In the **repository root**, create a `.env` file (next to the root `package.json`):

   ```env
   SANITY_PROJECT_ID=your_project_id
   SANITY_DATASET=production
   SANITY_API_VERSION=2024-01-01
   ```

   Use the same `projectId` and `dataset` everywhere so the studio and the Astro build read the same data.

3. **Install and run the studio** (to edit content):

   ```bash
   cd Backend
   npm install
   npm run dev
   ```

4. **Install and run the site** (in a second terminal, from the repo root):

   ```bash
   npm install
   npm run dev
   ```

5. Fill in documents in the studio, then refresh or rebuild the site. For production, run `npm run build` at the root; output is in `dist/`.

## Repo layout

| Path       | Role                                                |
|------------|-----------------------------------------------------|
| Root       | Astro portfolio site                                |
| `Backend/` | Sanity Studio + schema definitions (`schemaTypes/`) |
| `src/`     | Frontend                                            |

## Hosting

- **Site:** any host that builds Astro and serves `dist/` (e.g. [Vercel](https://vercel.com/), [Netlify](https://www.netlify.com/), [Cloudflare Pages](https://pages.cloudflare.com/)). Set the same `SANITY_*` variables as in your local `.env`.
- **Studio:** deploy from `Backend/` with [Sanity’s deployment docs](https://www.sanity.io/docs/deployment), or keep running `npm run dev` locally when you edit content.

The deployed site only needs static hosting; Sanity serves the content API.

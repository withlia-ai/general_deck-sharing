# Decks on Vercel

Each subfolder here is one deck, deployed independently to Vercel as a static
site. A deck is just an `index.html`, its `media/`, and a `vercel.json`.

**Deploys are manual and separate from GitHub.** Pushing to this repo does
**not** deploy anything — GitHub is only source-of-truth and history. You go
live by running the Vercel CLI from a deck's folder (see below). This is
intentional: it keeps "what's committed" and "what's live" decoupled, so you
control exactly when a deck publishes.

## Decks

| Folder | Deck | Live URL |
|--------|------|----------|
| `prekickoff/` | LIA × HelloFresh pre-kickoff | https://lia-hellofresh-prekickoff.vercel.app |

## Deploy a deck

Prerequisite: a Vercel account you're logged into. No global install needed —
`npx vercel` works (a global `npm i -g vercel` is fine too if you prefer).

From inside the deck's folder:

```bash
cd prekickoff
npx vercel --prod          # deploys just this folder to production
```

- The **first** deploy from a new folder asks which Vercel project to use —
  pick the existing one or create a new project. Vercel remembers the link in a
  gitignored `.vercel/` folder, so later deploys are just `npx vercel --prod`.
- Drop `--prod` for a throwaway preview URL instead of going live.
- Check who you're logged in as with `npx vercel whoami`; switch with
  `npx vercel login`.

## Add a new deck

1. Copy the template:
   ```bash
   cp -r _template my-deck-name      # e.g. cp -r _template q3-review
   ```
2. Replace `index.html` with your deck's HTML.
3. Put videos/images in that folder's `media/` and reference them with
   **relative paths** — `src="media/clip.mp4"`, never `../media/`. Each deck
   carries its own media so it deploys on its own.
4. Deploy it with the steps above.
5. Add a row to the **Decks** table here with its live URL.

## Not here

The **investor deck** is not in this repo. It lives in `general_pitch-decks`
(`investor-deck-v5.html`) and is served at `withlia.ai/deck/` via AWS S3 +
CloudFront — see that repo's `DEPLOY.md`. Leave it there; don't duplicate it.

# Decks on Vercel

Each subfolder here is one deck, deployed independently to Vercel as a static
site. A deck is just an `index.html`, its `media/`, and a `vercel.json`.

## Decks

| Folder | Deck | Live URL |
|--------|------|----------|
| `prekickoff/` | LIA × HelloFresh pre-kickoff | https://lia-hellofresh-prekickoff.vercel.app |

## Add a new deck

1. Copy the template:
   ```bash
   cp -r _template decks-new-name      # e.g. cp -r _template q3-review
   ```
2. Replace `index.html` with your deck's HTML.
3. Put videos/images in that folder's `media/` and reference them with
   **relative paths** — `src="media/clip.mp4"`, never `../media/`. Each deck
   carries its own media so it deploys on its own.
4. Deploy (see below).

## Deploy a deck

From inside the deck's folder:

```bash
cd prekickoff
vercel --prod            # deploys just this folder to its Vercel project
```

The first time in a new folder, Vercel asks which project to link it to — pick
or create one, and it remembers the link (stored in a gitignored `.vercel/`).

### Optional: push-to-deploy

To make `git push` deploy automatically, connect this repo to the deck's Vercel
project in the Vercel dashboard and set the project's **Root Directory** to the
deck's folder (e.g. `prekickoff`). After that, pushes to `main` redeploy that
deck with no CLI. This is a one-time per-deck setup in the dashboard.

## Not here

The **investor deck** is not in this repo. It lives in `general_pitch-decks`
(`investor-deck-v5.html`) and is served at `withlia.ai/deck/` via AWS S3 +
CloudFront — see that repo's `DEPLOY.md`. Leave it there; don't duplicate it.

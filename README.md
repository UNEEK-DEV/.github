<<<<<<< HEAD
# UNEEK-DEV / .github
||||||| parent of c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)
# UNEEK-DEV · `.github`
=======
# `UNEEK-DEV/.github` — the org profile system
>>>>>>> c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)

<<<<<<< HEAD
Org-level GitHub configuration for **UNEEK-DEV** — profile README, discussion templates, and community defaults.
||||||| parent of c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)
Org-level assets and the **GitHub organization profile** for [UNEEK-DEV](https://github.com/UNEEK-DEV).
=======
This repo renders the public page at **[github.com/UNEEK-DEV](https://github.com/UNEEK-DEV)**.
It is **data-driven**: the board you see is generated from JSON, so adding a property or
flipping a status is a one-line edit — never hand-editing the rendered README.
>>>>>>> c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)

<<<<<<< HEAD
## What lives here
||||||| parent of c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)
## What shows on the org page

The profile lives at **`profile/README.md`** — that's what renders on [github.com/UNEEK-DEV](https://github.com/UNEEK-DEV).

**THE ARCHITECT** · **ONYX** · NEEKMODE / UNEEK-DEV · client build board.

## Assets
=======
## How it fits together

```
data/profile.json        # brand, tagline, the two principals, the law, footer
data/properties.json     # THE ROSTER — one object per property (source of truth)
templates/profile.tpl.md # the layout (GitHub-safe HTML + tokens)
scripts/build-profile.mjs# renders template + data  ->  profile/README.md
assets/                  # gold wordmark SVGs (dual-theme) + portraits + font
profile/README.md        # GENERATED — what renders on the org page. Do not edit.
.github/workflows/       # rebuilds profile/README.md automatically on push
```

## Add a property (the whole point)

1. Open **`data/properties.json`** and add one object to `items`:
   ```json
   { "name": "New Thing", "domain": "newthing.com", "url": "https://newthing.com",
     "tag": "Studio", "status": "building", "repo": "UNEEK-DEV/new-thing" }
   ```
   `status` is `live` · `building` · `soon`. `repo` is `owner/name` or `null`.
2. Commit and push. The Action rebuilds `profile/README.md` for you.
   *(Local preview: `node scripts/build-profile.mjs`.)*
>>>>>>> c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)

<<<<<<< HEAD
| Path | Purpose |
|:--|:--|
| `profile/README.md` | Public org profile shown on [github.com/UNEEK-DEV](https://github.com/UNEEK-DEV) |
| `DISCUSSION_TEMPLATE/` | Starter templates for org discussions |
| `ISSUE_TEMPLATE/` | Structured issue intake |
| `FUNDING.yml` | Sponsor button links (GitHub · Ko-fi · custom) |
| `DONATE.md` | Crypto wallets + fiat setup guide (replace placeholders) |
| `CODEOWNERS` | Default reviewers for meta-repo changes |
||||||| parent of c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)
| Path | Purpose |
|--|--|
| `assets/architect.webp` | Niko — The Architect |
| `assets/onyx.webp` | Onyx — Bengal · studio enforcer |
| `assets/the-architect.svg` | Gold header banner |
| `assets/fonts/MBF-Royal.otf` | Profile typography |
| `assets/fonts/MBF-Royal.ttf` | Profile typography (fallback) |
=======
## Edit branding or the principals
>>>>>>> c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)

<<<<<<< HEAD
## Core GitHub accounts
||||||| parent of c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)
## Edit the profile
=======
Change **`data/profile.json`** (brand line, tagline, the ARCHITECT / ONYX captions, the
house-rules plaque, footer), then rebuild. Wordmarks live in `assets/*.svg` and use a gold
gradient baked into the SVG — they render identically on **both** GitHub themes (no `<style>`
blocks, which GitHub strips).
>>>>>>> c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)

<<<<<<< HEAD
- **[neekmode](https://github.com/neekmode)** — The Architect · builder identity
- **[THE-SAVAGE-STUDIO](https://github.com/THE-SAVAGE-STUDIO)** — core studio repos · OS · templates
- **[UNEEK-DEV](https://github.com/UNEEK-DEV)** — client delivery · private builds
||||||| parent of c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)
1. Change `profile/README.md`
2. Commit + push to `main`
3. Org page updates in ~1 min
=======
## Commands
>>>>>>> c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)

<<<<<<< HEAD
## Surfaces

- [savage.ceo](https://savage.ceo) — The Architect's desk
- [savagestud.io](https://savagestud.io) — Savage Studio

## Discussions

Discussions are open on this repo. Use them for build inquiries, studio updates, and client coordination — not for code bugs in individual project repos.

→ [Open a discussion](https://github.com/UNEEK-DEV/.github/discussions/new/choose)

## Donate

Support links live in `FUNDING.yml` (repo Sponsor button) and `DONATE.md` (full wallet list).

→ [Donate setup guide](./DONATE.md)
||||||| parent of c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)
Built by **[NEEKMODE](https://github.com/UNEEK-DEV)** / **[UNEEK-DEV](https://github.com/UNEEK-DEV)**.
=======
```bash
node scripts/build-profile.mjs          # rebuild the profile
node scripts/build-profile.mjs --ping   # also probe each domain; demote dead 'live' to 'soon'
node scripts/build-profile.mjs --check  # CI guard: exit 1 if the README is stale
```

## Renaming the org (UNEEK-DEV → THE-ARCHITECT)

This page is **rename-safe by design**: assets use relative paths and the org handle is
injected from `data/profile.json` (one place). After GitHub renames the org:

1. Set `"org"` in `data/profile.json` to the new handle, rebuild, commit.
2. GitHub keeps clone/fetch/push and most web links working via redirects. Repo `Source ↗`
   links redirect automatically. **The old `github.com/UNEEK-DEV` profile link does not redirect.**
3. Vercel tracks repos by immutable ID — **builds keep working**; no re-import needed. If any
   project stops auto-deploying, Project → Settings → Git → Disconnect → Reconnect (or
   `vercel git connect`) from the Vercel **team** that owns the org.
4. Update local clones: `git remote set-url origin <new-url>` (optional; redirects cover it).
5. Optional: claim the freed `UNEEK-DEV` name with an empty org to prevent squatting.

---

Built by **NEEKMODE** / **UNEEK-DEV**.
>>>>>>> c6ec51f (feat: overhaul org profile structure and assets for UNEEK-DEV)

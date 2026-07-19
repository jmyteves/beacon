# Push BEACON to github.com/jmyteves/beacon (full replacement)

You're replacing the **entire** contents of the existing `beacon` repo (which held the old switch-model explainer) with this pan-cancer tool. Do it from VSCode / your terminal — the sandbox can't push.

The deployable folder is:
`beacon_2/pancancer_beacon/`  ← everything in here becomes the repo root.

---

## Already pushed once? Use this to UPDATE + drop the now-ignored .md files

If the repo is already live and you just want to push the latest changes (logo, About text, footer credit) **and** stop tracking the manuscript/notes `.md` files (now covered by `.gitignore`, except `README.md`):

```bash
# in your local clone of the beacon repo
SRC="$HOME/Library/CloudStorage/GoogleDrive-jmyteves@gmail.com/My Drive/repos/beacon_2/pancancer_beacon"
cp -R "$SRC"/. .                       # refresh with the latest files (index.html, assets/, .gitignore, ...)

# stop tracking the .md files that are now gitignored (keeps README.md; keeps local copies on disk)
git rm --cached -r --ignore-unmatch "*.md"
git add README.md                      # re-add the one .md we DO want tracked
git add -A                             # stage everything else (index.html, assets/beacon_logo.png, ...)

git commit -m "Add logo + About section + author credit; stop tracking manuscript .md files"
git push origin main                   # or 'master'
```

`git rm --cached` removes the files from the repo index (so they disappear from GitHub) **without deleting your local copies**. After this, `PUSH_INSTRUCTIONS.md`, `manuscript/*.md`, etc. stay on your machine but are no longer published.

---

## Option A — clone, wipe, replace (recommended, keeps git history)

```bash
# 1. Clone the existing repo somewhere OUTSIDE the beacon_2 folder
cd ~/Desktop        # or anywhere convenient
git clone https://github.com/jmyteves/beacon.git
cd beacon

# 2. Remove ALL tracked files (keeps the .git history)
git rm -rf .

# 3. Copy in the new contents (adjust the source path to your Drive)
SRC="$HOME/Library/CloudStorage/GoogleDrive-jmyteves@gmail.com/My Drive/repos/beacon_2/pancancer_beacon"
cp -R "$SRC"/. .

# 4. Commit and push
git add -A
git commit -m "Replace with pan-cancer BEACON co-driver Navigator (792 BDPs × 14 cancers)"
git push origin main        # or 'master' if that's the default branch
```

## Option B — fresh history (simpler, discards old commits)

```bash
SRC="$HOME/Library/CloudStorage/GoogleDrive-jmyteves@gmail.com/My Drive/repos/beacon_2/pancancer_beacon"
cd "$SRC"
git init
git add -A
git commit -m "Pan-cancer BEACON co-driver Navigator"
git branch -M main
git remote add origin https://github.com/jmyteves/beacon.git
git push -f origin main      # -f overwrites remote history
```

---

## Enable GitHub Pages (one-time)

1. On GitHub: **Settings → Pages**
2. **Source:** Deploy from a branch
3. **Branch:** `main`, folder **`/ (root)`** → Save
4. Wait ~1 min. The tool goes live at:
   **https://jmyteves.github.io/beacon/**

`index.html` is at the repo root and `.nojekyll` is included, so Pages serves it as-is (no build step, no Jekyll processing).

---

## Verify after deploy
- Open https://jmyteves.github.io/beacon/ — the cancer picker should list 14 types.
- Switch cancer (e.g. CRC → Thyroid): the co-driver quadrant and table should change, and PLAGL2–POFUT1 should flip from co-driver (CRC) to no-clear (thyroid).
- Toggle **"expansion pack only"** — the table should shrink to the 287-BDP set.

## Notes
- The repo is **self-contained**: `index.html` embeds the full prediction grid inline, so it works offline and needs no server.
- `notebooks/figures/` is gitignored — a local notebook re-run won't add scratch files to the repo.
- Total repo size ≈ 6.8 MB (well within GitHub Pages limits, which are ~1 GB).

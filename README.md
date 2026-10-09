# Security Materials

Live site: https://zagran.github.io/security-materials/

The site is a single static page, `index.html`, served by GitHub Pages from the root of the `main` branch.

## Update the site

Edit `index.html`, then commit and push to `main`:

```sh
git add index.html
git commit -m "Update lecture plan"
git push origin main
```

GitHub rebuilds the site on every push to `main`, usually within a minute or two. Check progress under the repo's **Actions** tab, or:

```sh
gh api repos/zagran/security-materials/pages/builds/latest -q .status
```

To force a rebuild without a new commit:

```sh
gh api -X POST repos/zagran/security-materials/pages/builds
```

## Initial setup (one time)

Already done for this repo; kept here for reference.

1. Make the repo public (free GitHub plans only serve Pages from public repos).
2. Push `index.html` to the root of `main`.
3. Enable Pages, either in **Settings → Pages** (Source: *Deploy from a branch*, Branch: `main`, folder `/ (root)`), or with the GitHub CLI:

   ```sh
   gh api -X POST repos/zagran/security-materials/pages \
     -f "source[branch]=main" -f "source[path]=/"
   ```

4. Wait for the first build; the site appears at `https://zagran.github.io/security-materials/`.

Note: everything in this repo is publicly visible once Pages is on.

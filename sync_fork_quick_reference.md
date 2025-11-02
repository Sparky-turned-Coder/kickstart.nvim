# Sync Your Fork with Upstream (Quick Reference)

This mini‑guide shows how to keep your fork updated with the original
Kickstart repo.

------------------------------------------------------------------------

## ✅ One‑Time Setup: Add Upstream Remote

Do this **once** to connect to the original Kickstart repository:

``` bash
git remote add upstream https://github.com/nvim-lua/kickstart.nvim.git
```

Verify:

``` bash
git remote -v
```

You should see:

    origin    git@github.com:YOUR-USERNAME/kickstart.nvim.git (fetch)
    upstream  https://github.com/nvim-lua/kickstart.nvim.git (fetch)

------------------------------------------------------------------------

## 🔄 Update Your Fork (Use Regularly)

1.  Fetch the latest changes from upstream:

``` bash
git fetch upstream
```

2.  Switch to your main branch:

``` bash
git checkout main
```

3.  Merge upstream changes into your main branch:

``` bash
git merge upstream/main
```

If there are no conflicts, your main is now up to date.

------------------------------------------------------------------------

## 🚀 Push Updated Main Back to Your Fork

``` bash
git push origin main
```

Your fork on GitHub is now synced!

------------------------------------------------------------------------

### 📌 Tips

-   **Never work on `main`** --- always create a feature branch for your
    changes.
-   If merge conflicts appear, resolve them in your editor, then:

``` bash
git add .
git commit
```

You're good to go!

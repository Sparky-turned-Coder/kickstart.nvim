# Git + SSH Setup for Neovim Config (Beginner-Friendly Guide)

This guide walks you through setting up SSH for GitHub and pushing
changes to your Neovim (Kickstart) config.

------------------------------------------------------------------------

## ✅ 1. Check if You Already Have SSH Keys

Run this in your terminal:

``` bash
ls -al ~/.ssh
```

If you see `id_ed25519` and `id_ed25519.pub`, you already have keys. If
not, you'll create them in the next step.

------------------------------------------------------------------------

## 🔐 2. Create a New SSH Key (If Needed)

``` bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```

When asked for a file location, press **Enter** to accept the default.

------------------------------------------------------------------------

## 🚀 3. Start the SSH Agent and Add Your Key

``` bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_ed25519
```

You should see: `Identity added`

------------------------------------------------------------------------

## 🌐 4. Add Your Public Key to GitHub

1.  Display your public key:

    ``` bash
    cat ~/.ssh/id_ed25519.pub
    ```

2.  Copy the output

3.  Go to: https://github.com/settings/keys

4.  Click **New SSH Key**

5.  Title it (Example: "Ubuntu Desktop")

6.  Paste the key → **Add SSH Key**

------------------------------------------------------------------------

## 🔁 5. Convert Your Repo Remote from HTTPS → SSH

Navigate to your Neovim Kickstart repo (usually):

``` bash
cd ~/.config/nvim
```

Update remote:

``` bash
git remote set-url origin git@github.com:YOUR-USERNAME/kickstart.nvim.git
```

Verify:

``` bash
git remote -v
```

Should show something like:

    origin  git@github.com:YOUR-USERNAME/kickstart.nvim.git (fetch)
    origin  git@github.com:YOUR-USERNAME/kickstart.nvim.git (push)

------------------------------------------------------------------------

## 🧪 6. Test Your SSH Connection

``` bash
ssh -T git@github.com
```

Expected message:

    Hi YOUR-USERNAME! You've successfully authenticated, but GitHub does not provide shell access.

------------------------------------------------------------------------

## 📤 7. Push Your Changes to GitHub

Make sure you're on your feature branch:

``` bash
git add .
git commit -m "Describe your change"
git push origin your-branch-name
```

------------------------------------------------------------------------

### 🎉 You're Done!

You can now push code without entering a username or password each time.

------------------------------------------------------------------------

## 🔄 8. (Optional but Recommended) Keep Your Fork Updated with the Original Kickstart Repo

This lets you pull new changes, bug fixes, and improvements from the
original Kickstart repo without overwriting your customizations.

### ✅ Add the original Kickstart repo as an "upstream" remote (only do this once):

``` bash
git remote add upstream https://github.com/nvim-lua/kickstart.nvim.git
```

Verify it was added:

``` bash
git remote -v
```

You should see two remotes now:

    origin    git@github.com:YOUR-USERNAME/kickstart.nvim.git (fetch)
    upstream  https://github.com/nvim-lua/kickstart.nvim.git (fetch)

### 📥 Pull Updates From Upstream

When you want the latest Kickstart updates:

``` bash
git fetch upstream
git checkout main
git merge upstream/main
```

If there are no conflicts, your main branch now includes the latest
changes.

### 🚀 Push Updated Main to Your Fork

``` bash
git push origin main
```

Your fork is now updated!

> 💡 Tip: Do NOT work on your `main` branch. Always create feature
> branches for your changes.

# Plugin Separation Guide

This guide will help you separate the plugins into individual repositories, similar to [NadyaNayme's plugin directory](https://github.com/NadyaNayme/NyusPluginDirectory).

## What I've Done

✅ Created plugin directories locally (`elder-timer/` and `flippr/`)
✅ Copied all plugin files to separate directories
✅ Created a directory-style `index.html` for the main repo
✅ Prepared `appconfig.json` files with correct relative paths

## Next Steps - Manual GitHub Setup

Since GitHub CLI isn't installed, you'll need to create the repositories manually on GitHub:

### Step 1: Create Repository on GitHub

1. Go to https://github.com/new
2. Create repository: `elder-timer`
   - Make it **Public**
   - Don't initialize with README (we have files ready)
3. Create repository: `flippr`
   - Make it **Public**
   - Don't initialize with README

### Step 2: Initialize Each Plugin Repository

For each plugin directory, run these commands in PowerShell:

**For elder-timer:**
```powershell
cd ..\elder-timer
git init
git add .
git commit -m "Initial commit: Elder Tree Timer plugin"
git branch -M main
git remote add origin https://github.com/6inq/elder-timer.git
git push -u origin main
```

**For flippr:**
```powershell
cd ..\flippr
git init
git add .
git commit -m "Initial commit: Flippr plugin"
git branch -M main
git remote add origin https://github.com/6inq/flippr.git
git push -u origin main
```

### Step 3: Enable GitHub Pages for Each Plugin

For each repository:
1. Go to Settings → Pages
2. Select "Deploy from a branch"
3. Branch: `main`, Folder: `/ (root)`
4. Save

After Pages deploys, plugins will be available at:
- `https://6inq.github.io/elder-timer/`
- `https://6inq.github.io/flippr/`

### Step 4: Update Directory Repository

1. Update `alt1plugins` repo:
   - Replace `index.html` with `directory-index.html`
   - Update `README.md` to be directory-style (like NyusPluginDirectory)
   - Commit and push

2. Update the installation links in the directory to point to:
   - `alt1://addapp/https://6inq.github.io/elder-timer/appconfig.json`
   - `alt1://addapp/https://6inq.github.io/flippr/appconfig.json`

## File Structure After Separation

```
Desktop/Github/
├── alt1plugins/          (Directory repo - lists all plugins)
│   ├── index.html       (Directory landing page)
│   └── README.md        (Directory README)
├── elder-timer/         (Plugin repo)
│   ├── index.html
│   ├── main.js
│   ├── style.css
│   └── appconfig.json
└── flippr/              (Plugin repo)
    ├── index.html
    ├── main.js
    ├── style.css
    └── appconfig.json
```

## Benefits of Separation

1. **Independent versioning** - Each plugin has its own version history
2. **Separate GitHub Pages** - Each plugin gets its own domain
3. **Cleaner structure** - Easier to manage and maintain
4. **Better organization** - Matches the community standard pattern


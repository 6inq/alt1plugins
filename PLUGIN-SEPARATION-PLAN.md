# Plugin Separation Plan

This document outlines the steps to separate plugins into individual repositories, similar to [NadyaNayme's plugin directory structure](https://github.com/NadyaNayme/NyusPluginDirectory).

## Current Structure
```
alt1plugins/
├── plugins/
│   ├── elder-timer/
│   └── ge-flipper/
```

## Target Structure
```
alt1plugins/           (Directory repo - just lists plugins)
elder-timer/           (Separate repo for plugin)
flippr/                (Separate repo for plugin)
```

## Steps Required

### Step 1: Create New Repositories on GitHub (Manual)
1. Go to GitHub and create these new repositories:
   - `elder-timer` (public)
   - `flippr` (public)

### Step 2: Prepare Plugin Repositories Locally
I've prepared scripts to help set up each plugin repository locally.

### Step 3: Update Directory Repository
Replace the current `alt1plugins` repo with a directory-style README/index.html that just links to the separate plugin repos.

## Files Ready
- `directory-index.html` - New landing page for directory repo
- This plan document

## Next Steps
1. Create the repositories on GitHub UI
2. Run the separation scripts (I can help with this)
3. Push each plugin to its own repository
4. Update the directory repository with the new structure


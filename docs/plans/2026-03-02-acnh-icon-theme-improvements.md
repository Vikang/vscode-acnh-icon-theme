# ACNH Icon Theme Improvements — Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Fix broken icon references, expand file type coverage, add folder icons, reassign tslint, and replace all remaining previous Valley references.

**Architecture:** All changes are in `icons.json` (icon definitions, file mappings, folder config), `README.md` (rebrand), `package.json` (repo URL), and cleanup of old files. No build step — VS Code reads `icons.json` directly.

**Tech Stack:** VS Code icon theme (JSON config), PNG sprites in `icons/acnh/`

---

### Task 1: Fix broken icon references in icons.json

4 icon definitions are referenced in `fileExtensions`/`fileNames` but missing from `iconDefinitions`.

**Files:**
- Modify: `icons.json`

**Step 1: Add missing iconDefinitions**

Add these 4 entries inside the `"iconDefinitions"` block (after the `_tslint` entry):

```json
"_proto": {
  "iconPath": "icons/acnh/Fossil.png"
},
"_thrift": {
  "iconPath": "icons/acnh/Pale_Chub.png"
},
"_flow": {
  "iconPath": "icons/acnh/Recipe_Bottle.png"
},
"_visualstudiocode": {
  "iconPath": "icons/acnh/Axe_Iron.png"
}
```

**Step 2: Verify JSON is valid**

Run: `python3 -c "import json; json.load(open('icons.json')); print('OK')"`
Expected: `OK`

**Step 3: Commit**

```bash
git add icons.json
git commit -m "fix: add missing icon definitions for proto, thrift, flow, vscode"
```

---

### Task 2: Reassign tslint and add folder icons in icons.json

`Clump_of_Weeds.png` moves from tslint to folders. tslint gets `Fishing_Rod.png`.

**Files:**
- Modify: `icons.json`

**Step 1: Change tslint icon**

In `iconDefinitions`, change `_tslint` from:
```json
"_tslint": {
  "iconPath": "icons/acnh/Clump_of_Weeds.png"
}
```
to:
```json
"_tslint": {
  "iconPath": "icons/acnh/Fishing_Rod.png"
}
```

**Step 2: Add folder definition and folder key**

Add a new `_folder` definition in `iconDefinitions`:
```json
"_folder": {
  "iconPath": "icons/acnh/Clump_of_Weeds.png"
}
```

Then add these two top-level keys to the JSON (after `"file": "_file"`):
```json
"folder": "_folder",
"folderExpanded": "_folder",
```

**Step 3: Verify JSON is valid**

Run: `python3 -c "import json; json.load(open('icons.json')); print('OK')"`
Expected: `OK`

**Step 4: Commit**

```bash
git add icons.json
git commit -m "feat: add folder icons (Clump_of_Weeds) and reassign tslint to Fishing_Rod"
```

---

### Task 3: Add new file type definitions in icons.json

Add 9 new icon definitions and their file extension / file name mappings.

**Files:**
- Modify: `icons.json`

**Step 1: Add new iconDefinitions**

Add these entries inside `iconDefinitions`:

```json
"_python": {
  "iconPath": "icons/acnh/Turnips.png"
},
"_ruby": {
  "iconPath": "icons/acnh/Cherry.png"
},
"_yaml": {
  "iconPath": "icons/acnh/Book_1.png"
},
"_docker": {
  "iconPath": "icons/acnh/Egg_Wood.png"
},
"_shell": {
  "iconPath": "icons/acnh/Axe_Iron.png"
},
"_env": {
  "iconPath": "icons/acnh/Pitfall_Seed.png"
},
"_test": {
  "iconPath": "icons/acnh/Nugget_Gold.png"
},
"_config": {
  "iconPath": "icons/acnh/Coral.png"
},
"_readme": {
  "iconPath": "icons/acnh/Nook_Miles_Ticket.png"
}
```

**Step 2: Add fileExtensions entries**

Add to the `fileExtensions` block:
```json
"py": "_python",
"pyw": "_python",
"rb": "_ruby",
"erb": "_ruby",
"gemspec": "_ruby",
"yml": "_yaml",
"yaml": "_yaml",
"sh": "_shell",
"bash": "_shell",
"zsh": "_shell",
"env": "_env",
"ts": "_typescript",
"tsx": "_typescript",
"css": "_css",
"html": "_html",
"htm": "_html",
"json": "_json",
"lock": "_lock",
"log": "_log"
```

**Step 3: Add fileNames entries**

Add to the `fileNames` block:
```json
"Dockerfile": "_docker",
"dockerfile": "_docker",
"docker-compose.yml": "_docker",
"docker-compose.yaml": "_docker",
"docker-compose.override.yml": "_docker",
".dockerignore": "_docker",
"Gemfile": "_ruby",
"Gemfile.lock": "_lock",
"Rakefile": "_ruby",
".env": "_env",
".env.local": "_env",
".env.development": "_env",
".env.production": "_env",
".env.test": "_env",
".env.example": "_env",
"README.md": "_readme",
"readme.md": "_readme",
"README": "_readme",
"readme": "_readme",
".editorconfig": "_config",
"webpack.config.js": "_config",
"webpack.config.ts": "_config",
"rollup.config.js": "_config",
"rollup.config.ts": "_config",
"vite.config.js": "_config",
"vite.config.ts": "_config",
"vitest.config.js": "_jest",
"vitest.config.ts": "_jest",
"pnpm-lock.yaml": "_lock",
".bashrc": "_shell",
".zshrc": "_shell",
".bash_profile": "_shell"
```

**Step 4: Add languageIds entries**

Add to the `languageIds` block:
```json
"python": "_python",
"ruby": "_ruby",
"yaml": "_yaml",
"dockerfile": "_docker",
"shellscript": "_shell",
"markdown": "_markdown"
```

**Step 5: Verify JSON is valid**

Run: `python3 -c "import json; json.load(open('icons.json')); print('OK')"`
Expected: `OK`

**Step 6: Commit**

```bash
git add icons.json
git commit -m "feat: add Python, Ruby, YAML, Docker, Shell, Env, Config, Readme file type icons"
```

---

### Task 4: Rebrand README.md

Replace all previous Valley content with ACNH branding.

**Files:**
- Modify: `README.md`

**Step 1: Rewrite README.md**

Replace entire contents with:

```markdown
# Animal Crossing: New Horizons Icon Theme for VS Code

An Animal Crossing: New Horizons themed icon pack for VS Code!
Uses inventory sprites from AC:NH to bring your code editor to island life.

## Supported File Types

- **Languages:** JavaScript, TypeScript, Python, Ruby, HTML, CSS, GraphQL
- **Config:** ESLint, Prettier, Babel, Jest, Apollo, Bazel, Docker, YAML
- **Project:** package.json, lock files, git, logs, licenses, env files
- **Folders:** All folders use the iconic Clump of Weeds

## Development

This extension uses image files from `icons/acnh/` mapped in `icons.json`.

Open this repo in VS Code and press F5 to test.

### Prerequisites

```
npm install -g @vscode/vsce
```

### Publish to VS Code Marketplace

Update the version in `package.json`, then:

```
vsce publish
```

### Package for sharing

```
vsce package
```

Install the generated `.vsix`:

```
code --install-extension vscode-acnh-icon-theme-0.0.8.vsix
```

## Resources

Icons inspired by Animal Crossing: New Horizons by Nintendo.
```

**Step 2: Commit**

```bash
git add README.md
git commit -m "docs: rebrand README from previous Valley to ACNH"
```

---

### Task 5: Update package.json repo URL and clean up old files

**Files:**
- Modify: `package.json`
- Delete: `vscode-stardew-icon-theme-0.0.1.vsix`
- Delete: `SampleScreenshot.png` (previous screenshot, no longer relevant)

**Step 1: Note about repo URL**

The repo URL `https://github.com/klyap/vscode-stardew-icon-theme.git` points to the actual GitHub repo. Since renaming the repo is a GitHub operation (not a code change), leave this as-is or add a comment. No code change needed here unless the repo is actually renamed on GitHub.

**Step 2: Delete old artifacts**

```bash
rm -f vscode-stardew-icon-theme-0.0.1.vsix
rm -f SampleScreenshot.png
```

**Step 3: Commit**

```bash
git add -u
git commit -m "chore: remove old previous .vsix and screenshot"
```

---

### Task 6: Update docs/plans to remove previous references

**Files:**
- Modify: `docs/plans/2026-03-02-acnh-icon-theme-implementation.md`

**Step 1: Update the old implementation plan**

Replace references to "previous" with "previous theme" or remove them where they're no longer relevant. Key changes:
- Goal line: "Convert the previous theme" instead of "Convert the previous Valley..."
- Task 4 heading: "Clean up unused icon files" instead of "Clean up unused previous icon files"
- Remove specific previous wiki references

**Step 2: Commit**

```bash
git add docs/plans/
git commit -m "docs: update plans to remove previous Valley references"
```

---

### Task 7: Final verification

**Step 1: Validate all icon paths resolve to real files**

```bash
python3 -c "
import json, os
with open('icons.json') as f:
    data = json.load(f)
missing = []
for name, obj in data['iconDefinitions'].items():
    path = obj['iconPath']
    if not os.path.isfile(path):
        missing.append(f'{name} -> {path}')
if missing:
    print('MISSING:')
    for m in missing: print(f'  {m}')
else:
    print('All icon paths resolve. OK')
"
```

Expected: `All icon paths resolve. OK`

**Step 2: Validate no dangling icon definition references**

```bash
python3 -c "
import json
with open('icons.json') as f:
    data = json.load(f)
defs = set(data['iconDefinitions'].keys())
refs = set()
for section in ['fileExtensions', 'fileNames', 'languageIds']:
    if section in data:
        refs.update(data[section].values())
if 'folder' in data: refs.add(data['folder'])
if 'folderExpanded' in data: refs.add(data['folderExpanded'])
dangling = refs - defs
if dangling:
    print(f'DANGLING refs: {dangling}')
else:
    print('All references resolve. OK')
"
```

Expected: `All references resolve. OK`

**Step 3: Test in VS Code**

Press F5 in VS Code to launch Extension Development Host. Verify:
- Files show correct ACNH icons
- Folders show Clump of Weeds icon
- Python, Ruby, YAML, Docker, Shell files show their new icons
- No broken/missing icons in the file explorer

# ACNH Icon Theme Implementation Plan

> **For Claude:** REQUIRED SUB-SKILL: Use superpowers:executing-plans to implement this plan task-by-task.

**Goal:** Convert the previous theme into an Animal Crossing: New Horizons icon theme, remapping all icon definitions to ACNH inventory sprites and rebranding the project.

**Architecture:** Replace all `iconPath` values in `icons.json` to point at `icons/acnh/*.png` files. Update `package.json` with new name/description/keywords. Remove seasonal variants (autumn/winter) from the theme contributions since we're starting with one base theme. Keep all `fileExtensions`, `fileNames`, and `languageIds` mappings intact.

**Tech Stack:** VS Code icon theme (JSON config), PNG sprites

---

## Available ACNH Icons → Icon Definition Mapping

Cross-referencing the approved design doc with the actual files in `icons/acnh/`:

| ACNH File | → Icon Def | Rationale |
|---|---|---|
| `Green_Leaf.png` | `_file` | Default fallback — iconic AC leaf |
| `Recipe.png` | `_javascript` | JS = crafting from recipes |
| `Fossil.png` | `_javascript_test` | Tests examine/reveal (single fossil covers both test + babel, see note) |
| `Wand.png` | `_css` | Styling/transformation |
| `Coral.png` | `_html` | Structural reef of the web |
| `Money_Bag.png` | `_json` | Structured data/values |
| `Pitfall_Seed.png` | `_lock` | Don't touch! It's a trap! |
| `Fishing_Rod.png` | `_eslint` | Catches code problems |
| `Cosmos_Pink.png` | `_prettier` | Making things pretty |
| `Nook_Miles_Ticket.png` | `_git` | Branching/traveling |
| `Recipe_Bottle.png` | `_log` | Messages from the past |
| `Egg_Wood.png` | `_image` | Decorative visual item (Bunny Day egg) |
| `Book_1.png` | `_markdown` | Book = docs |
| `Wasp_Nest.png` | `_babel` | Wasps transform raw material into complex structures |
| `Tree_Branch.png` | `_license` | Basic natural offering/token |
| `Present_Red.png` | `_package` | A wrapped bundle of things |
| `Spider.png` | `_graphql` | Web of connections |
| `Pale_Chub.png` | `_cerberus` | A fish catch (Cerberus guards, chub is watchful) |
| `Net.png` | `_jest` | Catches bugs |
| `Star.png` | `_apollo` | Celestial/space |
| `Axe_Iron.png` | `_bazel` | Build tool |
| `Hyacinths_Purple.png` | `_fusion` | Flower → flower |
| `Nugget_Gold.png` | `_typescript` | Valuable strong material |
| `Clump_of_Weeds.png` | `_tslint` | Weeds = lint to clean up |

**Note:** The design doc called for separate Appraised/Unappraised fossils, Peach, Snapping Turtle, Construction Permit, Custom Design Editor, Tailors Ticket, and Customization Kit — these aren't in `icons/acnh/` yet. The plan uses the best available alternatives. Icons can be swapped later when more sprites are added.

**Missing from design (not yet available):**
- Peach → using Present_Red for `_package` instead
- Snapping Turtle → using Pale_Chub for `_cerberus`
- Construction Permit → using Tree_Branch for `_license`
- Custom Design Editor → using Egg_Wood for `_image`
- Tailors Ticket → no `_font` def (font files fall back to `_file`)
- Customization Kit → no `_visualstudiocode` def (VS Code files fall back to `_file`)
- Second fossil sprite → using Wasp_Nest for `_babel` instead

---

### Task 1: Rename project in package.json

**Files:**
- Modify: `package.json`

**Step 1: Update package.json fields**

Replace `name`, `displayName`, `description`, `icon`, `keywords`, and remove autumn/winter theme contributions. Keep only one base ACNH theme.

New values:
- `name`: `"vscode-acnh-icon-theme"`
- `displayName`: `"Animal Crossing New Horizons Icon Theme"`
- `description`: `"Inventory icons from Animal Crossing: New Horizons"`
- `icon`: `"icons/acnh/Green_Leaf.png"`
- `iconThemes`: single entry with id `"vscode-acnh-icon-theme"`, label `"Animal Crossing New Horizons Icon Theme"`, path `"./icons.json"`
- `keywords`: `["icons", "theme", "pixel", "icon", "cute", "game", "animal", "crossing", "new horizons", "acnh", "cozy", "nintendo"]`

**Step 2: Verify JSON is valid**

Run: `cat package.json | python3 -m json.tool > /dev/null`
Expected: no output (valid JSON)

**Step 3: Commit**

```
git add package.json
git commit -m "Rename project to Animal Crossing New Horizons Icon Theme"
```

---

### Task 2: Replace all icon paths in icons.json

**Files:**
- Modify: `icons.json`

**Step 1: Replace all iconPath values in iconDefinitions**

Map every `iconPath` to the corresponding `icons/acnh/*.png` file. Also add new definitions for `_typescript`, `_tslint`, and `_visualstudiocode` that were previously dangling references (referenced in `fileNames`/`languageIds` but never defined).

Final `iconDefinitions` block:

```json
{
  "_file":            { "iconPath": "icons/acnh/Green_Leaf.png" },
  "_css":             { "iconPath": "icons/acnh/Wand.png" },
  "_html":            { "iconPath": "icons/acnh/Coral.png" },
  "_javascript":      { "iconPath": "icons/acnh/Recipe.png" },
  "_javascript_test": { "iconPath": "icons/acnh/Fossil.png" },
  "_json":            { "iconPath": "icons/acnh/Money_Bag.png" },
  "_lock":            { "iconPath": "icons/acnh/Pitfall_Seed.png" },
  "_eslint":          { "iconPath": "icons/acnh/Fishing_Rod.png" },
  "_prettier":        { "iconPath": "icons/acnh/Cosmos_Pink.png" },
  "_git":             { "iconPath": "icons/acnh/Nook_Miles_Ticket.png" },
  "_log":             { "iconPath": "icons/acnh/Recipe_Bottle.png" },
  "_image":           { "iconPath": "icons/acnh/Egg_Wood.png" },
  "_markdown":        { "iconPath": "icons/acnh/Book_1.png" },
  "_babel":           { "iconPath": "icons/acnh/Wasp_Nest.png" },
  "_license":         { "iconPath": "icons/acnh/Tree_Branch.png" },
  "_package":         { "iconPath": "icons/acnh/Present_Red.png" },
  "_graphql":         { "iconPath": "icons/acnh/Spider.png" },
  "_cerberus":        { "iconPath": "icons/acnh/Pale_Chub.png" },
  "_jest":            { "iconPath": "icons/acnh/Net.png" },
  "_apollo":          { "iconPath": "icons/acnh/Star.png" },
  "_bazel":           { "iconPath": "icons/acnh/Axe_Iron.png" },
  "_fusion":          { "iconPath": "icons/acnh/Hyacinths_Purple.png" },
  "_typescript":      { "iconPath": "icons/acnh/Nugget_Gold.png" },
  "_tslint":          { "iconPath": "icons/acnh/Clump_of_Weeds.png" }
}
```

**Step 2: Keep fileExtensions, fileNames, and languageIds sections unchanged**

These map file types → icon definition names. They stay the same since the definition names haven't changed.

Only fix: the typo `"grapqhl"` → `"graphql"` in fileExtensions.

**Step 3: Verify JSON is valid**

Run: `cat icons.json | python3 -m json.tool > /dev/null`
Expected: no output (valid JSON)

**Step 4: Commit**

```
git add icons.json
git commit -m "Replace all previous icon paths with ACNH inventory sprites"
```

---

### Task 3: Remove autumn and winter theme files

Since we're starting with one base theme, remove the seasonal JSON files and their icon directories.

**Files:**
- Delete: `icons-autumn.json`
- Delete: `icons-winter.json`
- Delete: `icons/autumn/` (directory)
- Delete: `icons/winter/` (directory)

**Step 1: Delete seasonal files**

```bash
rm icons-autumn.json icons-winter.json
rm -rf icons/autumn icons/winter
```

**Step 2: Verify only base icons.json remains**

Run: `ls *.json`
Expected: `icons.json  package.json`

**Step 3: Commit**

```
git add -u
git commit -m "Remove seasonal theme variants (autumn, winter)"
```

---

### Task 4: Clean up unused previous icon files

The original previous `.png` files in `icons/` (top-level) are no longer referenced. Remove them to avoid confusion — all ACNH icons live in `icons/acnh/`.

**Files:**
- Delete: all `.png` files directly in `icons/` (NOT in `icons/acnh/`)

**Step 1: List previous icons to be removed**

```bash
ls icons/*.png
```

Expected: Apple.png, Blobfish.png, Bok_Choy.png, Book.png, Bundle_Orange.png, Bundle_Yellow.png, Cat.png, Cat_1.png, Coffee_Bean.png, Dandelion.png, Dog_3.png, Fiber.png, Garlic.png, Grape.png, Key.png, Leek.png, Melon.png, Pancakes.png, Parsnip.png, Quartz.png, Red_Mushroom.png, Scroll.png, Spangle.png, Starfruit.png, Strawberry.png, Summer_Seeds.png, Sunflower.png, Sweet_Pea.png, Tea_Bush.png, Wood.png

**Step 2: Remove them**

```bash
rm icons/*.png
```

**Step 3: Verify only acnh/ subdirectory remains**

```bash
ls icons/
```

Expected: `acnh`

**Step 4: Commit**

```
git add -u
git commit -m "Remove unused previous Valley icon files"
```

---

### Task 5: Final verification

**Step 1: Validate all icon paths resolve to real files**

```bash
python3 -c "
import json, os
with open('icons.json') as f:
    data = json.load(f)
for name, obj in data['iconDefinitions'].items():
    path = obj['iconPath']
    exists = os.path.isfile(path)
    status = 'OK' if exists else 'MISSING'
    print(f'{status}: {name} -> {path}')
"
```

Expected: all lines show `OK`

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
dangling = refs - defs
if dangling:
    print(f'DANGLING refs (no iconDefinition): {dangling}')
else:
    print('All references resolve to definitions. OK')
"
```

Expected: `All references resolve to definitions. OK`
Note: `_proto`, `_thrift`, and `_flow` will show as dangling — these were inherited from the previous theme and never had definitions. Can be cleaned up as a follow-up.

**Step 3: Validate package.json**

Run: `cat package.json | python3 -m json.tool > /dev/null`
Expected: no output (valid JSON)

# Animal Crossing: New Horizons Icon Theme for VS Code

An Animal Crossing: New Horizons themed icon pack for VS Code!
Uses inventory sprites from AC:NH to bring your code editor to island life.

## Icon Reference

| Icon | ACNH Item | File Types |
|:----:|-----------|------------|
| <img src="icons/acnh/Green_Leaf.png" width="32"> | Green Leaf | Default (all unmapped files) |
| <img src="icons/acnh/Coral.png" width="32"> | Coral | `.html`, `.htm` |
| <img src="icons/acnh/Wand.png" width="32"> | Wand | `.css` |
| <img src="icons/acnh/Recipe.png" width="32"> | Recipe | `.js`, `.jsx` |
| <img src="icons/acnh/Fossil.png" width="32"> | Fossil | `.ts`, `.tsx`, `.proto` |
| <img src="icons/acnh/Money_Bag.png" width="32"> | Money Bag | `.json`, `jsconfig.json`, `tsconfig.json` |
| <img src="icons/acnh/Book_1.png" width="32"> | Book | `.md`, `.yml`, `.yaml` |
| <img src="icons/acnh/Turnips.png" width="32"> | Turnips | `.py`, `.pyw` |
| <img src="icons/acnh/Cherry.png" width="32"> | Cherry | `.rb`, `.erb`, `Gemfile`, `Rakefile` |
| <img src="icons/acnh/Peach.png" width="32"> | Peach | Images (`.jpg`, `.png`, `.gif`, `.svg`, `.bmp`, `.ico`) |
| <img src="icons/acnh/Recipe_Bottle.png" width="32"> | Recipe Bottle | `.log`, changelogs |
| <img src="icons/acnh/Nook_Miles_Ticket.png" width="32"> | Nook Miles Ticket | `.git`, `README` |
| <img src="icons/acnh/Wasp_Nest.png" width="32"> | Wasp Nest | `.gitignore`, `.babelrc` |
| <img src="icons/acnh/Pitfall_Seed.png" width="32"> | Pitfall Seed | `.lock`, `.env` files |
| <img src="icons/acnh/Present_Red.png" width="32"> | Present | `package.json` |
| <img src="icons/acnh/Tree_Branch.png" width="32"> | Tree Branch | `LICENSE`, `COPYRIGHT` |
| <img src="icons/acnh/Nugget_Gold.png" width="32"> | Nugget Gold | Test files (`.snap`) |
| <img src="icons/acnh/Fishing_Rod.png" width="32"> | Fishing Rod | ESLint, TSLint configs |
| <img src="icons/acnh/Cosmos_Pink.png" width="32"> | Cosmos Pink | Prettier configs |
| <img src="icons/acnh/Net.png" width="32"> | Net | Jest, Vitest configs |
| <img src="icons/acnh/Star.png" width="32"> | Star | Apollo config |
| <img src="icons/acnh/Spider.png" width="32"> | Spider | `.graphql` |
| <img src="icons/acnh/Axe_Iron.png" width="32"> | Axe Iron | Bazel, VS Code settings, `.sh`, `.bash`, `.zsh` |
| <img src="icons/acnh/Egg_Wood.png" width="32"> | Egg Wood | Dockerfile, docker-compose |
| <img src="icons/acnh/Hyacinths_Purple.png" width="32"> | Hyacinths Purple | Fusion config |
| <img src="icons/acnh/Pale_Chub.png" width="32"> | Pale Chub | Cerberus, `.thrift` |
| <img src="icons/acnh/Coral.png" width="32"> | Coral | `.editorconfig`, webpack/rollup/vite configs |
| <img src="icons/acnh/Clump_of_Weeds.png" width="32"> | Clump of Weeds | Folders |

### Not yet mapped

These common file types currently use the default Green Leaf — future icon assignments welcome!

`.txt`, `.go`, `.java`, `.c`, `.cpp`, `.h`, `.rs`, `.swift`, `.php`, `.sql`, `.toml`, `.xml`, `.vue`, `.svelte`, `.scss`, `.sass`, `.less`, `.tf`, `.tfvars`, `.lua`, `.kt`, `.r`, `.csv`

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

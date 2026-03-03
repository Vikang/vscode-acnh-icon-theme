# Animal Crossing: New Horizons Icon Theme — Improvement Design

## Overview

Improve and fully rebrand the VS Code ACNH icon theme. The theme was partially converted from previous Valley but has broken references, limited file type coverage, no folder icons, and remaining previous branding.

## Goals

1. Fix 4 broken icon references (`_proto`, `_thrift`, `_flow`, `_visualstudiocode`)
2. Add ~9 new file type definitions (Python, Ruby, YAML, Docker, Shell, Env, Test, Config, Readme)
3. Add simple folder icons using `Clump_of_Weeds.png` for all folders
4. Replace all remaining previous Valley references with Animal Crossing: New Horizons
5. Clean up old artifacts (`.vsix` file)

## Design Decisions

- **Folder icons:** Single icon (`Clump_of_Weeds.png`) for all folders — keep it simple
- **tslint reassignment:** `Clump_of_Weeds` moves to folders, tslint gets `Fishing_Rod` (alongside eslint, both linters)
- **Rebranding scope:** Everything — README, package.json, docs/plans, old .vsix file

## Fix Broken Icon References

| Missing Definition | Used By | Map To |
|---|---|---|
| `_proto` | `.proto` files | `Fossil.png` |
| `_thrift` | `.thrift` files | `Pale_Chub.png` |
| `_flow` | `.flowconfig` | `Recipe_Bottle.png` |
| `_visualstudiocode` | VS Code config files | `Axe_Iron.png` |

## New File Type Mappings

| Definition | File Types | Icon | Reasoning |
|---|---|---|---|
| `_python` | `.py`, `.pyw` | `Turnips.png` | Turnip market = Python's popularity |
| `_ruby` | `.rb`, `.erb`, `.gemspec`, `Gemfile` | `Cherry.png` | Red fruit = Ruby |
| `_yaml` | `.yml`, `.yaml` | `Book_1.png` | Config = reference book |
| `_docker` | `Dockerfile`, `docker-compose.*` | `Egg_Wood.png` | Container = egg |
| `_shell` | `.sh`, `.bash`, `.zsh` | `Axe_Iron.png` | Shell = tool |
| `_env` | `.env`, `.env.local`, etc. | `Pitfall_Seed.png` | Hidden = secrets |
| `_test` | `*.test.*`, `*.spec.*` | `Nugget_Gold.png` | Gold standard = tests |
| `_config` | various config files | `Coral.png` | Structured = config |
| `_readme` | `readme.md`, `README.md` | `Nook_Miles_Ticket.png` | Guide = readme |

## Folder Icons

| Type | Icon |
|---|---|
| All folders (closed and open) | `Clump_of_Weeds.png` |

## Reassignments

| Definition | Old Icon | New Icon | Reason |
|---|---|---|---|
| `_tslint` | `Clump_of_Weeds.png` | `Fishing_Rod.png` | Freed up for folders |

## Rebranding Scope

| File | Action |
|---|---|
| `README.md` | Full rewrite — ACNH title, description, resource links |
| `package.json` | Update repo URL comment |
| `vscode-stardew-icon-theme-0.0.1.vsix` | Delete |
| `docs/plans/*.md` | Update previous references |

## Available Icons (27 total + 2 new)

All in `icons/acnh/`: Axe_Iron, Book_1, Cherry, Clay, Clump_of_Weeds, Coral, Cosmos_Pink, Egg_Wood, Fishing_Rod, Fossil, Green_Leaf, Hyacinths_Purple, Money_Bag, Net, Nook_Miles_Ticket, Nugget_Gold, Pale_Chub, Peach, Pitfall_Seed, Present_Red, Recipe, Recipe_Bottle, Spider, Star, Stone, Tree_Branch, Turnips, Wand, Wasp_Nest

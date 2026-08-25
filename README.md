# Mina's Modules

A Logos Basecamp module catalog. Add it once and everything here shows up in
your Package Manager.

## Install

In Basecamp, open **Package Manager → Add repository** and paste:

```
https://raw.githubusercontent.com/Thompsonmina/logos-basecamp-modules/main/logos-repo.json
```

Then install anything below. Dependencies resolve on their own — installing a
game pulls in whatever engine it needs.

## What's here

| Module | | Source |
|---|---|---|
| **Minesweeper** | The game. Five tiers, resumable, with recorded times. | [`minesweeper_ui`](https://github.com/Thompsonmina/minesweeper_ui) |
| `minesweeper_module` | Its engine — a headless core you can also drive over IPC. | [`minesweeper_module`](https://github.com/Thompsonmina/minesweeper_module) |

Install **Minesweeper**; the engine comes with it.

Every module here is dual-licensed MIT or Apache-2.0, and each lives in its own
repository with its own README, issues and releases.

## How this catalog works

Basecamp reads `logos-repo.json` from this repo's default branch. That file
points at `index.json`, published as an asset on the rolling
[`index`](../../releases/tag/index) release, which lists every module version
with its download URL, content hash and manifest.

Each module version is its own GitHub release here, tagged
`<module>-v<version>`, carrying the `.lgx` package and a JSON sidecar. The
index is rebuilt from those releases, so **the releases are the source of
truth** and the index is derived.

The machinery is [`logos-co/logos-modules-release-action`](https://github.com/logos-co/logos-modules-release-action),
and this repo was created from
[`logos-co/logos-modules-release-base`](https://github.com/logos-co/logos-modules-release-base).

### Publishing a new version

Bump the module's `metadata.json#version` in its own repo and tag it, move the
submodule pointer here, then run **Release all modules** from the Actions tab
(or **Release &lt;module&gt;** for just one). Re-running for an unchanged version
is a no-op, so the umbrella workflow is always safe to run.

```bash
git submodule update --init --recursive   # after cloning
```

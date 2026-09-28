# charly-filebrowser

The `charly-filebrowser` family — the FileBrowser web file-manager skill.

The `charly-filebrowser` candy is a **concept candy**: it ships no install
content and owns the `filebrowser` family of `skill:` entities whose names have
no namesake candy. It currently carries the `filebrowser-layer` skill —
FileBrowser Quantum (the gtsteffaniak fork) served as a config-file-driven web
file manager on port 8080. `candy/plugin-marketplace` regenerates the standalone
[opencharly/marketplace](https://github.com/opencharly/marketplace) corpus from
these entities, so the skills are authored here and projected there.

## What it provides

| Property | Value |
|---|---|
| Layer / candy | `charly-filebrowser` (concept candy) |
| Install content | none — a `true` no-op `plan:` |
| Owns | 1 `skill:` entity: `filebrowser-layer` |
| Projected to | `marketplace/filebrowser/skills/` |
| Service / port | none |

## How to use it

This repo is consumed as a **skill source**, not as an image layer. Edit the
`skill:` entities in `charly.yml`; the marketplace regeneration projects them
into `/charly-filebrowser:*` pages. To reference the repo directly, compose it
in a box. A box is a `candy:` node that carries the box's `base:` image and a
nested `candy:` list of layer refs (the nested `candy:` is the composition list;
the outer `candy:` is the box body):

```yaml
my-box:
  candy:                  # the box body (an IMAGE is a `candy:` node carrying `base:`)
    base: fedora          # the box's base image
    candy:                # the box's composition list
      - '@github.com/opencharly/layer-charly-filebrowser:v2026.243.2103'
```

The FileBrowser service is consumed through the `filebrowser` box, which composes
the `filebrowser` candy from `opencharly/pod-filebrowser`; the `filebrowser-layer`
skill here documents that candy's behaviour.

## Layout

- `charly.yml` — the `charly-filebrowser:` concept candy entity plus the
  `filebrowser-layer-skill:` entity (`name: filebrowser-layer`,
  `family: filebrowser`).
- `.github/workflows/tag-on-merge.yml` — CalVer tag + `CHANGELOG/` on merge.
- `README.md` — this user overview.

## Related

- Owning skill: `/charly-filebrowser:filebrowser-layer`
- Authoring reference: `/charly-image:layer`
- FileBrowser box: `/charly-filebrowser:filebrowser` (in `opencharly/pod-filebrowser`)
- [`opencharly/marketplace`](https://github.com/opencharly/marketplace) — the projected corpus
- [`opencharly/charly`](https://github.com/opencharly/charly) — the charly CLI and image builder
- [`opencharly/opencharly`](https://github.com/opencharly/opencharly) — the umbrella

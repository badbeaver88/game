# Gridmapper for Umberhold

This directory vendors **Gridmapper** by Alex Schroeder and includes a small Umberhold-specific fork:

- `umberhold-gridmapper.svg` — browser-based map editor with the default canvas changed from `30x30` to `26x26`
- `upstream/` — upstream README, license, and optional Perl server scripts

## Review

### Why it fits Umberhold

Gridmapper is a good fit as a **graybox map-authoring tool** for this repo because it already provides:

- fast keyboard-first dungeon drafting
- multi-level support
- dead-simple sharing through exported text
- an optional collaboration model
- a permissive **CC0 / public-domain** license

That matches Umberhold's need for quickly sketching classic blobber-style spaces before engine implementation exists.

### Limits

Gridmapper is **not** a final runtime map format for Umberhold.

It does **not** model important game-specific data such as:

- `texture_id`
- per-tile encounter tables
- step triggers / set pieces
- transit metadata between regions
- conditional interactions and flags
- first-person rendering data

So the right use is:

1. draft a dungeon layout in Gridmapper
2. export the map text
3. convert or hand-author the final structured game data in Umberhold schemas

## Recommended workflow

1. Open `umberhold-gridmapper.svg` in a browser.
2. Draft the floor layout at `26x26` scale.
3. Use **Download -> TXT** or **Export Map** to save the text representation.
4. Commit that exported text alongside the design docs for the region/floor.
5. Translate the approved layout into the eventual structured Umberhold map schema.

## Running it

### Easiest

Open `umberhold-gridmapper.svg` directly in your browser.

### Local web server

From this directory:

```bash
python3 -m http.server 8000
```

Then open:

```text
http://localhost:8000/umberhold-gridmapper.svg
```

## Collaboration and server support

Upstream Gridmapper supports collaboration through a Mojolicious websocket server.
Those server-side files are preserved in `upstream/`, but they are **not wired into this repo** and require Perl dependencies not currently provisioned here.

## Suggested Umberhold conventions

Until a final importer exists, use Gridmapper as a layout draft and keep annotations lightweight:

- labels for room names or encounter IDs
- stairs for inter-floor transitions
- doors only where traversal state matters
- colors only as designer notes, not canonical gameplay data

## License

Upstream Gridmapper is released under **CC0 1.0 / public domain**.
See `upstream/LICENSE.md`.

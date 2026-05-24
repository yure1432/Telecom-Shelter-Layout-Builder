# Telecom Shelter Layout Builder

A self-contained, single-file web app for designing and exporting telecom shelter rack layouts as PNG diagrams.

## Features

- **Multiple shelters** — up to 6 shelters per session
- **5 fixed zones** per shelter: front wall, left wall, center, right wall, door wall
- **Dynamic columns** — add any number of columns between left↔center and center↔right
- **Sub-columns** — add sub-columns directly beneath any column
- **AC unit detection** — labels starting with `AC` render as compact AC tiles; everything else renders as a rack with alternating sub-item rows
- **Live canvas preview** — real-time 1100px-wide PNG-quality preview with per-shelter tabs
- **Customizable heading color** — color picker updates rack headers globally; foreground text auto-adjusts for contrast
- **Import / Export** — structured `.txt` format compatible with the original Python tool; export individual or all shelter PNGs

## Usage

Open `shelter_layout_builder.html` directly in any modern browser — no server or dependencies required.

### Text format

```
Shelter 1
--zone: front wall
----AC1
----AC2
--zone: left wall
----Rack 1: U1, U2, U3
--sub-col: Left Sub
----PDU A: C1, C2
--lc-col: Extra Col
----Switch 1
--zone: center
----Rack 2: U1, U2
--zone: right wall
----Rack 3
--zone: door wall
----Fire Panel
```

**Directives:**
| Directive | Description |
|---|---|
| `--zone: <name>` | Switch to a fixed zone (`front wall`, `left wall`, `center`, `right wall`, `door wall`) |
| `--lc-col: <name>` | Add a dynamic column between left wall and center |
| `--cr-col: <name>` | Add a dynamic column between center and right wall |
| `--sub-col: <name>` | Add a sub-column beneath the preceding zone or column |
| `----<label>` | Item with no sub-items |
| `----<label>: A, B, C` | Item with comma-separated sub-items (rendered as rack rows) |

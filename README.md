# JTF-DC Guard map — label placer

Interactive tool for positioning the number labels on the Capital News Service
map of National Guard personnel deployed to Washington, D.C.

**Live:** https://dlanderm-dal.github.io/jtf-dc-guard-map/

## What it does

Drag any number to move it. A dashed outline marks where it started. Arrow keys
nudge one pixel; Shift+arrow moves ten.

- **Copy changes** — puts the moved labels on your clipboard as `Name: lat, lon`
- **Copy full CSV** — the complete positions file, ready to upload to Flourish
- **Reset all** — back to the computed starting points

Output is latitude and longitude, so it is projection-independent: a number
placed inside Florida here lands inside Florida on the Flourish map.

## Starting positions

Each state's default is its *pole of inaccessibility* — the point furthest from
any of that state's borders. That beats a centroid, which falls in open water on
L-shaped states like Florida and Louisiana.

D.C. and the U.S. Virgin Islands are drawn as inset boxes in the Atlantic,
matching the boxes in the Flourish geometry. Alaska and Puerto Rico get their
own panels, since they do not fit the main map at true scale.

## Status

**Draft. Not cleared for publication.** The personnel figures and the 2026
governor results behind the colors are unverified. See the parent project for
the outstanding sourcing questions.

## Built with

d3 v7 and topojson-client, both bundled into `index.html` so the page needs no
network at all. State outlines from the US Census via `us-atlas`.

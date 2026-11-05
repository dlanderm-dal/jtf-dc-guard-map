# JTF-DC Guard map — label placer

Interactive tool for positioning the number labels on the Capital News Service
map of National Guard personnel deployed to Washington, D.C.

**Live:** https://dlanderm-dal.github.io/jtf-dc-guard-map/

Companion to Flourish visualisation `30816616`.

## What it does

Drag any number to move it. A dashed outline marks where it started and a line
connects the two. Arrow keys nudge one pixel; Shift+arrow moves ten.

- **Copy changes** — the moved labels as `Name: new_lat, new_lon (Δlat, Δlon)`
- **Copy full CSV** — the complete positions file, ready to paste straight into
  the Flourish Points sheet. Its columns and starting coordinates already match
  that sheet, so nothing has to be recombined by hand.
- **Reset all** — back to the starting points

## Why it matches the Flourish map

A dragged position is only meaningful if this map starts from the same baseline
as the Flourish one, so both halves of that baseline are taken from the live
visualisation rather than rebuilt:

**Projection.** The embed reports `projection: "Albers USA"`, `fit: "map"`,
`zoom: 1`, no padding. That is a composite — Alaska scaled and tucked under the
southwest, Puerto Rico moved up beside Florida — not a plain Albers. Stock
`d3.geoAlbersUsa` has no Puerto Rico lobe and returns `null` there, so a fourth
lobe is added; the rest are d3's own constants.

**Geometry.** The 53 region outlines are the visualisation's own
`regions_geometry` sheet, not a generic US atlas, so the shapes, the D.C. inset
box and the U.S. Virgin Islands box are identical in both places.

Output is latitude and longitude, so a number placed inside Florida here lands
inside Florida on the Flourish map.

## Two things to know

- **Keep the D.C. and U.S. Virgin Islands numbers inside their boxes.** Those
  two are inset boxes in the open Atlantic, not real locations. A label dragged
  outside its box gets a coordinate in open ocean, and Flourish will plot it
  there.
- **Puerto Rico's placement is calibrated, not read from Flourish.** Flourish
  draws to canvas and does not expose its projection, so the Puerto Rico lobe
  was fitted by measuring the rendered map. It is within a few pixels, which is
  fine for placing a label, but it is the one part not derived exactly.

## Status

**Draft. Not cleared for publication.** The personnel figures and the 2026
governor results behind the colors are unverified. See the parent project for
the outstanding sourcing questions.

## Built with

d3 v7, bundled inline. The page needs no network and no server — though opening
it from GitHub Pages is the easy route.

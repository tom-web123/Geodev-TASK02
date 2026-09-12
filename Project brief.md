# My project brief

## The question

Which residential areas in Tabata Ward, Ilala Municipality are more than 300m from a paved road?

## Why it matters

Tabata Ward is repeatedly flagged in Dar es Salaam disaster-planning exercises as flood-prone. A footway or unpaved road that becomes impassable during a flood can cut a household off from emergency responders even when help is nearby. Ward disaster-management officers could use this to prioritize which residential clusters need alternate access routes before the next flood season.

## The data I need

| Dataset | Source & Link | Features | Geometry Type | Key Columns | Gaps / Missing Values |
|---|---|---|---|---|---|
| Tabata Ward boundary | OpenStreetMap, via QuickOSM plugin in QGIS — https://www.openstreetmap.org/ | 1 | MultiPolygon | `Municipal`, `Ward`, `Subward`, `Feature`, `Latitude`, `Longitude` | None — single feature, fully populated |
| Building footprints | HOTOSM Export Tool — https://export.hotosm.org/v3/ | 16,879 | MultiPolygon | `osm_id`, `osm_type`, `building` | `name` present on <1% of buildings; most optional tags (address, levels, material) empty for the majority |
| Road network | HOTOSM Export Tool — https://export.hotosm.org/v3/ | 564 | MultiLineString | `highway`, `name`, `ward_name` | `name` missing on 72% of roads (mostly unnamed footways/service roads) |
| Amenity / POI points | OpenStreetMap, via QuickOSM plugin in QGIS — https://www.openstreetmap.org/ | 65 | Point | `amenity`, `Name`, `xcoord`, `ycoord` | `Name` missing on 46% of points |

All four datasets share a single CRS — EPSG:32737 (WGS 84 / UTM Zone 37S) — so no reprojection is needed before analysis.

## What I would build

A map showing which residential buildings in Tabata Ward fall outside a 300m buffer of the paved road network, layered against nearby emergency-relevant amenities. Alongside it, a short summary table reporting the count and share of road-isolated buildings, so a ward disaster officer can see at a glance which areas to prioritize.

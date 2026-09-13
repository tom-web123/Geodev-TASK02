# My project brief

## The question

Which residential areas in Tabata Ward, Ilala Municipality are more than 300m from a paved road?

## Why it matters

Tabata Ward is repeatedly flagged in Dar es Salaam disaster-planning exercises as flood-prone. A footway or unpaved road that becomes impassable during a flood can cut a household off from emergency responders even when help is nearby. Ward disaster-management officers could use this to prioritize which residential clusters need alternate access routes before the next flood season.

## The data I need

| Dataset | Source & Link | Features | Geometry Type | Key Columns | Gaps / Missing Values |
|---|---|---|---|---|---|
| Tabata Ward boundary | OpenStreetMap, via QuickOSM plugin in QGIS — https://www.openstreetmap.org/ | 1 | MultiPolygon | `Municipal`,<br>`Ward`, `Subward`,<br>`Feature`,<br>`Latitude`,<br>`Longitude` | None — single feature, fully populated |
| Buildings | HOTOSM Export Tool — https://export.hotosm.org/v3/ | 16,879 | MultiPolygon | `osm_id`,<br>`osm_type`,<br>`building` | `name` present on <1% of buildings; most optional tags (address, levels, material) empty for the majority |
| Road network | OpenStreetMap, via QuickOSM plugin in QGIS — https://www.openstreet.org/ | 564 | MultiLineString | `highway`, `name`| `name` missing on 72% (405/564), mostly unnamed footways/service roads; for segments matched to a nearby but non-identical OSM way, since not every segment had a close geometric match in the source `highway_unclassified` extract |
| Amenity | OpenStreetMap, via QuickOSM plugin in QGIS — https://www.openstreetmap.org/ | 16 | Point | `amenity`, `name`,|  Most optional tags are sparsely populated: `religion` missing on 14/16, `operator` on 15/16,|



All four datasets that I have shared are all in a single CRS — EPSG:32737 (WGS 84 / UTM Zone 37S) in my ACCESSIBILITY.qgz — so no reprojection is needed before analysis.

## What I would build

A map showing which residential buildings in Tabata Ward fall outside a 300m buffer of the paved road network, layered against nearby emergency-relevant amenities. Alongside it, a short summary table reporting the count and share of road-isolated buildings, so a ward disaster officer can see at a glance which areas to prioritize.

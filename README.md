# Tabata Ward Road Accessibility

## Spatial Question

Which residential buildings in Tabata Ward, Ilala Municipality, Dar es Salaam are located more than 300 metres from the nearest paved road, and what does this mean for their access to schools and health facilities?

Only 42 of the 564 mapped road segments in the ward (about 7%) have a paved surface (asphalt, concrete, or generic "paved"); the remaining 93% are unpaved or compacted earth. This project maps how far residential buildings sit from that thin paved network, as a proxy for reliable year-round access to services and emergency response.

## Study Area

**Tabata Ward**, Ilala Municipal Council, Dar es Salaam Region, Tanzania.
- Area: ~4.4 km²
- 2012 census population: 74,742
- Boundary source: Ramani Huria community-mapping project (mapped Oct–Nov 2015), available via OpenStreetMap — https://ramanihuria.org/en/tabata/

## Datasets

| Dataset | File | Source | Link |
|---|---|---|---|
| Ward boundary | `data/tabata_boundary.gpkg` | OpenStreetMap / Ramani Huria | https://ramanihuria.org/en/tabata/ |
| Road network | `data/roads.gpkg` | OpenStreetMap (via QuickOSM) | https://www.openstreetmap.org/copyright |
| Buildings | `data/buildings.gpkg` | OpenStreetMap (via QuickOSM) | https://www.openstreetmap.org/copyright |
| Amenities (schools) | `data/amenity.gpkg` | OpenStreetMap (via QuickOSM) | https://www.openstreetmap.org/copyright |

See [`data_note.md`](data_note.md) for feature counts, key columns, geometry types, and data quality notes for each dataset.

## Method (planned)

1. Reproject all layers to a common CRS (EPSG:32737 — UTM Zone 37S — matches roads/buildings/boundary; amenity layer needs reprojecting from EPSG:4326).
2. Select paved road segments (`surface` = asphalt, concrete, paved).
3. Buffer paved roads at 300 m.
4. Identify residential buildings (`building` = residential) falling outside the buffer.
5. Compute distance from each residential building to the nearest school and hospital.
6. Summarize and map the results within the Tabata Ward boundary.

## Tools

QGIS 3.x, QuickOSM plugin, OpenStreetMap data.

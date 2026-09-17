# Tabata Ward Road Accessibility

## Question

Which residential buildings in Tabata Ward, Ilala Municipality, Dar es Salaam are located more than 300 metres from the nearest paved road, and what does this mean for their access to schools and health facilities?

## Study Area

**Tabata Ward**, Ilala Municipal Council, Dar es Salaam Region, Tanzania.

## Datasets

| Dataset | File | Source | Link |
|---|---|---|---|
| Ward boundary | `tabata_boundary.gpkg` | OpenStreetMap | https://www.openstreetmap.org/ |
| Road network | `roads.gpkg` | OpenStreetMap (via QuickOSM) | https://www.openstreetmap.org/ |
| Buildings | `buildings.gpkg` | HotOSM | https://export.hotosm.org/v3/ |
| Amenities (schools) | `amenity.gpkg` | OpenStreetMap (via QuickOSM) |https://www.openstreetmap.org/|

See [`data_note.md`](data_note.md) for feature counts, key columns, geometry types, and data quality notes for each dataset.

## Method

1. Reproject all layers to a common CRS (EPSG:32737 — UTM Zone 37S incase of miss match).
2. Select paved road segments (`surface` = asphalt, concrete, paved).
3. Buffer paved roads at 300 m.
4. Identify residential buildings (`building` = residential) falling outside the buffer.
5. Compute distance from each residential building to the nearest school and hospital.
6. Summarize and map the results within the Tabata Ward boundary.

## Tools to be used

QGIS, QuickOSM plugin, HotOSM export tool.

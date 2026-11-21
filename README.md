# GB Renewables Dashboard

A self-contained WCAG 2.1 AA web dashboard for Great Britain electricity system data:

- Renewable share of the generation mix and carbon intensity (NESO Carbon Intensity API)
- Filterable register of major GB generating facilities (filter by generation type, supplier, facility, or combine filters with free-text search)
- Current generation mix chart and 24-hour wind, solar and carbon intensity series

## Running the app

The dashboard is a single static file with no build step and no dependencies. Either open `index.html` directly in a browser, or serve the folder:

```bash
python3 -m http.server 8080
# then visit http://localhost:8080
```

When opened from a local file or a server, the page attempts a live refresh from
`https://api.carbonintensity.org.uk/generation` and falls back to the embedded
snapshot (21 November 2026, 20:30 GMT) if the connection is unavailable.

## Data sources

| Data | Source |
| --- | --- |
| Generation mix, carbon intensity | [NESO Carbon Intensity API](https://api.carbonintensity.org.uk) |
| Facility capacities (indicative register) | NESO Data Portal and published operator figures |
| Live per-facility output | Not publicly available; would require an Elexon BMRS licence. Facility output shown is a modelled estimate. |

Covers Great Britain only; Northern Ireland is part of the SEMO market.

## GitHub Pages

To publish: repository Settings, Pages, deploy from branch `main` on `/ (root)`. The dashboard will be available at `https://<owner>.github.io/gb-renewables-dashboard/`.

## Accessibility

Built against WCAG 2.1 AA: skip link, semantic landmarks, labelled form controls, live announcements, keyboard operation with visible focus, 4.5:1 contrast, reduced-motion support. Styling follows Tabler design tokens (docs.tabler.io), inlined so the single file works offline.

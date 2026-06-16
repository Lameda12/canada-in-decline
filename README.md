# Canada in Decline — Interactive Data Essay

Interactive D3.js v7 scrollytelling dashboard making a sourced, data-accurate case that Canada has declined as a destination for immigrants, expats, students, and workers.

## Run

Requires a local server (browser blocks `fetch()` from `file://`):

```bash
python3 -m http.server 8080
```

Open `http://localhost:8080`

## Files

| File | Purpose |
|------|---------|
| `index.html` | All markup + D3 chart code. Reads from `data.json`. No hardcoded stats. |
| `data.json` | Single source of truth. Every entry: `{value, year, source, method, url}`. |

## Chapters

1. **Housing** — Numbeo price-to-income ratio, Canadian cities vs peers
2. **Immigration** — Study permit refusal rates 2023–2025 (IRCC / ICEF Monitor)
3. **Economy** — GDP per capita indexed 2015=100, Canada vs G7 peers (OECD)
4. **Healthcare** — Canadians without a primary care provider 2018–2024 (OurCare / CMA)
5. **Crime** — Violent Crime Severity Index 2009–2024 (Statistics Canada table 35-10-0026)
6. **Work** — Credential underemployment (prose; chart pending primary source verification)
7. **Alternatives** — Radar chart: Canada vs Portugal, Germany, UAE, Australia, Japan, Mexico

## Data Integrity

- Every value in `data.json` has `{value, year, source, method, url}`
- No stat appears in a chart without all five fields
- Cross-country comparisons use the same source/method within each chart
- Unverified claims appear in prose, labeled `[Unverified]`, not in charts
- Counter-context for each chapter surfaced inline

## Accessibility

- `prefers-reduced-motion`: charts render at final state, no animation
- Every chart: `role="img"` + `aria-label` + visually-hidden data table
- Nav: real `<a href="#id">` links, keyboard navigable
- Color is never the only signal (all charts carry value labels or direct text labels)

## Sources

See footer of `index.html` for the full annotated source list.

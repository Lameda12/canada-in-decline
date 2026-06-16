# Canada in Decline — Interactive Data Essay

**Live data visualization making a sourced case that Canada has declined as a destination for immigrants, expats, students, and workers.**

→ **[Open the dashboard](https://file2-iota.vercel.app)**

---

## What This Is

Seven chapters. Real data. No invented numbers.

| # | Chapter | Key Stat |
|---|---------|----------|
| 1 | **Housing** | Toronto P/I ratio 11.3× — 47% above Germany (Numbeo 2024) |
| 2 | **Immigration** | Study permit refusal rate: 38% → 52% → 58% (IRCC 2023–2025) |
| 3 | **Economy** | GDP/capita growth +1.9% (2014–2023) — worst in G7 (OECD) |
| 4 | **Healthcare** | 6.5M Canadians without a family doctor (OurCare/CMA 2022) |
| 5 | **Crime** | Violent Crime Severity Index +73% since 2014 low (StatCan) |
| 6 | **Work** | Credential underemployment — documented, chart pending source |
| 7 | **Alternatives** | Radar: Canada vs Portugal, Germany, UAE, Australia, Japan, Mexico |

Every number has `{value, year, source, method, url}`. All data lives in [`data.json`](data.json).

---

## Run Locally

```bash
git clone https://github.com/Lameda12/canada-in-decline.git
cd canada-in-decline
python3 -m http.server 8080
# open http://localhost:8080
```

Requires a local server — browser blocks `fetch()` from `file://`.

---

## Update Schedule

**This repo is updated every 6 months** (January and July) with:
- Fresh data from the same sources (Numbeo, OECD, StatCan, IRCC, CMA)
- Any new chapters warranted by developments
- Removal or flagging of claims that no longer hold

Last updated: **June 2026**
Next update: **January 2027**

If a number is wrong or a source has been corrected, open an issue.

---

## Data Integrity

- Every chart value traces to a primary or well-cited secondary source
- Cross-country comparisons use the same source/method within each chart
- Unverified claims are in prose, labeled `[Unverified]`, not in charts
- Counter-context for every chapter — the rebuttal is shown, not hidden

---

## Stack

Vanilla HTML + D3.js v7 (CDN). No build step. No framework. One `index.html`, one `data.json`.

---

## Sources

Statistics Canada · OECD · IRCC · Numbeo · Demographia · OurCare/CMA · Commonwealth Fund · ICEF Monitor · Trevor Tombe/The Hub · Expat Insider

Full annotated list in the dashboard footer.

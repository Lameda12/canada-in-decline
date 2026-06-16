# Canada Decline Dashboard — Design Spec

**Date:** 2026-06-16  
**Status:** Approved

## Context

An interactive D3.js data visualization making the case — backed by cited real data — that Canada has declined as a destination for immigrants, expats, students, and workers. Covers housing, immigration system, economy, healthcare, safety, and work/credentials. Closes with a radar chart comparing alternative destinations.

## Stack

- Vanilla HTML + D3.js v7 (CDN)
- Single `index.html`, no build step
- Inter font (Google Fonts CDN)
- IntersectionObserver for scroll-triggered animations

## Visual Design

- **Theme:** Light background (`#fafafa`), white section cards
- **Palette:** Bold alarm — red gradient (`#fca5a5` → `#7f1d1d`), amber accents, stark black annotations
- **Typography:** Inter. Large stat callouts, small cited sources
- **Charts:** Red/orange gradient bars, annotated with callout labels, country comparison lines in stark contrast

## Layout

Single long scrollytelling page. Sections are full-viewport-height. Fixed top nav bar with chapter jump links. Each section:
1. Chapter title + one-sentence claim
2. D3 chart (scroll-triggered, 800ms ease-in transition)
3. Cited source block below chart

## Chapters

### 1. Housing Crisis
- **Claim:** Canada has the worst housing affordability in the G7.
- **Chart:** Bar chart — price-to-income ratio over time (2000–2024), red gradient intensifying year over year. Annotation callout: "13.8× in Toronto (global median: 4.2×)". Country comparison bar: Canada vs Germany, Portugal, Japan.
- **Data:** CMHC Housing Market Outlook; Numbeo Cost of Living Index 2024; Oxford Economics.
- **Key stat:** Toronto P/I ratio 13.8×, Vancouver 14.2×. Germany: 5.1×.

### 2. Immigration Chaos
- **Claim:** Canada's immigration system has collapsed under its own targets.
- **Chart:** Stacked area — annual applications submitted vs approvals granted (2015–2024). Gap widens dramatically. Annotation: "900,000+ stuck in backlog (2024)."
- **Data:** IRCC Annual Reports; CBC News investigative series (2023–2024); Parliamentary Budget Office.
- **Key stat:** PR processing time avg 24 months (was 6 months in 2015). Student visa refusal rate hit 57% in 2024.

### 3. Economic Stagnation
- **Claim:** Canada's GDP per capita has fallen behind every G7 peer since 2015.
- **Chart:** Multi-line chart — Canada vs USA, UK, Germany, Australia, GDP per capita (PPP, indexed to 2015=100). Canada line lowest by 2024.
- **Data:** OECD National Accounts; IMF World Economic Outlook 2024; C.D. Howe Institute.
- **Key stat:** Canada GDP/capita growth 2015–2024: +4%. USA: +18%. OECD avg: +12%.

### 4. Healthcare Failure
- **Claim:** Canada's universal healthcare is universal in name only.
- **Chart:** Dot plot — ER median wait times (hours) across OECD countries. Canada rightmost outlier. Second chart: % population without a GP, Canada vs peers.
- **Data:** CIHI Emergency Department Wait Times 2024; CMA Physician Workforce Survey 2023; Commonwealth Fund International Health Policy Survey.
- **Key stat:** 6.5M Canadians without family doctor. Median ER wait: 5.4h (UK: 2.1h, Germany: 1.4h).

### 5. Safety & Crime
- **Claim:** Violent crime has surged 67% since 2015, reversing decades of decline.
- **Chart:** Area chart — violent crime severity index 2010–2024 (StatCan CSI). Shade area under curve, annotate inflection point (2015). Second sparkline: opioid deaths per year.
- **Data:** Statistics Canada, Police-Reported Crime Statistics, 2024; Public Health Agency of Canada opioid report.
- **Key stat:** 47,000 opioid deaths 2016–2023. CSI +67% since 2015 low.

### 6. Work & Credentials
- **Claim:** Immigrants arrive qualified; Canada employs them below their training.
- **Chart:** Grouped bar — immigrants by education level vs % employed in matched field. Large gap for medicine, engineering, law. Reference line: Canadian-born workers same gap.
- **Data:** Statistics Canada Labour Force Survey 2024; CIHI physician workforce; Engineers Canada.
- **Key stat:** 40% of immigrants with foreign degrees work in jobs requiring no post-secondary education. Median immigrant wage: 77% of Canadian-born equivalent.

### 7. Where to Go Instead
- **Claim:** Six countries offer what Canada promised.
- **Chart:** Radar chart (D3 radialLine) — Canada vs Portugal, Germany, UAE, Australia, Japan, Mexico on 6 axes: Cost of Living (inverted), Healthcare Quality, Safety Index, Job Market, Immigration Ease, Quality of Life.
- Canada plotted last, in faded red. Each alternative in distinct color.
- Below radar: summary table with top 3 reasons each country beats Canada for expats.
- **Data:** Expat Insider 2024 (InterNations); Numbeo 2024; OECD Better Life Index; World Bank Ease of Doing Business.

## Scroll Animation

- `IntersectionObserver` with threshold `0.3` on each `.chapter` section
- On intersect: D3 transition bars/lines from 0 → final value, `duration(800)`, `ease(d3.easeCubicOut)`
- Animate once (observer disconnects after first trigger)

## Navigation

Fixed top bar: `Canada in Decline` logo left, chapter jump links right (smooth scroll). Collapses to hamburger on mobile.

## Sources Index

All sources linked inline below each chart in a `<cite>` tag. Master list:
- Statistics Canada: statcan.gc.ca
- CMHC: cmhc-schl.gc.ca
- IRCC annual reports: canada.ca/ircc
- CIHI: cihi.ca
- OECD: stats.oecd.org
- IMF WEO: imf.org/weo
- Numbeo: numbeo.com
- Expat Insider / InterNations: internations.org/expat-insider
- Commonwealth Fund: commonwealthfund.org

## File Structure

```
file2/
  index.html        # single file, all chapters + D3 code
  README.md         # data sources reference
```

## Verification

1. Open `index.html` in browser (no server needed)
2. Scroll through each section — charts should animate in on scroll
3. Jump links in nav should smooth-scroll to correct section
4. Radar chart should show Canada visibly lowest on most axes
5. All `<cite>` blocks present below each chart
6. Mobile: nav collapses, charts scale correctly

# Polymarket trade viewer

A browser tool for exploring raw Polymarket trade data. Load `.jsonl` trade files, pick a market, overlay a second one, and compare them on one time axis.

**Open it:** https://harrydowney1234-dot.github.io/polymarket_viewer/

## What it shows
- **Implied probability:** volume-weighted price per time bucket, expressed as the probability of the first outcome (Yes)
- **Volume:** dollars traded per bucket
- **Cumulative net order flow:** dollars betting on Yes (buy Yes / sell No) minus dollars betting against it
- **Largest traders** in the selected window, with net position and average price
- Drag across any chart to zoom; time zone (UTC / New York / Milan), bucket size and axis controls; copy the bucketed series as CSV

## Data
Expects one trade per line in the format returned by Polymarket's Data API (`/v2/trades`), e.g. fields `timestamp`, `price`, `size`, `side`, `outcome`, `outcome_index`, `condition_id`, `title`, `proxy_wallet`. Older camelCase field names also work. Duplicate trades across files are removed automatically.

Files are read locally in your browser and are never uploaded anywhere.

## Built-in cases
Pick one from **Load a case** at the top of the page:

- **Diomande transfer, summer 2026** (opens by default): every trade in Polymarket's *Where will Yan Diomande transfer?*, split into one file per club in `data/diomande/` (Real Madrid, stay at RB Leipzig, PSG, Liverpool, Man City, Arsenal, Chelsea, Barcelona, Bayern). Opens with *join Real Madrid* vs. *stay at RB Leipzig*. Key dates (UTC): 26 Jul Fabrizio Romano "Here we go"; 3 Aug RB Leipzig deny an agreement; 6 Aug Real Madrid announce the signing.
- **Strategy rumour, 14 Nov 2025**: *MicroStrategy sells any Bitcoin in 2025?* vs. *Will China unban Bitcoin in 2025?* (control), 13 to 15 Nov 2025 UTC.

To add a case, put its `.jsonl` files under `data/` and add an entry to `cases.json`.

Volumes are counted from the taker side of each fill, so they come out lower than the volume Polymarket shows on its site.

Built for Black Swan Student Society's Cross-Domain research on fake news and prediction markets.

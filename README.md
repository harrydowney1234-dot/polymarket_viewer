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

The page opens with a sample: the 14 Nov 2025 Strategy fake-news case (*MicroStrategy sells any Bitcoin in 2025?* vs. *Will China unban Bitcoin in 2025?* as a control), trades from 13 to 15 Nov 2025 UTC.

Built for Black Swan Student Society's Cross-Domain research on fake news and prediction markets.

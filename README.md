# WanderBricks Investor Analysis

## Goal

Determine which countries are the most attractive markets for purchasing residential property to rent out, based on rental income, demand stability, and property market trends.

The analysis is built on the WanderBricks rental platform dataset, covering 18 countries and approximately 16,000 properties across 2023–2025.

---

## Approach

The main question — *where should an investor buy property for rental income?* — was broken down into five measurable areas:

### 1. Profitability and financial performance
- Average rental revenue by country
- Average nightly rate
- Booking counts by country and year
- Years to Break-Even Point (BEP) for cash purchases — Investment ÷ annual cash flow (no debt service ratio, since no financing is involved)

**Answers:** Where does invested capital generate the highest return relative to property cost, and how long until it pays for itself?

### 2. Tenant behavior and retention
- Average rental duration by country and bookings per year
- Booking growth/decline trend across countries, filterable per country

**Answers:** Is rental demand stable and predictable, or is the market shrinking?

### 3. Demand and seasonality
- Booking volume during peak season, by country
- Total bookings by season, across all countries

**Answers:** Is income spread evenly across the year, or concentrated in a few months with long vacancy periods?

### 4. Property market
- Property price trend — growth or stagnation over 2023–2025 (OECD, 13 countries)
- Average price per square meter in city centre, by country
- Property supply growth — number of listed properties per country and year

**Answers:** Beyond rental income, can the investor expect capital appreciation — and is the market getting more crowded?

### 5. Final recommendation
- Country-level recommendation for buying rental property, weighing profitability, demand stability and price trend
- Investment and financing scenarios built on the metrics above

**Answers:** Given everything, where should the money go — and under what terms?

---

## Data sources

| Source | Content | Coverage |
|---|---|---|
| `samples.wanderbricks` | Bookings, properties, hosts, reviews — the platform's operational data | 18 countries, 2023–2025 |
| OECD SDMX API | Real house price index (2015 = 100), quarterly | 13 of 18 countries |
| Numbeo | Current price per m² to buy an apartment in city centre (EUR) | All 18 countries |

## Known limitations

- OECD data covers only member and partner economies — Thailand, Egypt, China, UAE and Singapore are missing
- Numbeo provides a current snapshot, not a historical series, so absolute prices are static across years
- The WanderBricks dataset is synthetic; several findings (uniform revenue across countries, ~1.5 bookings per property) are artifacts of data generation rather than market signals

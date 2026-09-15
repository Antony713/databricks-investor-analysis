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
- Years to Break-Even Point (BEP) for cash purchases — Investment ÷ annual cash flow

### 2. Tenant behavior and retention
- Average rental duration by country and bookings per year
- Average bookings per property

### 3. Demand and seasonality
- Booking volume by season, per country
- Each season's share of a country's bookings

### 4. Property market
- Current price per m² in city centre, by country
- Property supply growth per country and year

### 5. Final recommendation
- Country-level ranking combining cost, demand and break-even

---

## Data sources

| Source | Content | Coverage |
|---|---|---|
| `samples.wanderbricks` | Bookings, properties, hosts — the platform's operational data | 18 countries, 2023–2025 |
| OECD SDMX API | Real house price index | 13 of 18 countries |
| Numbeo | Current price per m² to buy an apartment in city centre (EUR) | All 18 countries |

---

## Gold tables

| Table | Description |
|---|---|
| `gold_host_performance` | Host activity: properties, bookings and revenue per host (2024 onwards) |
| `gold_bookings_by_year` | Booking counts per year — used to scope the property price data |
| `gold_revenue_and_pricing_by_country` | Revenue per property, nightly rate and booking counts by country and year |
| `gold_rental_duration_and_trends` | Average rental duration and booking growth by country and year |
| `gold_seasonal_demand` | Booking counts by season, per country and overall |
| `gold_real_estate_market` | House price index (OECD) and price per m² (Numbeo) |
| `gold_avg_revenue_per_booking_by_property` | Average revenue per booking, by individual property |
| `gold_avg_bookings_per_property` | Average booking volume per property — daily, weekly, monthly |
| `gold_break_even_point` | Years to recover a cash property purchase (70 m² assumption) |
| `gold_property_supply_growth` | Listed properties per country and year, with growth rate |

---

## Dashboard

**Page 1 — Host Performance**

![Host Performance](screenshots/Host%20Performance.png)

Activity concentrates in a handful of markets. The US has the most hosts (554), but Spain leads on bookings and revenue (€11M) with only 205 hosts.

---

**Page 2 — Profitability**

![Profitability](screenshots/Profitability.png)

Revenue per property lands between €540 and €820 across all 18 countries. Booking volume varies far more than revenue does.

---

**Page 3 — Tenant Behavior**

![Tenant Behavior](screenshots/Tenant%20Behavior.png)

Rental duration sits at 3.3–4.2 nights everywhere, and each property averages 1.3 bookings. Platform bookings grew from near zero to 15K over three years.

---

**Page 4 — Seasonality**

![Seasonality](screenshots/Seasonality.png)

Summer dominates almost universally — Spain books 78% of its year in one season. UAE and Japan spread demand more evenly.

---

**Page 5 — Property Market**

![Property Market](screenshots/Property%20Market.png)

Property cost varies 30×, from €756/m² in Egypt to €23,344/m² in Singapore. Supply roughly doubled each year in every market.

---

**Page 6 — Recommendation**

![Recommendation](screenshots/Recommendation.png)

Egypt and India offer the fastest payback on cost alone, but with thin booking volume. Spain and Thailand combine mid-range prices with the strongest demand.

---

## Important: working with synthetic data

The WanderBricks dataset is synthetic. Several patterns in the results are artifacts of data generation rather than market signals, and the analysis is presented with that in mind.

**What the data shows:**

- Each property records ~1.3 bookings across the entire 2023–2025 period, producing annual cash flow near €700 instead of the €10,000–30,000 a real rental would generate
- Revenue per booking sits between €539 and €575 across all 18 countries — a 6% spread, where real markets differ by an order of magnitude
- Break-even figures therefore run 3–100× longer than reality: 73 years for Egypt, 2,567 for Switzerland, against a realistic 15–30 years
- Booking growth from 2023 to 2025 reflects platform adoption, not market expansion

**What remains valid:**

Relative rankings between countries. Every market is distorted the same way, so the ordering — which countries offer better cost-to-income ratios, stronger demand, or higher vacancy risk — still holds. Absolute figures do not.

**Additional assumptions:**

- Property value is estimated as 70 m² × price per m², since the dataset has no property size field
- Numbeo provides a current snapshot, not a historical series, so property prices are static across years
- Rental income derives from short-term booking data, while property prices reflect long-term purchase values

---

## Repository contents

- `investor_questions_analysis_2026_v01-Git.ipynb` — Databricks notebook with all SQL and Python queries
- `wanderbricks_investor_analysis.pbix` — Power BI dashboard
- `README.md` — this file

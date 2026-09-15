# WanderBricks Investor Analysis

Which countries are the most attractive markets for buying residential property to rent out?

Built on the WanderBricks rental platform dataset — 18 countries, ~16,000 properties, 2023–2025.

---

## Approach

1. **Profitability** — rental revenue, nightly rates, booking counts, and years to break-even for cash purchases
2. **Tenant behavior** — rental duration and bookings per property
3. **Seasonality** — booking distribution across seasons, per country
4. **Property market** — price per m² and supply growth
5. **Recommendation** — country ranking combining cost, demand and break-even

---

## Data sources

| Source | Content | Coverage |
|---|---|---|
| `samples.wanderbricks` | Bookings, properties, hosts | 18 countries, 2023–2025 |
| OECD SDMX API | Real house price index | 13 of 18 countries |
| Numbeo | Price per m² in city centre (EUR) | All 18 countries |

---

## Gold tables

| Table | Description |
|---|---|
| `gold_host_performance` | Properties, bookings and revenue per host |
| `gold_bookings_by_year` | Booking counts per year |
| `gold_revenue_and_pricing_by_country` | Revenue, nightly rate and bookings by country and year |
| `gold_rental_duration_and_trends` | Rental duration and booking growth |
| `gold_seasonal_demand` | Bookings by season |
| `gold_real_estate_market` | House price index and price per m² |
| `gold_avg_revenue_per_booking_by_property` | Revenue per booking, by property |
| `gold_avg_bookings_per_property` | Bookings per property — daily, weekly, monthly |
| `gold_break_even_point` | Years to recover a cash purchase (70 m² assumption) |
| `gold_property_supply_growth` | Listed properties per country and year |

---

## Dashboard

**Host Performance**

![Host Performance](screenshots/host-performance.png)

The US has the most hosts (554), but Spain leads on bookings and revenue (€11M) with only 205.

---

**Profitability**

![Profitability](screenshots/profitability.png)

Revenue per property lands between €540 and €820 across all 18 countries. Booking volume varies far more than revenue does.

---

**Tenant Behavior**

![Tenant Behavior](screenshots/tenant-behavior.png)

Rental duration sits at 3.3–4.2 nights everywhere, and each property averages 1.3 bookings.

---

**Seasonality**

![Seasonality](screenshots/seasonality.png)

Summer dominates almost universally — Spain books 78% of its year in one season. UAE and Japan spread demand more evenly.

---

**Property Market**

![Property Market](screenshots/rroperty-market.png)

Property cost varies 30×, from €756/m² in Egypt to €23,344/m² in Singapore. Supply roughly doubled each year.

---

**Recommendation**

![Recommendation](screenshots/recommendation.png)

Egypt and India offer the fastest payback on cost alone, but with thin booking volume. Spain and Thailand combine mid-range prices with the strongest demand.

---

## Working with synthetic data

The dataset is synthetic, and several patterns are artifacts of data generation rather than market signals:

- Each property records ~1.3 bookings across 2023–2025, giving annual cash flow near €700 instead of a realistic €10,000–30,000
- Revenue per booking spans only €539–575 across all countries, where real markets differ by an order of magnitude
- Break-even figures run 3–100× too long: 73 years for Egypt, 2,567 for Switzerland, against a realistic 15–30
- Booking growth 2023–2025 reflects platform adoption, not market expansion

**Relative rankings still hold** — every market is distorted the same way. Absolute figures don't.

Other assumptions: property value estimated as 70 m² × price per m² (no size field in the data); Numbeo prices are a current snapshot, static across years.

---

## Contents

- `investor_questions_analysis_2026_v01-Git.ipynb` — Databricks notebook
- `wanderbricks_investor_analysis.pbix` — Power BI dashboard

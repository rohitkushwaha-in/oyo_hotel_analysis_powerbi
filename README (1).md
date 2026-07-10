# OYO Hotels — Price, Rating & Value Analysis Dashboard

A Power BI dashboard analyzing OYO Hotels' portfolio, customer ratings, and pricing/discount strategy across cities in India, built from a two-table dataset (hotel-level attributes + individual customer reviews).

## Project Overview

This project explores a core question in the budget hotel space: **does discounting and pricing strategy actually align with customer satisfaction?**

The dashboard is built across three pages — portfolio overview, ratings/geography trends, and a price-vs-rating value analysis — using OYO's brand color palette for a client-ready visual identity.

## Dataset

Two related tables joined on `hotel_id`:

**Hotel_Information**
- Hotel Name, Is New, Total No. Of Rating (Count), Price, Original Price, Discount (e.g. "64% off")

**Customer_Reviews**
- hotel_id, username, review text, date, review point (1–5), location (city)

## Data Cleaning & Prep

- Parsed `Discount` text into numeric `Discount_Pct`
- Parsed `Price` / `Original Price` into numeric columns
- Built `Price_Band` (Budget / Mid / Premium) using data-driven quantiles on **post-discount price**, not listed/original price — since that's what customers actually pay
- Built `Discount_Band` in 6 ranges (30–40%, 41–50%, ... 81–93%) to match the dataset's actual discount range, rather than generic 0–100% bins
- Checked for hotel_id mismatches between tables and duplicate reviews
- Verified whether `Total No. Of Rating` (listed count) matches actual review row counts per hotel

## Key Measures (DAX)

```dax
Avg Rating = AVERAGE(Reviews[review point])
Total Reviews = COUNTROWS(Reviews)
Total Hotels = DISTINCTCOUNT(Reviews[hotel_id])
Avg Price = AVERAGE(Hotels[Price_Numeric])
Avg Discount % = AVERAGE(Hotels[Discount_Pct])

% Positive Reviews = DIVIDE(CALCULATE(COUNTROWS(Reviews), Reviews[review point] >= 4), [Total Reviews])
% Negative Reviews = DIVIDE(CALCULATE(COUNTROWS(Reviews), Reviews[review point] <= 2), [Total Reviews])

Value Score = DIVIDE([Avg Rating], Hotels[Price_Numeric]) * 100
```

## Dashboard Structure

### Page 1 — Portfolio Snapshot
KPI cards (Total Hotels, Total Reviews, Avg Rating, Avg Price), hotel count by price band, new vs existing listing split, and discount band vs average rating.

### Page 2 — Ratings Over Time & Geography
Rating trend over time, review volume vs rating over time, average rating by city, and rating sentiment mix (Promoter/Passive/Detractor) by city.

### Page 3 — Value for Money: Price vs Rating
- Scatter: Price vs Rating (bubble size = review volume)
- Scatter, small multiples by city: Price vs Rating controlled for city
- Clustered bar: New vs Existing hotel average ratings
- Table: lowest value-for-money hotels, ranked by Value Score

## Key Finding: Simpson's Paradox Check

The dashboard specifically tests whether the overall Price-vs-Rating relationship holds up once controlled by city. A relationship that looks flat or negative in aggregate can reverse or strengthen within individual cities — this page is built to surface that rather than take the aggregate number at face value.

*(Fill in your actual finding here once confirmed, e.g.: "Aggregate data shows no clear price-rating relationship, but within most individual cities, higher-priced hotels do rate meaningfully better — the aggregate trend is masked by cross-city price differences.")*

## Design

Built using OYO's brand palette for visual consistency:

| Role | Hex |
|---|---|
| Primary (OYO Red) | `#EE2737` |
| Dark / Text | `#1A1A1A` |
| Background Grey | `#F2F2F2` |
| White | `#FFFFFF` |
| Muted Red (secondary series) | `#F8B4B9` |

## Tools Used

- Power BI Desktop (Power Query M, DAX, data modeling)
- Python / pandas (data cleaning and quantile checks, if used pre-load)

## Files

- `oyo_dashboard.pbix` — Power BI file
- `Hotel_Information.csv`, `Customer_Reviews.csv` — source data (or link if not included for size/privacy)

## Author

Rohit — [add LinkedIn / portfolio link here]

---

*This project is part of a portfolio series focused on data analysis, dashboarding, and reporting for real-world business questions in the hospitality/creator-economy data space.*

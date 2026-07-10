# 🏨 OYO Hotels — Price, Rating & Value Analysis Dashboard

## 📌 Project Overview

This project presents an interactive **Power BI dashboard** built to analyze OYO Hotels' portfolio, customer ratings, and pricing/discount strategy across cities in India, and to uncover whether discounting and pricing actually align with customer satisfaction.

The dashboard was developed using **Microsoft Power BI**, **Power Query**, and **DAX**, following an end-to-end Business Intelligence workflow—from data cleaning and modeling to visualization and storytelling.

---

## 🎯 Project Objectives

- Analyze OYO's overall hotel portfolio composition
- Identify pricing and discount patterns across the listing base
- Measure customer rating trends over time and across cities
- Study the relationship between price, discount, and rating
- Test whether an aggregate price-rating trend holds up city-by-city (Simpson's Paradox check)
- Surface the lowest value-for-money hotels for reporting

---

## 📂 Dataset

The dataset consists of two related tables joined on `hotel_id`.

**Table 1 — Hotel_Information**
- Hotel Name
- Is New
- Total No. Of Rating (Count)
- Price
- Original Price
- Discount (e.g. "64% off")
- hotel_id

**Table 2 — Customer_Reviews**
- hotel_id
- Username
- Review Text
- Date
- Review Point (1–5)
- Location (City)

---

## 🛠️ Data Preparation

The dataset was cleaned and transformed using **Power Query**.

### Transformations Performed

- Parsed `Discount` text (e.g. "64% off") into numeric `Discount %`
- Parsed `Price` and `Original Price` into numeric columns
- Created `Price_Category` (Budget / Mid / Premium) using data-driven quantiles on post-discount price
- Created `Discount_Band` in 6 ranges matched to the dataset's actual 30–93% spread
- Created `Review_Month`, `Review_Year` from the review date
- Checked for hotel_id mismatches between the two tables
- Checked for duplicate reviews
- Verified listed `Total No. Of Rating` against actual review row counts per hotel

---

## 📈 DAX Measures

The following measures were created for analysis:

- Total Hotels
- Total Reviews
- Avg Rating
- Avg Price
- Avg Discount %


---

# 📊 Dashboard Pages

## 1️⃣ Portfolio Snapshot

### Purpose

Provides an overview of the overall hotel portfolio.

### Visuals

- KPI Cards
  - Total Hotels
  - Total Reviews
  - Avg Rating
  - Avg Price

- Bar Chart
  - Hotels by Price Band

- Donut Chart
  - New vs Existing Listings

- Bar Chart
  - Discount Band vs Average Rating

---

## 2️⃣ Ratings Over Time & Geography

### Purpose

Understand how ratings trend over time and vary by location.

### Visuals

- Line Chart
  - Average Rating Trend

- Line/Bar Combo
  - Review Volume vs Rating Over Time

- Bar Chart
  - Average Rating by City

- Stacked Bar Chart
  - Rating Sentiment Mix (Promoter/Passive/Detractor) by City

---

## 3️⃣ Value for Money: Price vs Rating

### Purpose

Analyze whether price and discount actually correspond to customer satisfaction.

### Visuals

- Scatter Plot
  - Price vs Rating (bubble size = review volume)

- Scatter Plot (Small Multiples by City)
  - Price vs Rating — Controlled by City

- Clustered Bar Chart
  - New vs Existing Hotel Ratings

- Table
  - Lowest Value-for-Money Hotels (sorted by Value Score)

---

# 🔍 Key Finding: Simpson's Paradox Check

The dashboard specifically tests whether the overall Price-vs-Rating relationship holds up once controlled by city. A relationship that looks flat or weak in aggregate can reverse or strengthen within individual cities — Page 3 is built to surface that rather than take the aggregate number at face value.

> *(Insert your confirmed finding here, e.g.: "Aggregate data shows little price-rating relationship, but within most individual cities, higher-priced hotels rate meaningfully better — the city-level effect is masked in the combined view.")*

---

# 📊 Dashboard Preview

> **Add your dashboard screenshots here after uploading them.**

```
Dashboard_Screenshots/
│
├── Page1_Portfolio_Snapshot.png
├── Page2_Ratings_Geography.png
└── Page3_Value_Analysis.png
```

---

# 🧰 Tools & Technologies

- Microsoft Power BI
- Power Query
- DAX
- Data Modeling
- Data Visualization
- Git & GitHub

---

# 📁 Repository Structure

```
oyo-hotels-price-rating-analysis-powerbi/
│
├── README.md
├── OYO_Hotels_Analysis.pbix
├── Hotel_Information.csv
├── Customer_Reviews.csv
├── Dashboard_Screenshots/
│   ├── Page1_Portfolio_Snapshot.png
│   ├── Page2_Ratings_Geography.png
│   └── Page3_Value_Analysis.png
└── LICENSE
```

---

# 🚀 Skills Demonstrated

- Data Cleaning
- Data Transformation
- Power Query
- DAX Calculations
- Data Modeling
- Dashboard Design
- Business Intelligence
- Data Visualization
- Analytical Storytelling

---

# 📌 Future Improvements

- Add drill-through pages by hotel
- Implement Row-Level Security (RLS) by city
- Publish the dashboard to Power BI Service
- Connect the dashboard to a live database
- Automate data refresh using scheduled refresh

---

# 🤝 Connect With Me

If you enjoyed this project or have suggestions for improvement, feel free to connect with me.

- 💼 LinkedIn: https://www.linkedin.com/in/rohit-kushwaha-3482153b0/
- 📧 Email: rohit0614kushwaha@gmail.com

---

## ⭐ If you found this project helpful, consider giving it a star!

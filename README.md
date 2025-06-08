# Zomato-Analysis-Power-bi-project
Zomato project analyzing restaurant data globally: continents, costs, ratings, cuisines, drill-downs, filters, multi-page design for mobile + web.

## High-Level Steps
- Data import from multiple Excel files
- Data cleaning: fix city names, remove unused columns, split name/address
- Dim tables: extract cuisines, ensure unique CountryCode/Continent
- Build relations with correct cardinality & direction
- Geo‑hierarchy & continent grouping

## DAX Measures
1. Total countries = DISTINCTCOUNT('Country Master'[Country])
2. Average rating = AVERAGE(KPIs[Aggregate rating])
3. Customer rating text = 
   SWITCH(
        TRUE(),
        KPIs[Aggregate rating] >= 4.5 && KPIs[Aggregate rating] <= 4.9, "Excellent",
        KPIs[Aggregate rating] >= 4.0 && KPIs[Aggregate rating] <= 4.4, "Very Good",
        KPIs[Aggregate rating] >= 3.5 && KPIs[Aggregate rating] <= 3.9, "Good",
        KPIs[Aggregate rating] >= 2.5 && KPIs[Aggregate rating] <= 3.4, "Average",
        KPIs[Aggregate rating] >= 1.8 && KPIs[Aggregate rating] <= 2.4, "Poor",
        "Not Rated"
   )
4.  Highest Average customer Rating = 
   MAXX(
        VALUES('Zomato global'[Restaurant ID]),
        CALCULATE(AVERAGE(KPIs[Aggregate rating]))
   ) 
5.  Restaurant Cost Rank = 
RANKX(
    ALL('Zomato global'[Restaurant ID]),
    CALCULATE(AVERAGE(KPIs[Average Cost for two])),
    ,
    DESC
)

## Key Insights:

1. Zomato Global Insights Overview

India dominates the Zomato platform with the highest number of registered restaurants and cities served globally.

The platform's primary engagement is concentrated in a few major countries, showing a regional concentration of operations.

Cities like New Delhi and Bangalore contribute significantly to Zomato’s user and restaurant density.

The majority of restaurants offer multiple cuisines, showing Zomato’s diverse food offerings.

Restaurant availability and activity are heavily skewed toward urban and metro regions.

2. Zomato Global Footprints Overview
   
Zomato operates across multiple continents but is most active in Asia, especially South Asia.

A handful of countries account for the majority of Zomato’s data points, suggesting a focus on high-demand markets.

The heatmap of country-wise restaurant density reveals strategic targeting in population-dense regions.

Countries with high GDP and urbanization seem to correlate with higher Zomato presence.

The platform’s reach is gradually expanding into underrepresented regions such as parts of Africa and Latin America.

3. Worldwide Analysis

The distribution of restaurants varies widely across continents, with Asia leading significantly.

The continent-wise comparison reveals that while Zomato has a presence globally, user behavior and restaurant categories differ by region.

Countries like the USA, India, and Australia show varied food preferences, impacting menu and cuisine popularity.

The analysis highlights how regional culture influences restaurant ratings, pricing, and availability.

Data reveals a clear digital food footprint pattern—showing how Zomato’s growth aligns with smartphone penetration and food delivery trends.

4.  Restaurants Analysis

Quick Bites and Casual Dining are the most dominant restaurant types on the Zomato platform.

Price ranges vary by restaurant type, with Fine Dining and Cafés generally being the most expensive categories.

Ratings tend to be higher for restaurants offering fewer, specialized cuisines, indicating focused quality.

Restaurants with online delivery services tend to attract higher footfall and better ratings.

There’s a visible trend of mid-range pricing with higher review volumes, indicating affordability drives user engagement.

## 🛠 File Structure
- `Zomato_Dashboard.pbix` – Power BI report
- `high_level_steps.md` – ETL & modeling steps
- `dax_measures.md` – DAX queries
- `images/` – visuals screenshots
- `data_description.md` – dataset details (if any)

# Zomato-Analysis-Power-bi-project
Zomato is a restaurant search and discovery service. Operating in several countries worldwide, they
provide detailed information and customer reviews of various restaurants. The owners of Zomato,
want to unearth
the hidden anomalies in their business data. The final objective is to analyze the data in a way which
helps them to accurately judge their business performance.

## My Task

As a hypothetical applicant for this role, I was tasked with:

Writing dax to find the solution.

Creating a dashboard to showcase these insights, targeting top-level management.

## My Approach

1. Data Extraction with EXCEL, POWER BI:

- Used POWER BI to write queries and fetch the needed data.
  
2. Data Visualization:

- Used Power BI to create visuals that made the insights easy to understand and engaging.

3. Presentation Design:

Created a clear and professional dashboard in POWER BI to share the insights.

4. Actionable Insights:

- Provided actionable insights and recommendations to assist the management team in making informed decisions.


## DAX Measures
Total countries = DISTINCTCOUNT('Country Master'[Country])
   
Average rating = AVERAGE(KPIs[Aggregate rating])

Customer rating text = 

SWITCH(

        TRUE(),
        
        KPIs[Aggregate rating] >= 4.5 && KPIs[Aggregate rating] <= 4.9, "Excellent",
        
        KPIs[Aggregate rating] >= 4.0 && KPIs[Aggregate rating] <= 4.4, "Very Good",
        
        KPIs[Aggregate rating] >= 3.5 && KPIs[Aggregate rating] <= 3.9, "Good",
        
        KPIs[Aggregate rating] >= 2.5 && KPIs[Aggregate rating] <= 3.4, "Average",
        
        KPIs[Aggregate rating] >= 1.8 && KPIs[Aggregate rating] <= 2.4, "Poor",
        
        "Not Rated"
   
   )
   
Highest Average customer Rating = 

 MAXX(
        
        VALUES('Zomato global'[Restaurant ID]),
        
        CALCULATE(AVERAGE(KPIs[Aggregate rating]))
   
   ) 
   
Restaurant Cost Rank =
  
RANKX(

    ALL('Zomato global'[Restaurant ID]),
    
    CALCULATE(AVERAGE(KPIs[Average Cost for two])),
    
    ,
    
    DESC

)

## Key Insights:

1. Zomato Global Insights Overview:

India dominates the Zomato platform with the highest number of registered restaurants and cities served globally.

The platform's primary engagement is concentrated in a few major countries, showing a regional concentration of operations.

Cities like New Delhi and Bangalore contribute significantly to Zomato’s user and restaurant density.

The majority of restaurants offer multiple cuisines, showing Zomato’s diverse food offerings.

Restaurant availability and activity are heavily skewed toward urban and metro regions.

2. Zomato Global Footprints Overview:
   
Zomato operates across multiple continents but is most active in Asia, especially South Asia.

A handful of countries account for the majority of Zomato’s data points, suggesting a focus on high-demand markets.

The heatmap of country-wise restaurant density reveals strategic targeting in population-dense regions.

Countries with high GDP and urbanization seem to correlate with higher Zomato presence.

The platform’s reach is gradually expanding into underrepresented regions such as parts of Africa and Latin America.

3. Worldwide Analysis:

The distribution of restaurants varies widely across continents, with Asia leading significantly.

The continent-wise comparison reveals that while Zomato has a presence globally, user behavior and restaurant categories differ by region.

Countries like the USA, India, and Australia show varied food preferences, impacting menu and cuisine popularity.

The analysis highlights how regional culture influences restaurant ratings, pricing, and availability.

Data reveals a clear digital food footprint pattern—showing how Zomato’s growth aligns with smartphone penetration and food delivery trends.

4.  Restaurants Analysis:

Quick Bites and Casual Dining are the most dominant restaurant types on the Zomato platform.

Price ranges vary by restaurant type, with Fine Dining and Cafés generally being the most expensive categories.

Ratings tend to be higher for restaurants offering fewer, specialized cuisines, indicating focused quality.

Restaurants with online delivery services tend to attract higher footfall and better ratings.

There’s a visible trend of mid-range pricing with higher review volumes, indicating affordability drives user engagement.

## Outcome
This project showed that I can handle complex data and share insights in a clear and interesting way. It helped me improve both my technical skills and my ability to explain things well.

This project highlights my skills in data analysis, data visualization, and presentation design by via dashboard in a business setting. It demonstrates my ability to extract and present actionable insights from data, supporting data-driven decision-making in a corporate environment.

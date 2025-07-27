# Uber Fares Data Analysis Report

**Prepared by:** Munezero Irakoze Luccin

**ID:** 25815

**Course:** Introduction to big data

**Instructor:** Eric MANIRAGUHA 

**Submission Date:** July 27, 2025  

---

## 1. Introduction

This report provides a structured analysis of Uber fare data focused on uncovering demand trends, pricing behavior, and service performance. A rigorous data cleaning and feature engineering pipeline was applied to ensure analytical accuracy before visualization and insight generation.

---

## 2. Dataset Overview

- **Source:** Kaggle – Uber Fares Dataset  
- **Record Count:** ~65,000 trip records  
- **Time Span:** 2009 to mid-2016  
- **Key Variables:**
  - `fare_amount`  
  - `pickup_datetime`  
  - Geolocation coordinates (pickup/dropoff)  
  - `passenger_count`

---

## 3. Data Transformation Pipeline

### Initial Data Observations

Before cleaning:

<img width="1114" height="145" alt="image" src="https://github.com/user-attachments/assets/fe99fae5-d42e-427e-8d5b-54df76377b36" />


- Fare values in time format (e.g., `52:06.0`) indicating data corruption  
- Timezone inconsistencies  
- Extraneous fields (`key`) removed for clarity

### Cleaning Steps

- Removed non-numeric anomalies from `fare_amount` and converted to float  
- Standardized `pickup_datetime` with timezone (`+00:00`)  
- Filtered invalid geolocation values  
- Removed unrealistic trips (>50 km, zero/negative fares)  
- Dropped irrelevant columns (e.g., `key`)

### Feature Engineering

Derived features from cleaned `pickup_datetime`:

| Feature         | Description                             |
|----------------|-----------------------------------------|
| `hour`          | Hour of trip to identify peak times     |
| `day`           | Day of month                            |
| `month`         | Month of year                           |
| `day_of_week`   | Weekday label (e.g., Thursday)          |
| `Peak_Offpeak`  | Categorized peak vs. off-peak hours     |

After cleaning:

<img width="1469" height="145" alt="image" src="https://github.com/user-attachments/assets/a40ee024-c315-4db8-91a1-2b889c891783" />


---

## 4. Visualizations & Analysis

### Interactive Pickup Map

<img width="1283" height="721" alt="Screenshot 2025-07-27 191654" src="https://github.com/user-attachments/assets/f4971ae9-ef8b-4981-872b-8c2847cebdfe" />

This geospatial map visualizes ride pickup locations across NYC using latitude and longitude coordinates.

**Analytical Highlights:**
- **Time Filters:** Hour, weekday, month, and peak/off-peak toggles uncover hidden patterns in travel behavior.
- **Hotspot Clustering:** Dense areas around Midtown and Lower East Side reflect key demand regions.
- **Commuter & Leisure Insights:** Filtering “Friday, 17–20 Peak” reveals a traffic surge tied to evening transitions.

---

### Fare Buckets vs. Day of Week

<img width="1280" height="722" alt="Screenshot 2025-07-27 191943" src="https://github.com/user-attachments/assets/f8b16c5e-217f-4ef1-be3a-6f017a3fe6aa" />

A stacked bar chart sorting fare amounts into intuitive buckets across weekdays.

**Key Trends:**
- **High frequency of $0–$20 fares** on Friday and Saturday — short trips dominate.
- **Sparse upper fare brackets** suggest limited premium or long-haul usage.

| Observation                   | Interpretation                                  |
|-------------------------------|--------------------------------------------------|
| Low-fare dominance            | Indicates short, frequent urban rides           |
| Weekend concentration         | Reflects leisure and nightlife travel patterns  |
| Minimal high-fare rides       | Potential upsell opportunities                  |

---

### Passenger Count vs. Fare Amount

<img width="1281" height="723" alt="Screenshot 2025-07-27 191958" src="https://github.com/user-attachments/assets/28fb5652-629b-4ffa-912e-a2788dc41280" />


A scatter plot correlating passenger volume with fare values.

**Insights:**
- Most fares stay **below $50**, regardless of passenger count.
- **1–2 passengers** are most common; trips with **5–6** passengers are rare.
- **High-fare outliers** signal long-distance or surge-priced events.

---

### Fare Amounts Over Time

<img width="1280" height="721" alt="Screenshot 2025-07-27 192045" src="https://github.com/user-attachments/assets/006b6df9-05a8-4ca6-91b0-f18ede5d3f00" />

Three time-based visuals reveal how fare activity changes across the day, week, and year.

#### By Hour
- Peaks at **7–9 AM & 5–7 PM** reflect commuter demand.
- Early mornings (**1–4 AM**) show activity dips.

#### By Day
- Saturday surges — tied to social mobility.
- Slight Monday lull — less demand post-weekend.

#### Monthly Trends (2009–2015)
- Peaks during **June–August** suggest seasonality.
- Strong volume rise until **2013**, then plateau.

| Time Segment       | Analysis                                      |
|---------------------|-----------------------------------------------|
| Rush hour windows   | Highest activity for daily commuters          |
| Summer months       | Increased leisure and event-related rides     |
| 2013 plateau        | Possible market saturation or platform shift  |

---

### Yearly Fare Volume (2009–2015)

A historical line chart depicting annual fare counts over seven years.

**Trend Summary:**
- **2009–2011 decline** may reflect platform infancy or operational shifts.
- **2012–2013 rebound** followed by **steady volume** through 2015.

| Year Range     | Interpretation                                     |
|----------------|-----------------------------------------------------|
| Early dip      | Turbulent market entry or competitive influence     |
| Mid-phase rise | Platform recovery and scale expansion               |
| Later plateau  | Mature demand curve with steady engagement          |

---

Together, these dashboards offer a multi-dimensional analysis across geography, time, fare characteristics, and passenger behavior—demonstrating strong skills in exploratory visualization and domain interpretation.

Power BI dashboard components can be found at: https://drive.google.com/file/d/1APQAeNoTBlqARA0VZkZz76S18PEWCTjI/view?usp=sharing

---

## 8. Conclusion

Through detailed data transformation and feature creation, this project demonstrates how even corrupted datasets can yield actionable insights. The analytical pipeline supports urban mobility optimization and strategic pricing enhancements for ride-hailing services.

---

## Appendix

- Dataset raw sample file
- Dataset cleaned sample file  
- Data cleaning code (`da_uber.ipynb`)
- Power BI dashboard Reports\uber_dashbrd.pbix


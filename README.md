# Portfolio Setup Instructions

Welcome to CPLN5920/MUSA5080! This guide will help you set up your personal portfolio repository for the semester.

## What We're Building

- A portfolio repository on GitHub
- A live website showcasing our  work
- A place to document our learning journey  

```markdown
# CPLN 5920 / MUSA 5080 — Predictive Analytics for Planning
## Spring 2026 | University of Pennsylvania

This repository contains lab assignments and the final project for CPLN 5920/MUSA 5080 public policy analytics for urban planning at the University of Pennsylvania. The labs builds progressively from foundational data skills toward applied spatial and predictive modeling, culminating in a policy-relevant final challenge.

---

## Course Portfolio Structure

Each lab builds on the last, introducing new methods and tools that are applied in the final challenge.

| Lab | Title | Key Skills |
|-----|-------|------------|
| Lab 0 | dplyr Basics | Data wrangling, tidyverse fundamentals |
| Lab 1 | Census Data Quality for Policy Decisions | tidycensus, margin of error, ACS reliability |
| Lab 2 | Spatial Analysis and Visualization | sf, spatial joins, choropleth mapping |
| Lab 3 | Predicting Home Sales Price | Linear regression, feature engineering, train/test splits |
| Lab 4 | Spatial Predictive Modeling of Residential Burglary | Poisson regression, fishnet, Local Moran's I, kNN |
| Lab 5 | Bikeshare SpaceTime Prediction | Panel data, temporal features, cross-validation |
| **Final** | **Identifying Financially Vulnerable Homeowners** | **Logistic regression, class imbalance, equity analysis** |

---

## Final Challenge: Identifying Financially Vulnerable Homeowners: A Predictive Framework for Property Tax Delinquency in Philadelphia

### Overview

This report develops a predictive framework to identify Philadelphia properties at risk of becoming property tax delinquent before delinquency actually occurs, particularly during periods of economic hardship such as COVID-19. Property tax delinquency in Philadelphia increased from approximately $165 million to $178.5 million between 2024 and 2025, creating challenges for both municipal services and the School District of Philadelphia, which relies heavily on property tax revenue.

The goal of this project is not to create a tool for enforcement, but to provide the City with a way to identify financially vulnerable households earlier so that outreach and assistance can happen before penalties and debt begin to accumulate.

### Data

The project combined multiple sources of data including property tax delinquency records, OPA property characteristics, ACS census data at the block group and census tract levels, crime data, and neighborhood-level spatial features including Business Improvement Districts, Empowerment Zones, Housing Counseling Agencies, affordable housing developments, free meal sites, and parks.

### Methods

Several logistic regression models were tested throughout the analysis. One of the biggest challenges was the severe class imbalance in the dataset, since fewer than 1% of properties became delinquent. To better account for temporal patterns, the model incorporated yearly census data and used a validation framework where models were first trained on 2010–2018 data and validated on 2019 data before being retrained on 2010–2019 data and tested on 2020 outcomes.

After testing multiple approaches, **Model 8** produced the strongest results by combining sample rebalancing and inverse class weighting. The model achieved a sensitivity score of 84.2%, correctly identifying 3,430 properties that later became delinquent in 2020 while missing only 225.

### Key Findings

- Delinquency increased significantly between 2010 and 2020, remaining concentrated in areas facing greater economic hardship
- Properties located within Business Improvement Districts were generally less likely to become delinquent
- Properties located near affordable housing developments inside Empowerment Zones were more likely to experience delinquency
- The model performed most consistently in mid-to-high income neighborhoods where delinquency tends to be transient and event-driven
- The model performed less effectively in some of Philadelphia's lowest-income neighborhoods, reflecting deeper structural inequalities tied to property tax delinquency

### Policy Value

Even with these limitations, the model provides meaningful policy value. Rather than being used for punitive enforcement, the model is best suited for low-cost interventions such as mailed outreach about payment plans, hardship exemptions, and housing counseling programs. This project demonstrates how predictive modeling can help the City of Philadelphia take a more proactive and equitable approach to addressing property tax delinquency while still recognizing the need for broader long-term support in economically vulnerable communities.

---

## Authors of Final Challenge

**Jenny Brar · Maude Ceruso · Shubhanga Satyal · Vedika Jawa**
Master of Urban Spatial Analytics | Weitzman School of Design
University of Pennsylvania | Spring 2026

---

### Clone and Render

```bash
git clone https://github.com/JENB99/PPA-CPLN-5920-Spring26-Portfolio.git
cd PPA-CPLN-5920-Spring26-Portfolio
quarto render --to html
quarto preview
```

### Data

Data files are not tracked in this repository due to file size. The `data/` folder is listed in `.gitignore`. To reproduce the analysis, download the following sources:

- [OPA Real Estate Tax Delinquencies: OpenDataPhilly](https://data.phila.gov/visualizations/real-estate-tax-delinquencies)
- [OPA Property Characteristics: OpenDataPhilly](https://opendataphilly.org)
- ACS 5-Year Estimates 2010–2020 via `tidycensus`
- Philadelphia City Limits, Neighborhoods, BIDs, Empowerment Zones, HCAs: OpenDataPhilly
- Philadelphia Crime Incidents 2019: OpenDataPhilly

---

## Additional Sources

- [Quarto Documentation](https://quarto.org/docs/)
- [GitHub Docs](https://docs.github.com/)
- [tidycensus Documentation](https://walker-data.com/tidycensus/)
- [sf Package Documentation](https://r-spatial.github.io/sf/)
```

# Regression Analysis of Twitter Impressions  
**Authors**: Hunter Perkins, Marlon Durand, Jordan Deuley  

## Overview  
This project analyzes Twitter impressions for three accounts—Chris Udalla (137K followers), "Corn" (873K followers), and Elon Musk (136M followers)—to build regression models predicting tweet views based on engagement metrics (favorites, retweets, replies) and media type. The goal is to identify factors driving virality and inform marketing strategies.  

---

## Data Sources  
- **Twitter Data**: Scraped using [Apify](https://apify.com/quacker/twitter-scraper).  
- **Accounts Analyzed**:  
  - [Chris Udalla](https://twitter.com/Cudalla)  
  - [Elon Musk](https://twitter.com/elonmusk)  
  - [Corn](https://twitter.com/upblissed)  

---

## Methodology  
### Data Preparation  
- Removed retweets (identified by `NA` view counts).  
- Scaled numerical variables (e.g., divided by 1,000 to avoid scientific notation).  
- Addressed outliers using IQR filtering.  

### Exploratory Analysis  
- Generated histograms and pairs panels to visualize distributions and correlations.  
- Observed strong positive correlations between favorites, retweets, and views.  

### Modeling  
- Built linear regression models using `caret` and `lm`.  
- Evaluated performance with 10-fold cross-validation.  
- Compared models with/without outliers.  

---

## Key Results  
### Model Performance  
| Account     | R-squared (Original Data) | R-squared (IQR Filtered) |  
|-------------|---------------------------|--------------------------|  
| **Corn**    | 0.80                      | 0.74                     |  
| **Musk**    | 0.61                      | -                        |  
| **Udalla**  | 0.69                      | 0.71                     |  

### Insights  
- **Corn**: Favorites (`β = 56.92, p < 0.001`) and replies (`β = 3.43, p < 0.001`) most influenced views.  
- **Musk**: High variance in views (RMSE = 16.4M) due to extreme outliers (e.g., 50M+ views).  
- **Udalla**: Smaller dataset but stronger model fit after IQR filtering. 

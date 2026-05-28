# YouTube US Trending Analysis

Exploratory data analysis on what makes a YouTube video trend in the US.

## Dataset

`US_youtube_trending_data.csv` — daily snapshots of the US YouTube trending page from 2020 to 2024. Raw data has 268,787 rows since the same video appears once per trending day. After cleaning and deduplication: 47,124 unique videos.

Source: [Kaggle — YouTube Trending Video Dataset](https://www.kaggle.com/datasets/rsrishav/youtube-trending-video-dataset?select=US_youtube_trending_data.csv)

## Project Structure

```
Youtube_project/
  Data/
    US_youtube_trending_data.csv
    US_category_id.json
  Youtube_US_analysis.ipynb
  README.md
```

## Analysis Overview

**Section 1. Data Cleaning**
Deduplicated by video_id keeping peak view count, converted datetime columns, engineered engagement and timing features, and fixed three data quality issues.

**Section 2. What Categories Dominate Trending?**
Category distribution by video count and average views. Gaming leads in volume; Music leads in reach at 4.9M avg views per video.

**Section 3. What Drives Engagement?**
Engagement rate (likes / views) by category. Comedy ranks first at 7.1%. Scatter plot shows engagement flattens past a few million views.

**Section 4. How Long Do Videos Stay Trending?**
Distribution of trending duration. Median is 6 days. Boxplot by category shows Music and Entertainment have the widest spread.

**Section 5. Does Timing Matter?**
Upload hour and day of week analysis. Peak window is 3–5 PM UTC on Fridays and Tuesdays, but average views stay flat across time slots.

**Category Landscape**
Bubble chart plotting reach vs. engagement rate with trending duration as bubble size — all three dimensions in one view.

**Section 6. Key Takeaways**
5 findings distilled from the analysis.

## Key Findings

Gaming has the most trending videos but Music reaches further at 4.9M avg views. Comedy drives the highest engagement rate at 7.1%. The median video stays trending for 6 days. Upload timing shows a weak signal — it affects volume of trending appearances more than performance. High views and high engagement are separate things and the relationship flattens quickly past a few million views.

## Tools

Python 3, pandas, numpy, matplotlib, seaborn

## Contributors

Hyunseung Lee

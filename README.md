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

## Analysis

**Data Cleaning**
The raw dataset contains duplicate rows because the same video appears once for each day it stays on the trending page. I deduplicated by video_id keeping the row with the peak view count, then converted date columns from string to datetime, and addressed three data quality issues: 44 rows with negative days_to_trend caused by UTC offset differences, 18 rows with zero view counts, and 7,764 tags stored as the literal string `'[None]'` instead of null. After cleaning, the dataset contains 47,124 unique videos across 15 categories.

**Category Analysis**
Grouped videos by category to compare trending volume and average views. Gaming and Entertainment dominate in video count, but Music has the highest average view count at 4.9M per video — nearly 3x higher than Gaming. This shows that high volume on the trending page doesn't necessarily translate to high reach.

**Engagement Analysis**
Defined engagement rate as likes divided by views and compared it across categories. Comedy leads at 7.1%, followed by Music at 6.1%, while Sports and News & Politics rank at the bottom. A scatter plot of views vs. engagement rate shows that the relationship flattens quickly past a few million views — viral scale and audience interaction don't move together.

**Trending Duration Analysis**
Used the full raw dataset (before deduplication) to count how many unique days each video appeared on trending, then analyzed the distribution. The median is 6 days, with most videos falling between 4 and 8. A boxplot by category shows that while medians are similar across categories, Music and Entertainment have wider distributions — a small number of breakout videos in those categories stay trending for weeks.

**Timing Analysis**
Analyzed upload hour (UTC) and day of week to see if timing affects trending performance. Videos uploaded between 3–5 PM UTC appear most often in trending, and Fridays have the highest upload volume. However, average views stay flat across time slots, suggesting timing influences how many videos enter trending but has little effect on how well they perform once there.

**Category Landscape**
Built a bubble chart combining average views, average engagement rate, and median trending duration for each category in a single view. This makes it easier to see trade-offs between categories — for example, Music sits in a high-reach, high-engagement position while Sports has high volume but low engagement.

## Key Findings

Gaming has the most trending videos but Music reaches further at 4.9M avg views. Comedy drives the highest engagement rate at 7.1%. The median video stays trending for 6 days. Upload timing shows a weak signal — it affects volume of trending appearances more than performance. High views and high engagement are separate things and the relationship flattens quickly past a few million views.

## Tools

Python 3, pandas, numpy, matplotlib, seaborn

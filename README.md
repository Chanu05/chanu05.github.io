# Data Analysis Project 1: Top YouTubers 2024 
# Main Objective
* What are the client's requests?

The head of marketing is looking for the top YouTubers in order to run marketing campaigns throughout the rest of the year. Highest return on investment is the most important factor.
* How can I help?
By creating an interactive dashboard that showcases the top UK YouTubers, categorized by the following;
* Subscriber Count
* Total Views
* Total Videos uploaded
* Engagement metrics
This approach will provide the marketing team with useful insights before deciding which YouTuber(s) to collaborate with.

# Data source

Our data must include the following;
* Channel Names
* Total subscribers
* Total views
* Total videos uploaded
The data used for this project was sourced from Kaggle.

# Project Stages

1. Design
2. Development
3. Testing
4. Analysis

# Design

## Dashboard Requirements
To understand what components are needed in the dashboard, we must come up with a set of questions that need to be answered:
1. Who are the top 10 YouTubers with the most subscribers?
2. Which 3 channels have uploaded the most videos?
3. Which 3 channels have the most views?
4. Which 3 channels have the highest average views per video?
5. Which 3 channels have the highest views per subscriber ratio?
6. Which 3 channels have the highest subcriber engagement rate per video?
If our dashboard is able to answer these questions, then it is safe to assume that the dashboard has effectively carried out it's purpose.

## Dashboard mockup
* What should the dashboard look like?
Visuals to be included are;
1. Table with all relevant data
2. Treemap of Top YouTubers
3. Scorecards for engagement statistics
4. Horizontal bar chart to allow for quick and easy comparison

## Tools used
| Tool | Purpose |
| --- | --- |
| Excel | To explore the data |
| SQL Server | To clean, test and analyze the data |
| Power BI | To create the interactive dashboard |
| GitHub | To host and document the project |

# Development

## The plan

* What is the approach I am taking, from start to finish?

1. Obtain the data from Kaggle
2. Explore the data in Excel
3. Load the data into SQL server
4. Clean the data with SQL
5. Analyze and perform quality checks of the data in SQL
6. Visualize the data in Power BI
7. Generate the findings based on the insights
8. Document the project
9. Publish the data to GitHub

## Data exploration 

During this stage, the data is scanned for errors, inconsistencies, weird characters, etc.
Some issues found were:

1. Channel ID and an '@' sign was found before the channel name in the same column - so we need to extract just the channel name from this.
2. Some cells were in a different language - had to confirm if these bits of data was needed.
3. Had more data than needed, so some were to be removed.

## Data cleaning

What do we mean by 'clean data'?
* Only relevant columns needed
* All data types should be appropriate
* No columns should contain missing values (or null values)#

Our cleaned data resulted in a total of 4 columns, each with 100 rows.

| Column Name | Data Type | Nullable |
| --- | --- | --- | 
| channel_name | VARCHAR | NO |
| total_subscribers | INTEGER | NO |
| total_views | INTEGER | NO | 
| total_videos | INTEGER | NO |

## Transforming the data in SQL Server

```sql
/*

# Data cleaning steps:

1. Remove unnecessary columns by only selecting the ones we need.
2. Extract the Youtube channel names from the first columns.
3. Rename the column names.

*/

CREATE VIEW view_uk_youtubers_2024 AS

SELECT
	CAST(SUBSTRING(NOMBRE, 1, CHARINDEX('@', NOMBRE)-1) AS VARCHAR(100)) as channel_name,
	total_subscribers,
	total_views,
	total_videos
	

FROM top_uk_youtubers_2024

```

# Testing

Here are the data quality checks conducted: 

## 1. Row count check 

```sql

-- 1. Row count check:

SELECT
  COUNT(*) AS no_of_rows
FROM
  view_uk_youtubers_2024;

```









# Data Science Project By Muhammad Faiz Noh
This page is my portfolio for data science projects. 
The purpose of this portfolio is to present my skill in Data Science, Python and SQL. 

I have technical background in PHP programming and I am looking forward to change my carrer to data driven roles. 
This is to prepare myself for Industry Revolution 4.

If I am the right candidate to fill the position, please contact me for futher discussion. 


- Email: muhammadfaiznoh@gmail.com
- LinkedIn: [LinkedIn](https://www.linkedin.com/in/muhammadfaiznoh)
- Website: [Portfolio](https://muhammadfaiznoh.github.io/DataScience/)


## 1) Medical Cost Analysis

This is my Exploratory Data Analysis on medical cost dataset. 
Analyze by using Data Science OSEMN framework.

- `O`btain data: from Kaggle.
- `S`crub data / clean data: modify value from string to binary
- `E`xplore data: with Pandas DataFrame, Seaborn and Matplotlib visualization.
- `M`odelling: Supervised Learning Algorithms: Linear Regression & Unsupervised Learning Algorithms: K-Means Clustering
- i`N`terpret: summary of findings with visualization.

![image](https://github.com/muhammadfaiznoh/DataScience/blob/gh-pages/scatterplot.PNG?raw=true)

1. Project link: [Medical Cost Analysis](https://github.com/muhammadfaiznoh/medical-cost-analysis).
2. Dashboard link: [Medical Cost Visualization](https://datastudio.google.com/reporting/608ec992-d706-4945-9895-2eefae7b79c4).

## 2) Chicago Crime Visualization

This is my Exploratory Data Analysis on medical cost dataset.

1. Obtain data: from [Chicago crime data](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2/data).
2. What happened inside the Colab file?

- Retrieve Chicago Crime Data from 2018 - 2020 compress zipped file from Google Drive.
- Download and unzip the file then read with Pandas.
- Rename the column name of the DataFrame.
- Convert string DateTime from CSV into DateTime data type.
- Load the content of DataFrame into BigQuery

SQL script used to get month from date and remove the bracket from location
```
SELECT 
  primary_type
  ,year
  ,EXTRACT(MONTH FROM crime_date) AS crime_month
  ,REPLACE(REPLACE(location, ")",""), "(","") AS location
  ,arrest
FROM `chicagocrime-309113.DS360Dataset.ChicagoCrimeData`
WHERE location IS NOT NULL

```
SQL script used to get hour from date
```
SELECT 
  primary_type,
  EXTRACT (HOUR  FROM crime_date) as crime_hour
  ,year
FROM `chicagocrime-309113.DS360Dataset.ChicagoCrimeData`
```
SQL script used to calculate the moving average 100 days
```
SELECT
CASE
    WHEN ROW_NUMBER() OVER(ORDER BY day) > 100 THEN DATE_FROM_UNIX_DATE(day) end AS crime_date,
  -- DATE_FROM_UNIX_DATE(day) AS crime_date,
  CASE
    WHEN ROW_NUMBER() OVER(ORDER BY day) > 100 THEN AVG(crime_amount) OVER (ORDER BY day RANGE BETWEEN 100 PRECEDING AND CURRENT ROW)
  ELSE
  NULL
END
  mov_avg_7d
FROM (
  SELECT
    UNIX_DATE(DATE(crime_date)) AS day,
    COUNT(case_number) AS crime_amount
  FROM
    `chicagocrime-309113.DS360Dataset.ChicagoCrimeData`
  GROUP BY
    day )
```
<!-- Dashboard link: [Chicago Crime Visualization](https://datastudio.google.com/reporting/9298e282-0462-469e-b744-40a44b26db42).
```markdown
Syntax highlighted code block

# Header 1
## Header 2
### Header 3

- Bulleted
- List

1. Numbered
2. List

**Bold** and _Italic_ and `Code` text

[Link](url) and ![Image](src)
```



### Jekyll Themes

Your Pages site will use the layout and styles from the Jekyll theme you have selected in your [repository settings](https://github.com/muhammadfaiznoh/muhammadfaiznoh.github.io-DataScience/settings/pages). The name of this theme is saved in the Jekyll `_config.yml` configuration file.

### Support or Contact

Having trouble with Pages? Check out our [documentation](https://docs.github.com/categories/github-pages-basics/) or [contact support](https://support.github.com/contact) and we’ll help you sort it out. -->

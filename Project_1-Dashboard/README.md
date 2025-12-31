# Excel Salary Dashboard

![1_Dashboard.png](/Images\1_Dashboard.png)

## Introduction

This data jobs information dashboard is designed to help job seekers explore salary ranges for their desired roles and evaluate whether the compensation aligns with industry standards.

The data is from [Public Job Posting Datasets](https://datanerd.tech) developed by Luke Barousse. The data contains detailed information on job titles, salaries, posted date, job platform, locations, and essential skills that are presented here.

### Excel Skills Used

- **Formulas and Functions**
- **Charts**
- **Data Validation**

## Dashboard Build

### Charts

#### Top Paying Job Salary - Bar Chart

![Data_bars_1.png](/Images/Data_bars_1.png)

- **Excel Features:** Implemented bar charts (with formatted salary values) and optimized the layout to enhance clarity and readability.
- **Design Choice:** Visual comparison of median salaries for each jobs in horizontal bar chart.
- **Data Organization:** Sorted job titles by descending salary for improved readability.
- **Insights Gained:** This enables quick identification of salary trends, highlighting that senior level data jobs have higher salaries than entry/junior level data jobs. This chart also shows that Data Analyst is the lowest in both entry and senior level jobs while Data Scientist is the highest for both levels.

#### 🗺️ Country Median Salaries - Map Chart

![map_chart.png](/Images\map_chart.png)

- **Excel Features:** Utilized Excel's map chart feature to plot median salaries globally.
- **Design Choice:** A color-coded map visually differentiates salary levels across regions.
- **Data Representation:** Plotted median salary for each country with available data.
- **Visual Enhancement:** Improved readability and immediate understanding of geographic salary trends.
- **Insights Gained:** This helps quickly identify global salary differences and high- or low-paying regions.

### Formulas and Functions

#### Median Salary by Job Titles

```
=MEDIAN(
IF(
    (jobs[job_title_short]=A2)*
    (jobs[job_country]=country)*
    (ISNUMBER(SEARCH(type,jobs[job_schedule_type])))*
    (jobs[salary_year_avg]<>0),
    jobs[salary_year_avg]
)
)
```

- **Multi-Criteria Filtering:** Checks job title, country, schedule type, and excludes blank salaries.
- **Array Formula:** Utilizes `MEDIAN()` function with nested `IF()` statement to analyze an array.
- **Tailored Insights:** Provides specific salary information for job titles, regions, and schedule types.
- **Formula Purpose:** Returning the median salary based on job title, country, and schedule type specified from slicers.

Background Table

![background_table_salary.png](/Images\background_table_salary.png)

Dashboard Implementation

![Data_bars_1.png](/Images\Data_bars_1.png)

#### Count of Job Schedule Type

```
=FILTER(J2#,(NOT(ISNUMBER(SEARCH("and",J2#))+ISNUMBER(SEARCH(",",J2#))))*(J2#<>0))
```

- **Unique List Generation:** This Excel formula below employs the `FILTER()` function to exclude entries containing "and" or commas, and omit zero values.
- **Formula Purpose:** Gives us a list of unique job schedule types.

Background Table

![background_table_schedule_type.png](/Images\background_table_schedule_type.png)

Dashboard Implementation:

![data_bars_2.png](/Images\data_bars_2.png)

### Data Validation

#### Filtered List

- **Enhanced Data Validation:** Implementing the filtered list as a data validation rule under the `Job Title`, `Country`, and `Type` option in the Data tab ensures:
    - User input is limited to predefined and validated schedule types.
    - Incorrect or inconsistent entries are prevented
    - Overall usability of the dashboard is enhanced

![slicers.png](/Images\slicers.png)

![job_filtering.png](/Images\job_filtering.png)

![country_filtering.png](/Images\country_filtering.png)

![job_schedule_filtering.png](/Images\job_schedule_filtering.png)


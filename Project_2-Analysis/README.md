## Introduction

### Questions to Analyze

To gain insights into the data science job market, the following questions were addressed:

1. **Do more skills get you better pay?**
2. **What’s the salary for data jobs in different regions?**
3. **What are the top skills of data professionals?**
4. **What’s the pay for the top 10 skills?**

### Excel Skills Used

The following Excel skills were utilized for analysis:

- **Pivot Tables**
- **Pivot Charts**
- **DAX (Data Analysis Expressions)**
- **Power Query**
- **Power Pivot**

### Data Jobs Dataset

The dataset used for this project contains real-world data science job information from 2023. The dataset is available via [Public Job Posting Datasets](https://datanerd.tech), which provides a foundation for analyzing data using Excel. 

It includes detailed information on:

- **Job titles**
- **Salaries**
- **Locations**
- **Skills**

## 1. Do more skills get you better pay?

### Skill: Power Query (ETL)

a. Extract: first used Power Query to extract the original data (`data_salary_all.xlsx`) and create two queries: data jobs information and skills for each job listing data

b. Transform: Each query was transformed by adjusting column data types, removing unnecessary fields, cleaning text to remove specific terms, and trimming excess whitespace.

c. Load: loaded both transformed queries into the workbook, setting the foundation for my subsequent analysis.
- data_jobs_all

![power_query_q1_salary.png](/Images/power_query_q1_salary.png)

- data_job_skills

![power_query_q1_skills.png](/Images/power_query_q1_skills.png)

### Analysis

#### Insights

- Job postings that require more skills tend to offer higher median salaries, particularly for Senior Data Engineer and Data Scientist roles.
- Roles that require fewer skills, such as Business Analyst and Data Analyst, generally offer lower salaries, indicating that more specialized skill sets have higher market value.

    ![q1_plot.png](/Images/q1_plot.png)


- This trend highlights the importance of acquiring multiple relevant skills, especially for those pursuing higher-paying roles.

## 2. What’s the salary for data jobs in different regions?

### Skills: PivotTables & DAX

#### Pivot Table

- Created a PivotTable using the Data Model that created with Power Pivot.
- Insert the `job_title_short` to the rows area and `salary_year_avg` into the values area.
- Added new measure to calculate the median salary for jobs in United Satates and all countries except United States.
    ```
    =CALCULATE(
        [Median Salary],
        data_jobs_all[job_country] = "United States")
    ```

    ```
    =CALCULATE(
        [Median Salary],
        data_jobs_all[job_country] <> "United States")
    ```

#### DAX

- DAX is used to calculate median yearly salary.

    ```
    Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
    ```

### Analysis

#### Insights

- Salary differences between US and non-US roles are most evident in high-tech positions, reflecting the strong concentration of tech industries in the US.
- Roles such as Senior Data Engineer and Data Scientist earn higher median salaries both in the US and globally, reflecting strong worldwide demand for advanced data expertise.

    ![q2_pivottable.png](/Images/q2_pivottable.png)

- These insights support career planning and salary negotiations by aligning compensation expectations with market standards across regions.

## 3. What are the top skills of data professionals?

### Skill: Power Pivot

#### Power Pivot

- Created a data model by integrating the `data_jobs_all` and `data_jobs_skills` tables into one model.
- Power Pivot created a relationship between these two tables via `job_id` column.

    ![q3_power_pivot_diagram.png](/Images/q3_power_pivot_diagram.png)

#### Power Pivot Menu

- The Power Pivot menu was utilized to refine the data model and simplify the creation of measures.

    ![q3_power_pivot_table.png](/Images/q3_power_pivot_table.png)

### Analysis

#### Insights

- SQL, Excel, and Python dominate as top skills in data analyst jobs, reflecting their foundational role in data processing and analysis.
- Visualization tools like Tableu and Power BI also needed by Data Analyst jobs to support decision-making and for easy readibility.

    ![q3_plot.png](/Images/q3_plot.png)

- Understanding the most in-demand skills in the industry helps professionals remain competitive while also guiding training and educational programs to focus on the most impactful technologies.

## 4. What’s the pay of the top 10 skills?

### Skill: Advanced Charts (Pivot Chart)

#### PivotChart

- Created a combo PivotChart to plot median salary (as column) and skill likelihood (as a line with markers) from PivotTable.
- Removed the lines (skill likelihood), and changed the markers to rounds.

### Analysis

#### Insights

- Skills like Python, Oracle, and SQL, offering higher salaries because of their value and difficulty in data analyst roles.
- Skiils like SQL, Excel, and Python having higher demand, indicating their critical roles in data analyst.
- PowerPoint and Word rank among the lowest-paying skills, reflecting their lower specialization and demand in higher-salary roles.

    ![q4_plot.png](/Images/q4_plot.png)


- The chart underscores the importance of developing high-value skills like SQL and Python to access higher-paying roles in the data analyst jobs.

## Conclusion

This Excel-based project analyzes real-world data science job postings to uncover insights into roles, salaries, locations, and required skills. Using Power Query, PivotTables, DAX, and visualizations, it highlights the strong link between multiple in-demand skills, especially Python and SQL, and higher salaries.

This project aims to serve as a practical guide for data professionals and provide an overview of the skills required for higher-paying roles.

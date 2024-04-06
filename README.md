# JobSchedule_Monthly_Trend_Analysis

Job Schedule Monthly Trend Analysis
This repository contains a SQL query for analyzing the monthly trend in job schedules based on data from the job_schedule table. It calculates the count of jobs scheduled each month for the years 2022 and 2023 and calculates the difference between the counts for 2023 and 2022.

Overview
The provided SQL query retrieves data from the job_schedule table and aggregates it to calculate the count of jobs scheduled each month for the years 2022 and 2023. It also calculates the difference in counts between 2023 and 2022 to identify any trends or changes over time.

SQL Query
_**SELECT
    CASE 
        WHEN MONTH(start_date) = 1 THEN 'Jan'
        WHEN MONTH(start_date) = 2 THEN 'Feb'
        WHEN MONTH(start_date) = 3 THEN 'Mar'
        WHEN MONTH(start_date) = 4 THEN 'Apr'
        WHEN MONTH(start_date) = 5 THEN 'May'
        WHEN MONTH(start_date) = 6 THEN 'Jun'
        WHEN MONTH(start_date) = 7 THEN 'Jul'
        WHEN MONTH(start_date) = 8 THEN 'Aug'
        WHEN MONTH(start_date) = 9 THEN 'Sep'
        WHEN MONTH(start_date) = 10 THEN 'Oct'
        WHEN MONTH(start_date) = 11 THEN 'Nov'
        WHEN MONTH(start_date) = 12 THEN 'Dec'
    END AS Month,
     SUM(CASE WHEN YEAR(start_date) = 2022 THEN 1 ELSE 0 END) AS Count_2022,
    SUM(CASE WHEN YEAR(start_date) = 2023 THEN 1 ELSE 0 END) AS Count_2023,
    ( SUM(CASE WHEN YEAR(start_date) = 2023 THEN 1 ELSE 0 END)-SUM(CASE WHEN YEAR(start_date) = 2022 THEN 1 ELSE 0 END))as Diff_2023_sub_2022
FROM job_schedule
WHERE YEAR(start_date) IN (2022, 2023)
AND webschedulerstatus IN (12, 18)
GROUP BY MONTH(start_date)
ORDER BY MONTH(start_date);**_


Description
This SQL query provides insights into the monthly trends of job scheduling activity for the years 2022 and 2023. It categorizes the counts of scheduled jobs by month and calculates the difference between the counts for 2023 and 2022. This analysis can help identify any significant changes or patterns in job scheduling over time.

How to Use
Clone this repository to your local machine.
Execute the provided SQL query in your SQL Server environment, ensuring that you have access to the job_schedule table.
Review the output to understand the monthly trend in job scheduling activity and the difference between 2023 and 2022.
Utilize the insights gained from the analysis to inform decision-making processes related to job scheduling and resource allocation.

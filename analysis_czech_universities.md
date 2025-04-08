Project Documentation: Analysis of Czech University Data
1. Project Description
This project aims to perform an analysis of student data from Czech universities based on the provided dataset. The collected data was analyzed using SQL queries in PostgreSQL, and the results were saved as CSV files for further use in other tools (e.g., Power BI).

2. Tools Used:
PostgreSQL: for storing and manipulating data.

SQL: for writing queries to analyze the data.

Power BI (for visualization, if needed): for creating visualizations based on the data (not used yet, but can be added).

CSV: for saving the analysis results in a text format, with the ability to use them in various tools.

3. Database Structure
The project used one main table:

Table: university_stats

Columns:

college_en — University name (in English).

college_cs — University name (in Czech).

faculty_en — Faculty name (in English).

faculty_cs — Faculty name (in Czech).

study_program_en — Study program name (in English).

study_program_cs — Study program name (in Czech).

year_of_enrollment — Year of enrollment.

year — The year in which the data was collected.

active — Student status (active).

interrupted — Student status (interrupted).

completed — Student status (completed studies).

terminated_without_graduation — Student status (terminated without graduation).

for_study_reasons — Reasons for terminating studies (academic).

termination_of_accreditation — Reasons for terminating studies (termination of accreditation).

for_disciplinary_reasons — Reasons for terminating studies (disciplinary).

death — Reasons for terminating studies (death).

otherwise — Other reasons for terminating studies.

4. SQL Queries for Analysis
Distribution of Students by Faculty: This query analyzes the number of students by faculty, sorting by the number of students in descending order.


SELECT faculty_en, COUNT(*) AS student_count 
FROM university_stats 
GROUP BY faculty_en 
ORDER BY student_count DESC;
Student Status by Year: This query shows how many students have each status (active, completed studies, interrupted) based on the year.


SELECT year, active, COUNT(*) AS student_count
FROM university_stats
GROUP BY year, active
ORDER BY year, active;
Completion of Studies by Year: This query calculates how many students completed their studies each year.


SELECT year, completed, COUNT(*) AS student_count
FROM university_stats
GROUP BY year, completed
ORDER BY year;
5. Exporting Results
To save the results of the analysis into CSV files, the COPY command was used to export the queries into a text format. Here are examples for each query:

Export Distribution of Students by Faculty:


COPY (
  SELECT faculty_en, COUNT(*) AS student_count 
  FROM university_stats 
  GROUP BY faculty_en 
  ORDER BY student_count DESC



COPY (
  SELECT year, active, COUNT(*) AS student_count
  FROM university_stats
  GROUP BY year, active
  ORDER BY year, active


COPY (
  SELECT year, completed, COUNT(*) AS student_count
  FROM university_stats
  GROUP BY year, completed
  ORDER BY year)
  
6. Next Steps
Visualization in Power BI (if needed): You can import the saved CSV files into Power BI and create various charts to visualize the data, as previously discussed.

Query Optimization: Depending on the results and requirements, you may need to optimize the queries for faster data retrieval or extend the analysis.

Project Expansion: Further analysis can include additional filters, for example, to determine popular study programs or compare faculties based on other attributes.

7. Conclusions
The collected data provided valuable insights into the number of students, study statuses, and faculty popularity at Czech universities.

Using SQL queries and exporting results to CSV allows efficient handling of large datasets and preparation for further visualization or reporting.
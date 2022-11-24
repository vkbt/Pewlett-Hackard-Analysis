# Pewlett-Hackard Analysis - Silver Tsunami

## Overview

Bobby, an HR analyst from Pewlett Hackard, a large company boasting several thousand employees that's been around for a long time, asked us to perform an employee research on upcoming retirements of baby boomers as many current employees reach retirement age.  The result of our research will let Pewlett Hackard know how many employees will be retiring in the next few years and what are their titles in the company.

## Resources
- Data Source: [departments.csv](https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Data/departments.csv),
[employees.csv](https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Data/employees.csv),
[dept_emp.csv](https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Data/dept_emp.csv),
[dept_manager.csv](https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Data/dept_manager.csv),
[salaries.csv](https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Data/salaries.csv),
[titles.csv](https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Data/titles.csv)

- Software: PostgreSQL **15.1**, pgAdmin **6.15**

## Results

We received six csv files containing employee data from Bobby. It was important that considering the amount of data first we helped Bobby build an employee database and then started our analysis. 

We downloaded and installed [**PostgreSQL**](https://www.postgresql.org) - an open source object-relational database system and [**pgAdmin**](https://www.pgadmin.org/) - an open source graphical management tool that serves as a development platform for PosgreSQL to help Bobby create an employee database. We used [**Structured Query Language (SQL)**](https://en.wikipedia.org/wiki/SQL), a standard language for storing, manipulating and retrieving data in databases, to write and execute queries in pgAdmin.

After reviewing csv data files we received from Bobby, we created an [**ERD**](https://app.quickdatabasediagrams.com/#/) (entity relationship diagram) flowchart that highlights different tables and their relationships. ERD flowchart is an important and useful tool that provides visual representation of the tables and gives a deeper understanding of the data and the database as a whole.

We created a new Pewlett Hackard employee database with 6 tables in postgreSQL using [**CREATE TABLE**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-create-table/) statements and imported 6 csv data files and started our analysis:

- we started by building a query that holds all the titles of employees who were born between January 1, 1952 and December 31, 1955 using [**INNER JOIN**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-inner-join/) and [**WHERE**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-where/) clauses. We saved this query using [**SELECT INTO**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-select-into/) statement as **retirement_titles** table and exported it into [**retirement_titles.csv**](https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Data/retirement_titles.csv) file.

<img src="https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Resources/del_1.png" width=100% height=100%>

- we can see from the image above, some employees were duplicated as they held different titles throughout their employment with Pewlett Hackard. We used [**DISTINCT ON**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-select-distinct/) clause to clean the table of duplicates and saved it as **unique_titles** table using [**SELECT INTO**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-select-into/) and exported it into [**unique_titles.csv**](https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Data/unique_titles.csv) file.

<img src="https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Resources/del_1.2.png" width=100% height=100%>

- to retrieve the number of employees by their most recent job title who are about to retire we used [**COUNT**](https://www.postgresqltutorial.com/postgresql-aggregate-functions/postgresql-count-function/) function, [**GROUP BY**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-group-by/) and [**ORDER BY**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-order-by/) clauses and saved it as **retiring_titles** table using [**SELECT INTO**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-select-into/) statement and exported it into [**retiring_titles.csv**](https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Data/retiring_titles.csv) file.

<img src="https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Resources/del_1.3.png" width=100% height=100%>

- we created a mentorship eligibility table for current employees who were born between January 1, 1965 and December 31, 1965 using [**WHERE**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-where/), [**INNER JOIN**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-inner-join/) and [**ORDER BY**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-order-by/) clauses, saved it as **mentorship_eligibilty** table using [**SELECT INTO**](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-select-into/) statement and exported it into [**mentorship_eligibilty.csv**](https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Data/mentorship_eligibilty.csv) file.

<img src="https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Resources/del_2.png" width=100% height=100%>

## Summary

According to our reasearch 72,548 employees are retiring within the next several years. For a company that at the moment employs 240,124 it is a third of a workforce. 


<img src="https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Resources/summary_total_working_employees.png" width=100% height=100%>

During our data analysis we identified that only 1,549 employees are eligible for mentorship program. We think that this number is very low taking into account that more than 70,000 employees were eligible to retire the nearest future. We suggest to apply several changes to the query. For example, the number of employees eligible for mentorship soared to 14,002 after we expanded our eligibility criteria by one year(added employees born in 1964 to the query) and filtered it by employees holding senior positions only.

<img src="https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Resources/summary_eligible_mentors_64_65.png" width=100% height=100%>

We also would like to point out that women tend to retire earlier than men. To analyze this further we ran a separate query on retirement eligible employees, added a gender and grouped by it.

<img src="https://github.com/vkbt/Pewlett-Hackard-Analysis/blob/main/Resources/summary_retirement_eligible_employees_by_gender.png" width=100% height=100%>

We would also suggest that Pewlett Hackard conducts a survey for current retirement eligible employees to see if they are planning to retire or they are planning to keep on working and how long.

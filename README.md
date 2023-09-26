# PWC Power BI Virtual work experience - Diversity and Inclusion Analysis
![PwC Power BI Virtual Case Experience (1)](https://user-images.githubusercontent.com/118357991/229363730-638a282b-7348-4b3d-a0ff-3f8c0c9e3b9e.png)

## Table of Contents:

- [Problem Statement](https://github.com/DarvinciVincent/Diversity_and_Inclusion_Dashboard/blob/main/README.md#problem-statement-)
- [Datasource](https://github.com/DarvinciVincent/Diversity_and_Inclusion_Dashboard/blob/main/README.md#datasource-)
- [Data Preparation](https://github.com/DarvinciVincent/Diversity_and_Inclusion_Dashboard/blob/main/README.md#data-preparation)
- [Data Modeling](https://github.com/DarvinciVincent/Diversity_and_Inclusion_Dashboard/blob/main/README.md#data-modeling)
- [Data Analysis (DAX)](https://github.com/DarvinciVincent/Diversity_and_Inclusion_Dashboard/blob/main/README.md#data-analysis-dax)
- [Insights](https://github.com/DarvinciVincent/Diversity_and_Inclusion_Dashboard/blob/main/README.md#insights)

## Problem Statement :

The purpose of this task is to:

- Define proper KPIs in hiring, promotion, performance and turnover
- Create a visualisation for the HR manager that reflects all relevant Key Performance indicators(KPIs) and metrics in the dataset.

Calculating the following measures could help to define proper KPIs:

- Number of men
- Number of women
- Number of leavers
- % employees promoted (FY21)
- % of women promoted
- % of hires men
- % of hires women
- % turnover 
- Average performance rating: men
- Average Performance rating: women

## Datasource :

Dataset used for this task was presented by [Pwc](https://www.pwc.ch/en/careers-with-pwc/students/virtual-case-experience.html) and Diversity and Inclusion dataset:

Dataset: [Diversity and Inclusion](https://github.com/DarvinciVincent/Diversity_and_Inclusion_Dashboard/blob/main/03%20Diversity-Inclusion-Dataset.xlsx)

## Data Preparation:

Completed the Data transformation in Power Query and the dataset loaded into Microsoft Power BI Desktop for modeling.

Diversity and Inclusion dataset is give table named:

- `Diversity and Inclusion dataset` which has `500 rows and 31 Column` of observation

Data Cleaning for the dataset was done in the power query editor as follows:
- Changed the header row of dataset
- Removed Unnecessary columns 
- Removed Unnecessary rows
- Each of the columns in the table were validated to have the correct data type

## Data Modeling:
And then dataset was cleaned and transformed, it was ready to the data modeled.

- The `diversity and inclusion` tables as show below:

![Screenshot (53)](https://user-images.githubusercontent.com/118357991/229366105-ee670e8e-2c01-4370-b28d-3a74d5033a00.png)

## Data Analysis (DAX):

Measures used in  all visualization are:

- #of leavers = 'CALCULATE(COUNT('HR manager'[FY20 leaver?]), 'HR manager'[FY20 leaver?] = "Yes")'

- #of men = 'CALCULATE(COUNT('HR manager'[Gender]), 'HR manager'[Gender] = "Male")'

- #of women = 'CALCULATE(COUNT('HR manager'[Gender]), 'HR manager'[Gender] = "Female")'

- % employees promoted (FY21) = <br>
'Divide(<br>
    Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[Promotion in FY21?]="Yes")),<br>
    Calculate(distinctcount('HR Manager'[Employee ID]),Filter('HR Manager','HR Manager'[In base group for Promotion FY21]="Yes")),<br>
    0)'

- % of Hires Men = 'DIVIDE('HR manager'[# of men],('HR manager'[# of men]+'HR manager'[# of women]))'

- % of Hires Women = 'DIVIDE('HR manager'[# of women],('HR manager'[# of men]+'HR manager'[# of women]))'

- % of man promoted = <br>
'DIVIDE(<br>
    CALCULATE(DISTINCTCOUNT('HR Manager'[Employee ID]),FILTER('HR Manager','HR Manager'[Gender]="Male")),<br>
    DISTINCTCOUNT('HR Manager'[Employee ID]))'

- % of women promoted = <br>
'DIVIDE(<br>
    CALCULATE(DISTINCTCOUNT('HR Manager'[Employee ID]),FILTER('HR Manager','HR Manager'[Gender]="Female")),<br>
    DISTINCTCOUNT('HR Manager'[Employee ID]))'

- % Turnover = 'DIVIDE(CALCULATE(DISTINCTCOUNT('HR Manager'[Employee ID]),FILTER('HR Manager','HR Manager'[FY20 leaver?]="Yes")),DIVIDE(CALCULATE(DISTINCTCOUNT('HR Manager'[Employee ID]),FILTER('HR Manager','HR Manager'[In base group for turnover FY20]="Yes"))+CALCULATE(DISTINCTCOUNT('HR Manager'[Employee ID]),FILTER('HR Manager',NOT ('HR Manager'[Department @01.07.2020]=BLANK()))),2))'

- Avg Rating Men = 'CALCULATE(AVERAGE('HR manager'[FY20 Performance Rating]), 'HR manager'[Gender] = "Male")'

- Avg Rating Women = 'CALCULATE(AVERAGE('HR manager'[FY20 Performance Rating]), 'HR manager'[Gender] = "Female")'


## Insights:

As shown the data Visualization, It can be deduced that:

- 41 % Female hires of the year and 59 % Male hires of the years.
- 53.8% of promoted were Female in the Junior Officer category, the highest for the year.
- 47% of promoted were Male in the Junior Officer category, the lowest for the year.
- Director is the highest Average time of job level promoted in this year.
- Finance department 22% highest turnover of the year.
- Average Rating Female 2.42%
- Average Rating Male 2.41%
- Employees promoted year of 2021 is  54.34% Male and 45.66% Female.
- The most common age group is 20-29 having 223 employees fall in this category.

---

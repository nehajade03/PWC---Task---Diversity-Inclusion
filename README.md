# **PWC- Task 3 - Diversity-Inclusion**

## **Table Content**

- [Problem Statement](#problem-statement)
- [DataSource](#datasource)
- [Data Preparation](#data-preparation)
- [Data Analysis](#data-analysis)
- [Data Analysis (DAX)](#data-analysis-dax)
- [Data Visualization (Dashboard)](#data-visualization-dashboard)
- [Insights](#insights)
  








## **Problem Statement**
Despite efforts to improve gender balance at the executive management level, our telecom client’s HR team is not seeing progress. To identify gaps and define actionable strategies, key workforce metrics must be analyzed, including:

- Count of men
- Count  of women
- Count of leavers
-  % employees promoted (FY21)
- % of women promoted
- % of hires men
- % of hires women
- % turnover 
- Average performance rating: men
- Average Performance rating: women

## **Datasource**

The dataset is provided by the [PwC](https://www.theforage.com/virtual-experience/a87GpgE6tiku7q3gu/pw-c-switzerland/power-bi-cqxg/diversity-inclusion) Virtual Job Simulation on Forage, focusing on HR diversity and inclusion metrics.
- Gender, Job Levels, Promotions, Leavers
- Performance Ratings, New Hires, Turnover Rate

## **Data Preparation**

- Removed unnecessary columns to streamline the dataset.
- Changed data types for consistency (e.g., dates, percentages, integers).
- Created new measures:
     - Turnover Rate (%)
     - Promotion Rate (%)
     - Gender-Specific KPIs (e.g., % Women Promoted, % Hires by Gender).
**Data Analysis 
  And then dataset was cleaned and transformed, it was ready to the data modeled.

## **Data Analysis**

The dataset includes several new measures for in-depth analysis:

1. **Descriptive Statistics**
   - Gender distribution and leaver analysis.
2. **Promotion Rates**
   - Overall and gender-specific promotion rates.
3. **Hiring Trends**
   - Analysis of hiring by gender and time.
4. **Turnover Analysis**
   - Overall and gender-specific turnover rates.
5. **Performance Ratings**
   - Average performance ratings by gender.
6. **Actionable Recommendations**
   - Propose targeted interventions based on insights.

## **Data Analysis (DAX)**
- **% employees promoted(FY21)** = Divide(Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG','Pharma Group AG'[Promotion in FY21?]="Yes")),Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG','Pharma Group AG'[In base group for Promotion FY21]="Yes")))

- **% Turnover** = Divide(Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG','Pharma Group AG'[FY20 leaver?]="Yes")),Divide(Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG','Pharma Group AG'[In base group for turnover FY20]="Y"))+Calculate(distinctcount('Pharma Group AG'[Employee ID]),Filter('Pharma Group AG',NOT('Pharma Group AG'[Department @01.07.2020]=BLANK()))),2))

- **Average Performance Rating (Men)** = 
AVERAGEX(FILTER('Pharma Group AG', 'Pharma Group AG'[Gender] = "Male"), 'Pharma Group AG'[FY20 Performance Rating])

- **Average Performance Rating (Women)** = 
AVERAGEX(FILTER('Pharma Group AG', 'Pharma Group AG'[Gender] = "Female"), 'Pharma Group AG'[FY20 Performance Rating])

- **Female Count** = 
CALCULATE( COUNT('Pharma Group AG'[Gender]), 'Pharma Group AG'[Gender] = "Female")

- **Male Count**  = CALCULATE(COUNT('Pharma Group AG'[Gender]),'Pharma Group AG'[Gender] = "Male")
  
- **% Hire of Man** = DIVIDE('New Measures'[Male Count],('New Measures'[Male Count]+'New Measures'[Female Count]))
  
- **Hire of Women** = DIVIDE('New Measures'[Female Count],('New Measures'[Male Count]+'New Measures'[Female Count]))

- **Promoted employees in 2021** = DIVIDE(CALCULATE(COUNT('Pharma Group AG'[In base group for Promotion FY21]),'Pharma Group AG'[In base group for Promotion FY21] = "Yes")COUNT('Pharma Group AG'[In base group for Promotion FY21]), 0) * 100

## **Data Visualization (Dashboard)**

Data visualization for the data analysis (DAX) was done in Microsoft Power BI Desktop: [Live Dashboard](https://app.powerbi.com/groups/me/datasets/3ac2296c-87d4-4cb9-a281-0c01c73f2814/details?experience=power-bi)


**Dashboard:**
Diversity and inclusion dashboard - 1 
![image](https://github.com/user-attachments/assets/07108b93-9d68-4d1a-8675-07759922d265)


Diversity and inclusion dashboard - 2
![image](https://github.com/user-attachments/assets/03db1651-96cb-4344-ae21-5a320b5dee46)






##  **Insights**
 **Workforce and Hiring:**

 - 59% Male and 41% Female hires.

 - Women had a slightly higher average rating (2.42) than men (2.41).

**Promotions by Job Level:**

 - Junior Officer: Highest female representation (53% post-promotion).

 - Senior Levels (Executive/Director): Male dominance (87%-88% Male).

**Turnover Trends:**

- Finance had the highest turnover (11.76%), while HR had the lowest (6.06%).

- Turnover by performance rating: Higher among males (56%-63% Male).

**Leavers and New Hires:**

- Leavers: 55% Male, 45% Female.

- New Hires: 59% Male, 41% Female.

**Age Distribution:**

- 20-29 age group dominates with 223 employees, followed by 30-39.






























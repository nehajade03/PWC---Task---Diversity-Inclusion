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

![image](https://github.com/user-attachments/assets/337d5947-15c9-4474-89a8-e1417fb29b7a)

Diversity and inclusion dashboard - 2

![image](https://github.com/user-attachments/assets/d789544f-31fe-478f-9228-ec9892c971a3)


##  **Insights**


 **Workforce and Hiring Analysis**

- Gender Distribution of Hires:
  
  59% of new hires were male, while 41% were female.
  
   Average performance ratings were slightly higher for women (2.42) compared to men (2.41).

**Promotions by Job Level**

- Junior Officers:
  
  Women held the majority of promotions at this level, accounting for 53% of post-promotion roles.
  
 - Senior Levels (Executive/Director):
   
     Promotions were predominantly male, with 87%-88% of these roles occupied by men.

**Turnover Insights**

- By Department:
  
    The Finance department exhibited the highest turnover rate (11.76%), while HR had the lowest (6.06%).
  
- By Performance Rating:
  
    Turnover was disproportionately higher among males, ranging from 56% to 63% based on performance ratings.

**Employee Movement**

- Leavers:
  
    Male employees accounted for 55% of leavers, while females made up 45%.
  
- New Hires:
  
    The hiring pattern mirrored the leaver statistics, with 59% male and 41% female representation.

 - Workforce Age Distribution 

    Employees aged 20-29 formed the largest demographic, totaling 223 individuals, followed by those aged 30-39.


# **﻿Recommendations**
**Workforce and Gender Diversity**

- Balanced Hiring Practices:
   
    To achieve greater gender parity, implement targeted hiring programs to increase female representation, particularly in senior roles where male dominance is pronounced.
    Diversity Training:
  
    Introduce bias-awareness and exclusivity training for hiring managers to reduce unconscious biases in recruitment and promotions.

**Promotions by Job Level**
 - Mentorship Programs for Women:
   
    Create mentorship and leadership development programs for women to bridge the gender gap in senior executive and director-level roles.
   
 - Transparent Promotion Criteria:
   
    Develop clear, data-driven promotion criteria to ensure fairness and encourage female participation in higher job levels.

**Turnover Management**

  - Retention Strategies for Finance Department:
    
       Address high turnover in the Finance department through employee engagement initiatives, workload management, and competitive compensation packages.
    
   - Performance-Based Retention:
     
       Monitor and support employees with lower performance ratings to reduce turnover rates, particularly among males, by providing training and development opportunities.

**Leavers and New Hires**

  - Exit Interviews: 
    
      Conduct structured exit interviews to identify and address underlying reasons for turnover among both genders.
    
 - Focus on Female Retention:
    
     Strengthen retention policies for women to balance the disparity between leavers and new hires.

**Age Group Engagement**

   - Career Development for Young Employees:
     
     With the 20-29 age group being dominant, implement career progression plans and skill development opportunities to retain and grow talent in this segment.
    
   - Engagement Strategies for 30-39 Age Group:
    
     Focus on flexible working arrangements and professional growth opportunities to sustain engagement with this demographic.

**General Recommendations**

   - Data-Driven Decisions:
      
     Regularly analyze workforce data to identify emerging trends and proactively address gender, age, or department-based disparities.
    
  - Diversity Goals:
    
    Establish measurable diversity and inclusion goals tied to recruitment, retention, and promotion policies.

By implementing these recommendations, the organization can improve diversity, reduce turnover, and foster an inclusive and equitable workplace culture.
























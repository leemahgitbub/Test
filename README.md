
# Project Title

# Sales Report-Dashboard



## Problem Statement

In the highly competitive business environment, tracking and analyzing sales performance is crucial for ensuring sustained growth and profitability. The current challenge is to understand how year-over-year performance (2023 vs. 2022) aligns with business goals, particularly in terms of sales, customer engagement, profitability, and budget utilization.

This report aims to provide actionable insights into these metrics, enabling stakeholders to optimize sales strategies, improve customer engagement, and align expenditures with performance targets.


## Brief Overview of dataset

An excel file which contained 3 worksheet was supplied. The worksheets contained orders,details,and budget data


## Processes
- Data Tranformation

- Creation Dax measures and Calculated columns

- Data Modelling

#### Data Transformation

- Step 1 : Load data into Power BI Desktop, dataset is a csv file.
- Step 2 : Open power query editor 
- Step 3 : Created a custom Date column on the Budget table.

![Transformation 1](https://github.com/user-attachments/assets/e6efb5a6-b3db-41df-ac76-14141c07ad91)

- Step 4 : I unpivoted columns on the details sheets so as to get the number of amount and quantity for each product category.

![Transformation 1](https://github.com/user-attachments/assets/9a661bc6-a0da-4de5-b5cc-fc5de3c143a9)

- Step 5 : Renamed the columns 
- Step 6 : Merged the Details and Orders table using the Order ID.This is to expand the orders table into the Details table
- Step 7 : Then I filtered out null values from the Details table 
- Step 8 : Then closed and applied changes.

#### Dax Measures
- Step 1 : Created a new calendar table 
![Calendar Table](https://github.com/user-attachments/assets/62081206-183d-40fc-a882-84fcda3b2d37)
- Step 2 : Created neccessary Dax measures to visual KPI for the report such as Cuurent year profit,Previous year profit,growth,Year to date budget,Order Count

Below are some the Dax measures created

      YTDCurrryear Sale = 
      VAR Curryear = [Curr_Year]
      RETURN
      CALCULATE([YTD_Sales],'Calendar'[Year]= Curryear)
        

      YTDPrevYear Sale = 
      VAR Prevyear = [Prev_year]
      RETURN
      CALCULATE([YTD_Sales],'Calendar'[Year]= Prevyear)


      Growth = DIVIDE([YTDCurrryear Sale]-[YTDPrevYear Sale],[YTDPrevYear Sale])

      
      YTD BGT = 
      VAR monthindex = SELECTEDVALUE(YTDMonth[Month])
      RETURN
      CALCULATE([BGT Value],'Calendar'[Month]<=monthindex)
           
      
      CurrYr_Profit = VAR curryear = Config[Curr_Year]
      RETURN
      CALCULATE([Profit],'Calendar'[Year] = curryear) 

      
      Curr_vs_Bgt = DIVIDE([YTDCurrryear Sale],[YTD BGT],0)    
           

#### Dax Modelling    
        
- Created connections between tables to create and interactive report.

![Data Modelling](https://github.com/user-attachments/assets/79651692-43b5-4c09-a153-c83a7c72ee84)

#### Data Visualization

Below is a snap shot of KPI created using the above measure

  ![KPI cards](https://github.com/user-attachments/assets/ab8ca086-c9df-4877-ad92-e535d62fee0e)
  
  
 
 

# Snapshot of Dashboard (Power BI Service)


The report was then published to Power BI Service.
 
 
![PowerBI service Report](https://github.com/user-attachments/assets/e9baad3e-a06e-489b-b3bd-7cf0c041dbc5)


# Report Snapshot (Power BI DESKTOP)
![PowerBI Desktop](https://github.com/user-attachments/assets/00240ac6-1071-4b7b-9819-04a00a1b9471)

 
 

 


# Insights

A single page report was created on Power BI Desktop & it was then published to Power BI Service.

Following inferences can be drawn from the dashboard;

Sales Growth: Sales in 2023 reached 202K, representing a 58.5% increase compared to 128K in 2022, indicating strong year-over-year growth.

Customer Base Expansion: The total customers in 2023 stand at 2052, reflecting a positive trend in customer acquisition or retention efforts.

Category Performance: Some sub-categories show significant growth, with the highest sub-category sales reaching 33K, while others remain underperforming.

Seasonality in Sales: March recorded the highest monthly sales at 59K, whereas months like July and August showed notably lower sales activity.

Profitability: Total profit for 2023 is 54K, constituting approximately 26.7% of total sales, raising the need to examine cost and margin structures.

Budget Utilization: At 77% of the YTD budget, spending appears well-aligned with sales performance.

Order Volume: A total of 580 orders were recorded, with 95.34% contributed by 2023, reflecting a substantial increase from the previous year.


 
 


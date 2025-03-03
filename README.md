# PowerBI_Retail_Analysis
Power BI Retail Analysis

## Overview :

This Power BI project analyzes retail data by managing multiple tables, creating relationships, and using DAX formulas to enhance the dataset. The objective is to generate insights into sales, customer distribution, and cancellation trends through interactive dashboards.

## Business Context

The goal of this project is to load, clean, and transform retail data from four disparate files, ensuring proper relationships between tables. Key performance metrics such as revenue, transactions, and cancellations are analyzed by city, zone, city tier, and time (month, week, weekday).

## Dataset Details :

The dataset consists of the following tables:

- PinCode-Geo: Contains geographic data, including city, zone, and pincode.

- Mod3_Raw_CityTier: Provides information on city tiers.

- Sales Raw: Includes transaction details, order date, revenue, units, and cancellations.

- Mod3_Raw_ProductMaster: Contains product-related information.


### Data Cleaning & Transformation :


- Dropped records from PinCode-Geo where 'Zone' is missing.

- Removed records from Mod3_Raw_CityTier where 'CityTier' is missing.

- Established relationships between common columns (e.g., City in Mod3_Raw_CityTier and PinCode-Geo).

- Created new calculated columns using DAX:

	- Net_Units = 'Sales Raw'[Units]-'Sales Raw'[Cancelled_Units] (![image](https://github.com/user-attachments/assets/f2b10da2-6e68-4d84-af29-5c252c46794c)
)


	- OrderDayOfWeek = FORMAT('Sales Raw'[OrderDate].[Day],"dddd") (![image](https://github.com/user-attachments/assets/2acc9fe4-00dd-4fe4-9e0b-17c967523d78)
)

	- OrderWeekStart = FORMAT(('Sales Raw'[OrderDate] - WEEKDAY('Sales Raw'[OrderDate],2)+1),"mmm dd")  (![image](https://github.com/user-attachments/assets/122c0e3b-b767-443e-bb8a-54dd6a6d974a)
)

	- Total_Revenue = CALCULATE(SUM('Sales Raw'[Revenue]),'Sales Raw'[Net_Units]>0)  (![image](https://github.com/user-attachments/assets/175b7fdd-3f00-4dae-87aa-960653b02642)
)



### Key Metrics & Insights :


The dashboards provide insights into:

- Total Revenue: $38.84M

- Total Customers: 83K

- Total Transactions: 84.76K

- Net Units Sold: 60.33K

- City-wise Analysis:

### Power BI Dashboard Features :


City Analysis Dashboard

- Visualizations: Line charts, pie charts, and treemaps

- Filters for city, zone, and city tier

Date Analysis Dashboard 

- Revenue and transaction trends by month and week

- Cancellations and net units by month

- Weekly performance insights

- Tools & Technologies Used

- Power BI for data visualization


### Files in Repository :


Retail_Analysis.pbix - Power BI report file

City_Analysis.png - Screenshot of city-wise insights

Date_Analysis.png - Screenshot of date-wise insights

README.md - PowerBI_Retail_Analysis


### How to Use :


Download the Retail_Analysis.pbix file.

Open it in Power BI Desktop.

Explore different dashboards and insights using the filters and visuals.

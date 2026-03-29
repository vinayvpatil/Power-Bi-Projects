
# 🚢 Awesome Chocolate - Shipment & Sales Analytics Dashboard

#### 🔗 Live Dashboard
Explore the interactive dashboard here:
👉 [  View   ](https://app.powerbi.com/view?r=eyJrIjoiYzdlYTQ2MjYtZDM5OC00NGNjLWI4Y2YtNzY5ZWZkOTM1Nzk0IiwidCI6ImRjODhkNWNiLWMxMjEtNDUzYi1hMGRiLTFmMzlmYjEyMjJiMyJ9)
***
**Advanced Power BI Solution with Dynamic DAX Calculations**

***

## About This Project

Working on the Awesome Chocolate shipment and sales dashboard gave me the opportunity to combine strong data modeling skills with business insight. The goal? To equip the supply chain and sales teams with clear, timely, and actionable intelligence that helps them optimize performance and increase profitability.

With thoughtfully designed DAX measures and an intuitive data model, this dashboard makes complex logistics and financial data easy to understand, fast to analyze, and simple to act upon.

***

## Problem Statement

Managing shipment logistics and sales performance in the chocolate industry involves complex variables such as fluctuating shipment volumes, varying costs, and tight profit margins. Without timely, accurate analytics, decision-makers risk inefficiencies and lost revenue.

***

## Objective

- To provide a dynamic and scalable dashboard for monitoring shipments, sales, costs, and profits.
- To enable month-over-month trend analysis for proactive management.
- To incorporate intelligent profit targets and shipment segmentation for optimized operations.
- To drive data-driven decisions to improve supply chain efficiency and business performance.

***

## Dataset Description

- **Shipments Table:** Contains transactional data on shipments with fields such as Sales, Cost, Boxes, and shipment dates.
- **Calendar Table:** Date dimension used for time intelligence calculations, includes year, month, and [Start of Month] fields.

These tables are related by shipment date fields for context-aware analysis.

***

## Methodology

- Data is ingested into Power BI from source systems (shipping and sales databases).
- A star-schema model relates shipments and calendar data.
- Advanced DAX calculations create dynamic KPIs and comparisons, including month-over-month changes and profit margin indicators.
- Metrics automatically update based on the latest calendar date, ensuring always-current reporting.
- Visuals are designed for clarity, with conditional formatting highlighting performance against defined targets.

***

## Dashboard Features

- **Dynamic Monthly KPIs:** Total Shipments, Sales, Cost, Profit, and Boxes with automatic updates.
- **Month-over-Month Change Indicators:** For Sales, Shipments, Boxes, and Cost with percentage change calculations.
- **Profit Analysis:** Real-time profit percentage and intelligent Profit Target Indicator with color-coded status.
- **Shipment Size Segmentation:** Insights on small shipments via LBS Count and LBS % metrics.
- **Interactive Date Filtering:** Select specific date ranges or months for tailored analysis.
- **Executive Summary Tiles:** High-level metrics with visual cues for quick consumption.

***

## Dashboard Images 

![image alt](https://github.com/SatyaGanesh07/Awesome-Choco-Sales-Analytics-PowerBi/blob/543d525380b1b08c27671459073e7926945b4533/Dashboards/dashboard1.png)
*High-level sales and overall performance summary*

![image alt](https://github.com/SatyaGanesh07/Awesome-Choco-Sales-Analytics-PowerBi/blob/543d525380b1b08c27671459073e7926945b4533/Dashboards/dashboard2.png)
#####
![image alt](https://github.com/SatyaGanesh07/Awesome-Choco-Sales-Analytics-PowerBi/blob/543d525380b1b08c27671459073e7926945b4533/Dashboards/dashboard3.png)
*Detailed insight into product-wise sales, profit, and shipment quality*



***

## Core DAX Measures

| Measure Name                    | Description                                                         |
|---------------------------------|---------------------------------------------------------------------|
| **Total Shipments**             | Total count of shipments for Awesome Chocolate                      |
| **Total Sales**                 | Aggregate revenue from shipments                                    |
| **Total Cost**                  | Sum of shipment costs                                              |
| **Total Profit**                | Net profit: Total Sales minus Total Cost                            |
| **Total Boxes**                 | Total number of boxes shipped                                       |
| **LBS Count / LBS %**           | Number and percentage of shipments with fewer than 50 boxes        |
| **MoM Shipments Change %**      | Percentage change in shipments month-over-month                     |
| **MoM Sales Change %**          | Month-over-month sales growth percentage                            |
| **MoM Boxes Change %**          | Month-over-month box count percentage change                        |
| **MoM Cost Changes %**          | Month-over-month cost percentage change                             |
| **Profit %**                    | Profit margin percentage                                            |
| **Profit Target**               | Target profit margin (defaulted at 60%)                            |
| **Profit Target Indicator**     | Flag indicating profit target status: Above, Near, or Below Target |

***

## Sample DAX Calculations

```DAX
-- Total Shipments
Total Shipments = COUNTROWS(shipments)

-- Total Sales (Latest Month)
Total Sales Latest Month =
VAR ld = [latest date]
RETURN CALCULATE([Total Sales], 'calendar'[Start of Month] = ld)

-- Month-over-Month Sales Change %
latest MoM Sales Change % =
VAR ld = [latest date]
VAR this_month_sales = [Total Sales Latest Month]
VAR prev_month_sales = CALCULATE([Total Sales], 'calendar'[Start of Month] = EDATE(ld, -1))
RETURN DIVIDE(this_month_sales - prev_month_sales, prev_month_sales)

```

***

## Model Design Principles

- **Star-Schema Modeling:**  
  Structured relationships ensure accurate, flexible time intelligence calculations.

- **Readability & Maintainability:**  
  Meaningful measure names and comments make ongoing development and handoff seamless.

- **Performance Optimization:**  
  DAX best practices applied for efficient report refresh and user experience.

***

## Getting Started

1. Connect your Awesome Chocolate shipment and calendar datasets.
2. Verify date fields and refresh the model.
3. Explore the dashboard to monitor shipments, sales, and profits with real-time calculations.

***

## Final Words

This project reflects a combination of analytical rigor and business savvy. It demonstrates my ability to translate complex data into clear, high-value insights and to deliver tools that support real-world business success.

I'm excited to bring these skills and this mindset into my next role — driving impactful data solutions that empower effective decision-making.

***

## Contact

For any questions or suggestions, please open an issue or contact me via LinkedIn:  
[Satya Ganesh LinkedIn](https://www.linkedin.com/in/satya-ganesh-5a89b2283/)


**Delivering transformative analytics that ensure every chocolate shipment drives profitability and growth.**


# 📘 Data Dictionary – Awesome Chocolates Dataset

The dataset follows a **star schema** with one fact table and multiple dimension tables.

---

## 1. Shipments - Fact_Table  
Main fact table containing sales transactions.

| Field Name     | Data Type | Description                                                                 |
|----------------|-----------|-----------------------------------------------------------------------------|
| **Sales Person** | Text      | Name of the salesperson responsible for the shipment.                      |
| **Geography**    | Text      | Geographic code/short name of the location (links to *Locations_Dim*).     |
| **Product**      | Text      | Product identifier (links to *Products_Dim*).                              |
| **Date**         | Date      | Date of the shipment (links to *Calendar_Dim*).                            |
| **Sales**        | Numeric   | Total sales value (revenue) for the shipment in currency units.            |
| **Boxes**        | Numeric   | Number of boxes of product shipped.                                        |

---

## 2. Products_Dim  
Contains descriptive details about products.

| Field Name       | Data Type | Description                                                |
|------------------|-----------|------------------------------------------------------------|
| **Product**        | Text      | Unique product identifier (joins with fact table).         |
| **Category**       | Text      | Product category (e.g., Dark Chocolate, Milk Chocolate).   |
| **Cost per box**   | Numeric   | Standard cost price of one box of the product.             |

---

## 3. People_Dim  
Contains information about sales personnel.

| Field Name       | Data Type | Description                                               |
|------------------|-----------|-----------------------------------------------------------|
| **Sales person**   | Text      | Name of the salesperson (joins with fact table).          |
| **Team**           | Text      | Team or department to which the salesperson belongs.      |

---

## 4. Locations_Dim  
Contains information about geographic regions.

| Field Name | Data Type | Description                                            |
|------------|-----------|--------------------------------------------------------|
| **Geo**      | Text      | Geographic code/short name (joins with fact table).    |
| **Region**   | Text      | Region name (e.g., North, South, East, West).          |

---

## 5. Calendar_Dim  
Contains the time dimension for analysis.

| Field Name | Data Type | Description                           |
|------------|-----------|---------------------------------------|
| **Date**     | Date      | Calendar date (joins with fact table).|

---

⚡ With these tables, analysis can be performed by **time, product, salesperson, and geography**, enabling business intelligence insights.
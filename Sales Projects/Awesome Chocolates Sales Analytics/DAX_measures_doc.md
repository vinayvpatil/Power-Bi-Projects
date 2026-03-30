# 📊 DAX Measures – Awesome Chocolates

This document contains all the key DAX measures used in the Awesome Chocolates dashboard, organized into logical sections for clarity.

---

## 📌 Core Metrics

These measures capture the fundamental performance indicators.

```DAX
Total Sales = SUM(shipments[Sales])

Total Shipments = COUNTROWS(shipments)

Total Boxes = SUM(shipments[Boxes])

Total Cost = SUM(shipments[Costs])

Total Profit = [Total Sales] - [Total Cost]

Profit % = DIVIDE([Total Profit], [Total Sales])
```

### Low Box Shipments (LBS)
```DAX
LBS Count = 
    CALCULATE(
        [Total Shipments],
        shipments[Boxes] < 50
    )

LBS % = DIVIDE([LBS Count], [Total Shipments])
```

---

## 📅 Previous Month Metrics

These measures calculate values for the previous month to enable MoM comparisons.

```DAX
Total Sales (prev month) = 
    CALCULATE([Total Sales], PREVIOUSMONTH('calendar'[Date]))

Total Shipments (prev month) = 
    CALCULATE([Total Shipments], PREVIOUSMONTH('calendar'[Date]))

Total Boxes (prev month) = 
    CALCULATE([Total Boxes], PREVIOUSMONTH('calendar'[Date]))

Total Cost (prev month) = 
    CALCULATE([Total Cost], PREVIOUSMONTH('calendar'[Date]))

Total Profit (prev month) = 
    CALCULATE([Total Profit], PREVIOUSMONTH('calendar'[Date]))
```

---

## 🔄 Month-on-Month (MoM %) Change

These measures calculate the percentage change compared to the previous month.

```DAX
MoM Sales Change % = 
    VAR this_month = [Total Sales]
    VAR prev_month = [Total Sales (prev month)]
RETURN
    DIVIDE(this_month - prev_month, prev_month)

MoM Shipments Change % = 
    VAR this_month = [Total Shipments]
    VAR prev_month = [Total Shipments (prev month)]
RETURN
    DIVIDE(this_month - prev_month, prev_month)

MoM Boxes Change % = 
    VAR this_month = [Total Boxes]
    VAR prev_month = [Total Boxes (prev month)]
RETURN
    DIVIDE(this_month - prev_month, prev_month)

MoM Cost Change % = 
    VAR this_month = [Total Cost]
    VAR prev_month = [Total Cost (prev month)]
RETURN
    DIVIDE(this_month - prev_month, prev_month)

MoM Profit Change % = 
    VAR this_month = [Total Profit]
    VAR prev_month = [Total Profit (prev month)]
RETURN
    DIVIDE(this_month - prev_month, prev_month)
```

---

## 📆 Latest Month Metrics

These measures calculate performance values for the latest available month.

```DAX
Latest Date = LASTDATE('calendar'[Start of Month])
```

```DAX
Total Sales Latest Month = 
    VAR ld = [Latest Date]
RETURN
    CALCULATE([Total Sales], 'calendar'[Start of Month] = ld)

Total Shipments Latest Month = 
    VAR ld = [Latest Date]
RETURN
    CALCULATE([Total Shipments], 'calendar'[Start of Month] = ld)

Total Boxes Latest Month = 
    VAR ld = [Latest Date]
RETURN
    CALCULATE([Total Boxes], 'calendar'[Start of Month] = ld)

Total Cost Latest Month = 
    VAR ld = [Latest Date]
RETURN
    CALCULATE([Total Cost], 'calendar'[Start of Month] = ld)

Total Profit Latest Month = 
    VAR ld = [Latest Date]
RETURN
    CALCULATE([Total Profit], 'calendar'[Start of Month] = ld)
```

---

## 📊 Latest Month-on-Month (MoM %) Change

```DAX
Latest MoM Sales Change % = 
    VAR ld = [Latest Date]
    VAR this_month_sales = [Total Sales Latest Month]
    VAR prev_month_sales = 
        CALCULATE([Total Sales], 'calendar'[Start of Month] = EDATE(ld, -1))
RETURN
    DIVIDE(this_month_sales - prev_month_sales, prev_month_sales)

Latest MoM Shipments Change % = 
    VAR ld = [Latest Date]
    VAR this_month_shipments = [Total Shipments Latest Month]
    VAR prev_month_shipments = 
        CALCULATE([Total Shipments], 'calendar'[Start of Month] = EDATE(ld, -1))
RETURN
    DIVIDE(this_month_shipments - prev_month_shipments, prev_month_shipments)

Latest MoM Boxes Change % = 
    VAR ld = [Latest Date]
    VAR this_month_boxes = [Total Boxes Latest Month]
    VAR prev_month_boxes = 
        CALCULATE([Total Boxes], 'calendar'[Start of Month] = EDATE(ld, -1))
RETURN
    DIVIDE(this_month_boxes - prev_month_boxes, prev_month_boxes)

Latest MoM Cost Change % = 
    VAR ld = [Latest Date]
    VAR this_month_cost = [Total Cost Latest Month]
    VAR prev_month_cost = 
        CALCULATE([Total Cost], 'calendar'[Start of Month] = EDATE(ld, -1))
RETURN
    DIVIDE(this_month_cost - prev_month_cost, prev_month_cost)

Latest MoM Profit Change % = 
    VAR ld = [Latest Date]
    VAR this_month_profit = [Total Profit Latest Month]
    VAR prev_month_profit = 
        CALCULATE([Total Profit], 'calendar'[Start of Month] = EDATE(ld, -1))
RETURN
    DIVIDE(this_month_profit - prev_month_profit, prev_month_profit)
```

---

## 🎯 Other Measures

```DAX
Profit Target = 0.6

Profit Target Indicator = 
    IF(
        [Profit %] > [Profit Target], 2,
        IF([Profit %] > 0.9 * [Profit Target], 1, 0)
    )
```

---

## ⚙️ Parameter Measure

Used for dynamic measure selection.

```DAX
Measure Selector = {
    ("Sales", NAMEOF('_measures'[Total Sales]), 0),
    ("Boxes", NAMEOF('_measures'[Total Boxes]), 1),
    ("Shipments", NAMEOF('_measures'[Total Shipments]), 2),
    ("Cost", NAMEOF('_measures'[Total Cost]), 3),
    ("Profit", NAMEOF('_measures'[Total Profit]), 4)
}
```

---

✅ This formatting makes the measures easier to **read, copy, and maintain** while giving clear **business context**.
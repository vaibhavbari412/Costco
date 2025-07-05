
# 📊 Global Sales Performance Dashboard | Power BI  
> 🚀 Interactive analytics with dynamic revenue & order targets, YoY KPIs and storytelling

![Dashboard Banner](https://github.com/vaibhavbari412/Costco/blob/main/Costco%20Logo.png)

---

## 📍 **Project Overview**
This project is a **Power BI executive dashboard** that helps stakeholders monitor global sales, revenue targets, and order trends in real time.  
It uses **dynamic DAX measures** to set revenue and order targets, compare with last year’s performance, and visualize actionable insights.

---

## 🌟 **Highlights**
✅ Dynamic revenue & order targets based on historical data  
✅ YoY comparison KPIs with text & icons ▲▼  
✅ Drillthrough to detail by product or region  
✅ Multi-page navigation & slicers for interactivity  
✅ Automated updates & clean data modeling

---

## 📊 **Business Questions Answered**
- What is the current revenue vs last year? 📈
- How far are we from our monthly revenue & order targets? 🎯
- Which regions and products are driving growth? 🌍
- How are orders trending YoY? 📦
- What are the best vs lowest performing months?

---

## 🎨 **Dashboard Design**
- Overview page: total revenue, profit, order count, YoY KPIs
- Revenue & order target vs actual visuals
- Drillthrough by product, region, or month
- Time slicers: year, quarter, month
- Clear KPI cards and dynamic arrows ▲▼

![Dashboard Overview](https://github.com/vaibhavbari412/Costco/blob/main/Costco%20dashboard.png)
![ERD Diagram](https://github.com/vaibhavbari412/Costco/blob/main/Costco%20ERD.png)


---

## 🧩 **Data & Modeling**
| Component             | Details                                                             |
|---------------------:|----------------------------------------------------------------------|
| 🔗 Sources           | Excel / CSV / database export                                        |
| 📐 Data Model       | Star schema: fact table + calendar + dimensions                       |
| 🛠️ Transformations | Power Query for cleaning & shaping data                                |
| ⚙️ Measures         | Advanced DAX for KPIs, targets & YoY comparisons                       |

---

## 🧮 **Example DAX Measures**

```DAX
-- 📈 Revenue KPI: YoY difference with ▲▼ arrow
revenue KPI =
VAR LastYearRevenue = CALCULATE([total revenue], SAMEPERIODLASTYEAR('calendar'[Date]))
VAR CurrentYearRevenue = CALCULATE([total revenue], DATESYTD('calendar'[Date]))
VAR diff= CurrentYearRevenue - LastYearRevenue
VAR AbsDiff = ABS(diff)
RETURN IF(
    ISBLANK(LastYearRevenue),
    "No Sale Last year",
    IF(diff>0,
        FORMAT(AbsDiff/1000,"0.0") & "K More than last year (▲)",
        FORMAT(AbsDiff/1000,"0.0") & "K Less than last year (▼)"
    )
)
```
> Shows revenue difference in K with dynamic text & arrow.

---

```DAX
-- 🎯 Monthly revenue target
revenue target =
VAR LastMonthSale = CALCULATE([total revenue], PREVIOUSMONTH('calendar'[Date]))
RETURN IF(
    ISBLANK(LastMonthSale),
    25000,
    LastMonthSale * 1.2
)
```
> Sets this month’s revenue target as 120% of last month, or fallback to 25K.

---

```DAX
-- 📦 Orders target
orders target =
VAR LastyearOrders = CALCULATE([total orders], SAMEPERIODLASTYEAR('calendar'[Date]))
VAR SelectedYear = CALCULATE(DISTINCTCOUNT('calendar'[Year]), ALLSELECTED('calendar'))
RETURN IF(
    SelectedYear = 0,
    15000,
    IF(ISBLANK(LastyearOrders), 2000, LastyearOrders * 1.2)
)
```
> Dynamic target: based on last year’s orders, user-selected year, or fallback.

---

## 📊 **Business Impact**
✅ Quickly see performance vs goals  
✅ Support data-driven decisions for marketing & inventory  
✅ Encourage sales teams to beat targets  
✅ Clear communication to executives with dynamic KPI text

---

## 🛠️ **Tech Stack**
- Power BI Desktop, Power Query, DAX
- Star schema & time intelligence
- Drillthrough, bookmarks & slicers

---

## 🧰 **Key Learnings**
- Dynamic DAX measures & targets
- SAMEPERIODLASTYEAR, PREVIOUSMONTH & DATESYTD functions
- Combining visuals + dynamic text KPIs
- Building dashboards for non-technical stakeholders

---

## 🚀 **How to Use the Dashboard**
1. Open PBIX file locally
2. Use slicers to filter year, region or product
3. Hover over KPIs for detailed tooltips
4. See live YoY KPIs with ▲▼ and targets

---

## 📂 **Repository Structure**
```
📦 Global_Sales_Dashboard
├── Images/
│   ├── overview.png
│   ├── target_vs_actual.png
│   └── by_region.png
├── Global_Sales_Dashboard.pbix
└── README.md
```

---

## ⭐ **Like this project?**
If you found it useful:
- ⭐ Star this repo
- 🔗 Connect on [LinkedIn](https://www.linkedin.com/in/your-profile)
- 📧 vaibhavbari@example.com

> *Great dashboards are built on great data stories!*

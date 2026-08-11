# **Power-BI-Mastery-Dynamic-Dashboards-Advanced-DAX**  

### 📊 **Project Overview**  
An **Advanced Power BI Sales Dashboard** built to track key financial metrics and support data driven decision making.

- Uses **dynamic bookmarks** for guided, interactive storytelling across the report
- Applies **complex DAX calculations** for YoY growth, profit, and performance metrics
- Delivers **executive level insights** for high level, business wide decision making
- Delivers **operational level insights** for slicer driven, day to day performance tracking

## **📊 Dashboard Preview**  
[**Click to view the LIVE dashboard via Power BI web Link**](https://app.powerbi.com/view?r=eyJrIjoiNTQ0YTllMGItMjUxNi00ZDdiLThmZmUtMGQxNWI4ODdkMGExIiwidCI6IjY3NmQ5MDg1LTQzMjMtNDc2NS1iZTVjLWNjMDdlMTEyMTA5MiJ9) 

<div style="display: flex; flex-direction: row;">
  <img src="Icons & Screenshots/Dashboard.gif" alt="Dashboard" width="450" style="margin-right: 20px;">
</div>

---

### 🏢 **Industry Use Case**  
Sales performance analysis helps organizations **optimize revenue**, **monitor trends**, and **strengthen strategic decision making**.

This project applies **business intelligence best practices** and **data visualization techniques** to turn raw sales data into actionable insights on **YoY growth**, **customer satisfaction**, and **profitability**.
---

## **🔹 Key Features & Functionalities**  

### **📌 Executive-Level Insights**  
- **YoY Growth Analysis:** High-level growth trends using **REMOVEFILTERS()** to ensure business-wide visibility.  
- **Gross Sales & Profit KPIs:** Key financial indicators with comparisons to historical performance.  
- **Customer Satisfaction Score:** Aggregated customer feedback displayed dynamically.  

### **📌 Operational-Level Insights**  
- **Monthly & Yearly Trend Analysis:** Performance tracking over time, responding to slicer selections.  
- **Dynamic Bookmarking:** Interactive navigation for seamless storytelling.  
- **DAX-Based Performance Metrics:** Implementing **calculated measures for in-depth analysis** of sales trends.  

### **📌 Advanced DAX Calculations**  
- **Dynamic YoY Growth:**  
   - **Executive View:** Business-wide perspective ignoring slicer filters.  
   - **Operational View:** YoY growth influenced by user-selected filters.  
- **Customer Satisfaction Score:** Aggregating satisfaction ratings dynamically.  

---

## **🛠️ Technologies & Tools Used**  
| **Technology** | **Purpose** |  
|---------------|------------|  
| Power BI | Data visualization & dashboard development |  
| DAX (Data Analysis Expressions) | Advanced calculations & KPIs |  
| Power Query | Data transformation & cleansing |  
| SQL (optional) | Data extraction & preprocessing |  
| Excel | Initial dataset review & structuring |  

---

## **📂 Project Structure**  
```bash
📁 Sales-Performance-Analysis
│── 📂 Data          # Contains raw & cleaned data files  
│── 📂 PowerBI       # Power BI .pbix file with reports  
│── 📂 DAX           # Custom DAX scripts & calculations  
│── 📂 Screenshots   # Dashboard previews & insights  
│── 📜 README.md     # Documentation (this file)  
```


## **📌 DAX Code Snippets**  

### **YoY Growth – Executive Level**  
```DAX
Executive YoY% Dynamic = 
VAR _LatestYear = 
    CALCULATE( MAX( CalendarTable[Year] ), ALL( CalendarTable ) )

VAR _PreviousYear = _LatestYear - 1

VAR _Current12MonthSales = 
    CALCULATE(
        Measures_Sales[Total Sales], 
        CalendarTable[Year] = _LatestYear,
        REMOVEFILTERS( CalendarTable )
    )

VAR _Previous12MonthSales = 
    CALCULATE(
        Measures_Sales[Total Sales], 
        CalendarTable[Year] = _PreviousYear,
        REMOVEFILTERS( CalendarTable )
    )

VAR _Result =
    IF(
        NOT(ISBLANK(_Previous12MonthSales)), 
        (_Current12MonthSales - _Previous12MonthSales) / _Previous12MonthSales, 
        BLANK()
    )

RETURN _Result
```
---

## **🚀 How to Use This Project**  
1️⃣ **Clone the Repository**  
```bash
git clone https://github.com/yourusername/Sales-Performance-Analysis.git
```  
2️⃣ **Open Power BI and Load the `.pbix` File**  
3️⃣ **Explore the Dashboard & Interact with Slicers**  
4️⃣ **Review DAX Scripts for Advanced Insights**  

---

## Key Learnings and Takeaways

- Built YoY growth measures at two levels, one using REMOVEFILTERS for a business wide executive view, and one that responds to slicer selections for operational analysis
- Learned when to use REMOVEFILTERS versus ALL in DAX, and how each changes the filter context for reporting
- Designed dynamic bookmarks to create a guided, interactive storytelling flow across the dashboard
- Wrote optimized DAX measures for gross sales, profit, and customer satisfaction scoring
- Practiced structuring a Power BI project end to end, from raw data in Excel and SQL through Power Query transformation to final published dashboard

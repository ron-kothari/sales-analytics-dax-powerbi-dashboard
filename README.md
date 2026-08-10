# **Power-BI-Mastery-Dynamic-Dashboards-Advanced-DAX**  

### 📊 **Project Overview**  
This project showcases an **Advanced Power BI Sales Dashboard**, incorporating **dynamic bookmarks, complex DAX calculations, and interactive storytelling techniques** to analyze business sales performance. Designed to **track key financial metrics**, the dashboard provides insights for both **executive-level decision-making** and **operational-level performance analysis**.  

---

## **📊 Dashboard Preview**  
[Click to view dashboard via Power BI web Link](https://app.powerbi.com/view?r=eyJrIjoiNTQ0YTllMGItMjUxNi00ZDdiLThmZmUtMGQxNWI4ODdkMGExIiwidCI6IjY3NmQ5MDg1LTQzMjMtNDc2NS1iZTVjLWNjMDdlMTEyMTA5MiJ9) 

<div style="display: flex; flex-direction: row;">
  <img src="Icons & Screenshots/Dashboard.gif" alt="Dashboard" width="400" style="margin-right: 20px;">
</div>

---

### 🏢 **Industry Use Case**  
Sales performance analysis is critical for organizations looking to **optimize revenue, monitor trends, and enhance strategic decision-making**. This project applies **best practices in business intelligence (BI) and data visualization** to provide actionable insights into **YoY growth, customer satisfaction, and profitability**.  

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

## **🔮 Key Learnings & Takeaways**  
✔️ **Understanding YoY Analysis** at both executive and operational levels  
✔️ **Building Interactive Power BI Dashboards** with bookmarks & storytelling  
✔️ **Writing Optimized DAX Measures** for business performance analysis  
✔️ **Using REMOVEFILTERS vs ALL in DAX** for strategic reporting  

---

## **🎯 Target Audience**  
✅ **Data Analysts & BI Professionals** – Learn how to implement advanced Power BI techniques  
✅ **Recruiters & Hiring Managers** – Evaluate Power BI skills with a practical case study  
✅ **Businesses & Clients** – Gain insights into sales trends & data-driven decision-making  

---

## **📢 Connect With Me**  
🔗 **LinkedIn:** [Connect](https://www.linkedin.com/in/israeljosiah/)  
🔗 **Portfolio:** [Portfolio Link](https://www.datascienceportfol.io/IsraelJosiah)  
📧 **Email:** Israeljvow@gmail.com  

🙌 If you find this project useful, don't forget to ⭐ **star** the repository! 🚀  

---

### **📌 Final Thoughts**  
This project **bridges the gap between executive-level and operational analytics**, offering insights into how **advanced Power BI dashboards** can drive **business decisions with data**.  

Looking forward to your feedback & contributions! 💡🔥

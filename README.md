# 📊 Power BI Sales Dashboard with Dynamic DAX

This is a sales performance dashboard I built in Power BI to practice advanced DAX and dashboard design beyond the basics. It covers year over year growth, gross sales, profit, and customer satisfaction, and it is built to work for two different audiences at once. An executive can look at the dashboard and get a company wide view. An operations person can slice into monthly and yearly trends and get numbers that respond to their filters.

## **📊 Dashboard Preview**  
[Click to **view** dashboard via Power BI web Link](https://app.powerbi.com/view?r=eyJrIjoiNTQ0YTllMGItMjUxNi00ZDdiLThmZmUtMGQxNWI4ODdkMGExIiwidCI6IjY3NmQ5MDg1LTQzMjMtNDc2NS1iZTVjLWNjMDdlMTEyMTA5MiJ9) 

<div style="display: flex; flex-direction: row;">
  <img src="Icons & Screenshots/Dashboard.gif" alt="Dashboard" width="800" style="margin-right: 20px;">
</div>




## 🧠 Why I built this

Most beginner Power BI projects stop at basic charts and a few slicers. I wanted to go further and solve a real problem that comes up in business reporting: executives usually want numbers that ignore whatever filter someone else applied, while operational teams want numbers that move with their selections. Getting both to work correctly in the same report means writing DAX that handles filter context on purpose instead of by accident.

## 📈 What is in the dashboard

**Executive view**
- Year over year growth using REMOVEFILTERS, so the numbers stay consistent no matter what a user clicks elsewhere in the report
- Gross sales and profit totals
- Aggregated customer satisfaction score

**Operational view**
- Monthly and yearly trends that respond live to slicer selections
- Dynamic bookmarks for moving through different views without extra pages

## 🛠️ Tools used

- Power BI, for the dashboard itself
- DAX, for the calculated measures
- Power Query, for cleaning and shaping the data
- Excel, for reviewing the raw dataset before bringing it in

## 🧮 Example: year over year growth

Here is the DAX behind the executive level growth calculation. It grabs the latest year in the data, compares it to the year before, and calculates percent growth while ignoring any slicer selections so the number stays stable at the executive level.

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

## 📁 Project structure

Sales-Performance-Analysis
├── Data          raw and cleaned data files
├── PowerBI       the .pbix file with the full report
├── DAX           standalone DAX scripts and calculations
├── Screenshots   dashboard previews
└── README.md

## 🚀 Running it yourself

Clone the repo, then open the .pbix file in Power BI Desktop.

git clone https://github.com/ron-kothari/Power-BI-Mastery-Dynamic-Dashboards-Advanced-DAX.git

Once it is open, use the slicers to move between monthly and yearly views, and check the DAX scripts folder if you want to see how each measure is built.

## 💡 What I learned

- The real difference between REMOVEFILTERS and ALL in DAX, and when to use each one depending on whether a number should stay fixed or move with the user
- How to use dynamic bookmarks to guide someone through a report without needing five separate pages
- How to write DAX measures that hold up when non technical stakeholders start clicking around
- How to design one report that actually serves two different audiences instead of forcing a compromise

# Power BI Project: Global Superstore Sales Analysis

## Overview
Comprehensive business intelligence dashboard analyzing global retail sales data across multiple markets, product categories, and time periods. This project demonstrates end-to-end data analysis workflow including data transformation, relationship modeling, and interactive visualization using Microsoft Power BI Desktop.

## Course Information
**Course:** CSC 245 - Introduction to Data Science  
**Institution:** CUNY College of Staten Island  
**Semester:** Fall 2025  
**Tool:** Microsoft Power BI Desktop

## Project Objectives
- Load and transform raw business data from multiple sources
- Build relationships between datasets for comprehensive analysis
- Create interactive visualizations for business insights
- Calculate year-over-year growth metrics
- Design professional, multi-page analytical reports

## Business Problem
A global superstore needs to analyze sales performance across:
- **5 Geographic Markets:** Asia Pacific, Europe, USCA, LATAM, Africa
- **3 Product Categories:** Furniture, Office Supplies, Technology
- **4-Year Period:** 2021-2024
- **Key Metrics:** Revenue, profit, growth trends, category performance

**Goal:** Provide actionable insights for strategic business decisions through data visualization.

---

## Dashboard Pages

### Page 1: Market Analysis

**Screenshot:** `page1-market-analysis.png`

**Visualizations:**
1. **Sum of Sales by Market** (Horizontal Bar Chart)
   - Shows total revenue by geographic region
   - Asia Pacific leads with ~$4.7M in sales
   - Africa has lowest performance with ~$700K

2. **Sum of Sales by Market and Category** (Clustered Column Chart)
   - Breaks down revenue by product category within each market
   - Technology (orange) is strongest in Asia Pacific
   - Furniture (blue) performs consistently across all markets

3. **Sum of Sales by Market and Category** (Stacked Column Chart)
   - Alternative visualization showing category composition
   - Enables easy comparison of category mix across markets
   - Clearly shows Asia Pacific's dominance in all categories

**Key Insights from Page 1:**
- Asia Pacific generates ~37% of total global revenue
- Technology category contributes significantly in mature markets
- Africa represents untapped growth opportunity
- USCA shows balanced category performance

---

### Page 2: Time Series Analysis

**Screenshot:** `page2-time-series.png`

**Visualizations:**
1. **Sum of Sales Growth Over Time** (Line Chart)
   - Shows cumulative sales growth from 2021-2024
   - Clear upward trend indicating business growth
   - Steep growth acceleration from 2022 onwards

2. **Sum of Sales YoY% by Year** (Line Chart)
   - Year-over-year growth rate analysis
   - Peak growth of ~27% in 2023
   - Growth moderating to ~26% in 2024
   - Shows healthy sustained growth

3. **Monthly Sales and Profit Matrix** (Data Table)
   - Detailed breakdown by month and year
   - Shows both revenue and profit metrics
   - Enables identification of seasonal patterns
   - Conditional formatting highlights strong/weak performance

**Key Insights from Page 2:**
- Total sales grew from $2.26M (2021) to $4.3M (2024)
- June consistently shows strong performance across all years
- December is traditionally the strongest sales month
- Profit margins remain relatively stable (~10-12%)
- Year-over-year growth is positive but moderating

---

## Data Sources

### 1. Global Superstore Orders 2025.xlsx
**Structure:** Excel workbook with 2 worksheets
- **Orders Sheet:** 51,289 rows of transaction data
- **People Sheet:** Regional sales representatives

**Key Columns:**
- Order ID, Order Date, Ship Date
- Customer ID, Customer Name
- Country, Region, Market
- Product Category, Sub-Category, Product Name
- Sales, Quantity, Discount, Profit

### 2. Global Superstore Returns 2025.csv
**Structure:** CSV file with return information
- Order ID (links to Orders)
- Returned (Yes/No)
- Market information

### 3. Relationships Established
```
Orders (Order ID) ----< Returns (Order ID)     [Many-to-One]
Orders (Region)   ----< People (Region)        [Many-to-One]
```

---

## Technical Implementation

### Data Preparation (Power Query)

**1. Excel Data Transformation:**
- Changed year from 2016 to 2025 using DATE() function
- Converted date columns to proper Date format
- Verified numeric data types for Sales and Profit columns
- Split Order ID into Distribution Center and Order ID components

**2. CSV Data Cleaning:**
- Promoted first row to headers
- Validated data types
- Removed duplicate entries

**3. Data Quality Checks:**
- Postal Code: 81% null values (acceptable for global data)
- No duplicate records found
- All required fields populated
- Consistent data formats

### Data Modeling

**Relationships:**
- Orders ↔ Returns: Many-to-One via Order ID
- Orders ↔ People: Many-to-One via Region
- Cross-filter direction: Both (bidirectional)

**Calculated Measures:**
```DAX
Sum of Sales YoY% = 
IF(
    ISFILTERED('Orders'[Order Date]),
    ERROR("Time intelligence quick measures can only be grouped or filtered by the Power BI-provided date hierarchy or primary date column."),
    VAR __PREV_YEAR = 
        CALCULATE(
            SUM('Orders'[Sales]),
            DATEADD('Orders'[Order Date].[Date], -1, YEAR)
        )
    RETURN
        DIVIDE(SUM('Orders'[Sales]) - __PREV_YEAR, __PREV_YEAR)
)
```

### Visualization Techniques

**Chart Types Used:**
- Horizontal Bar Charts: Market comparison
- Clustered Column Charts: Category breakdown
- Stacked Column Charts: Composition analysis
- Line Charts: Time series trends
- Matrix Tables: Detailed data view

**Design Principles:**
- Color-coded by market/category for consistency
- Data labels for precise values
- Conditional formatting for performance highlighting
- Clear titles and legends
- Consistent formatting across pages

---

## Business Insights & Recommendations

### Market Performance
**Strengths:**
- Asia Pacific is the dominant market (37% of revenue)
- Europe shows strong, consistent performance (28% of revenue)
- Steady growth across all geographic regions

**Opportunities:**
- Africa is significantly underpenetrated (5% of revenue)
- LATAM shows growth potential with improving trends
- Consider market-specific strategies for expansion

### Product Category Analysis
**Technology:** 
- Highest revenue generator
- Strong margins
- Dominates in Asia Pacific and Europe

**Office Supplies:**
- Consistent performer across all markets
- Lower margins but high volume
- Stable revenue stream

**Furniture:**
- Variable performance by market
- Higher shipping costs impact margins
- Focus on high-end products

### Time-Based Patterns
**Seasonal Trends:**
- Q4 (November-December) shows peak sales
- June also performs strongly (mid-year push)
- January-February are slowest months

**Growth Trajectory:**
- Compound annual growth rate (CAGR): ~23%
- Growth is decelerating slightly but remains healthy
- 2024 on track to exceed $4.3M in sales

### Strategic Recommendations
1. **Market Expansion:** Invest in Africa and LATAM infrastructure
2. **Seasonal Optimization:** Increase inventory for Q4 rush
3. **Category Focus:** Expand technology offerings in growing markets
4. **Customer Retention:** Analyze return rates to improve satisfaction
5. **Profitability:** Focus on high-margin products and markets

---

## Power BI Features Demonstrated

### Data Transformation
- ✅ Power Query Editor for ETL
- ✅ Applied Steps tracking
- ✅ Column splitting and data type conversion
- ✅ Duplicate removal
- ✅ Header promotion

### Data Modeling
- ✅ Star schema implementation
- ✅ Relationship creation (many-to-one)
- ✅ Cross-filter configuration
- ✅ Date hierarchy creation

### DAX (Data Analysis Expressions)
- ✅ Quick Measures for YoY calculations
- ✅ Time intelligence functions
- ✅ CALCULATE and DIVIDE functions
- ✅ Error handling in measures

### Visualizations
- ✅ Multiple chart types
- ✅ Conditional formatting
- ✅ Data labels and tooltips
- ✅ Custom color schemes
- ✅ Interactive filtering

### Report Design
- ✅ Multi-page layouts
- ✅ Consistent branding
- ✅ Professional formatting
- ✅ Export to PDF capability

---

## Files in This Project

```
powerbi-global-superstore/
├── _Global_Superstore_Sales_Report.pbix  # Power BI Desktop file
├── page1-market-analysis.png              # Dashboard screenshot - Page 1
├── page2-time-series.png                  # Dashboard screenshot - Page 2
└── README.md                              # This file
```

---

## How to Use This Project

### Option 1: View Screenshots
Simply review the PNG images to see the final dashboards.

### Option 2: Open in Power BI Desktop
**Requirements:**
- Windows PC (Power BI Desktop not available on Mac)
- Power BI Desktop (free download from Microsoft)

**Steps:**
1. Download Power BI Desktop: https://powerbi.microsoft.com/desktop/
2. Open `_Global_Superstore_Sales_Report.pbix`
3. Explore interactive dashboards
4. Modify visualizations or add new ones
5. Refresh data if source files are updated

### Option 3: Replicate the Project
Follow the lab instructions (Power BI Lab Parts I & II) to:
1. Prepare data in Excel
2. Load data into Power BI
3. Transform data in Power Query
4. Create relationships
5. Build visualizations
6. Add calculated measures

---

## Key Metrics Summary

| Metric | 2021 | 2022 | 2023 | 2024 | Total |
|--------|------|------|------|------|-------|
| **Sales** | $2.26M | $2.68M | $3.41M | $4.30M | $12.64M |
| **Profit** | $249K | $307K | $407K | $504K | $1.47M |
| **Orders** | ~12,000 | ~13,000 | ~15,000 | ~11,000* | 51,289 |
| **Profit Margin** | 11.0% | 11.5% | 11.9% | 11.7% | 11.6% |

*2024 data may be partial year

---

## Learning Outcomes

This project demonstrates proficiency in:
- ✅ Business Intelligence fundamentals
- ✅ Data cleaning and preparation
- ✅ Relational data modeling
- ✅ DAX formula creation
- ✅ Interactive visualization design
- ✅ Business metrics analysis
- ✅ Professional report creation
- ✅ Data storytelling

---

## Real-World Applications

**Business Intelligence Skills:**
- Sales performance tracking
- Market analysis and comparison
- Trend identification
- KPI monitoring
- Executive reporting

**Industries Using These Skills:**
- Retail and e-commerce
- Financial services
- Healthcare analytics
- Supply chain management
- Marketing analytics

**Career Paths:**
- Business Intelligence Analyst
- Data Analyst
- Business Analyst
- Sales Analyst
- Operations Analyst

---

## Tools & Technologies

**Primary Tool:** Microsoft Power BI Desktop
- Industry-leading BI platform
- Used by Fortune 500 companies
- Free desktop version available
- Cloud sharing capabilities via Power BI Service

**Related Microsoft Tools:**
- Excel for data preparation
- Power Query for ETL
- DAX for calculations
- Power BI Service for sharing

**Alternative BI Tools:**
- Tableau (similar visualizations)
- Qlik Sense (associative analytics)
- Looker/Google Data Studio (web-based)
- Metabase (open-source)

---

## Future Enhancements

**Possible Additions:**
1. **Predictive Analytics:** Forecast future sales using trend analysis
2. **Customer Segmentation:** RFM analysis for customer value
3. **Geographic Maps:** Visual representation of global performance
4. **Drill-Through Pages:** Detailed product-level analysis
5. **Mobile Layout:** Optimize for phone/tablet viewing
6. **Bookmarks:** Save specific views for presentations
7. **What-If Parameters:** Scenario modeling for business planning
8. **R/Python Integration:** Advanced statistical analysis

---

## Author

**Mamadou Ba**  
Computer Science Student @ CUNY College of Staten Island  
Operations Analyst & AI Lead @ Apex Forum  
Fall 2025

**Skills Demonstrated:**
- Data Analysis & Visualization
- Business Intelligence
- Microsoft Power BI
- DAX Programming
- Data Storytelling

---

## Additional Resources

**Power BI Learning:**
- [Microsoft Learn - Power BI](https://docs.microsoft.com/learn/powerbi/)
- [Power BI Community](https://community.powerbi.com/)
- [DAX Guide](https://dax.guide/)

**Business Analytics:**
- [Harvard Business Review - Analytics](https://hbr.org/topic/analytics)
- [Tableau Learning Resources](https://www.tableau.com/learn)

**Data Visualization Best Practices:**
- Edward Tufte's principles
- Stephen Few's dashboard design
- Cole Nussbaumer Knaflic's "Storytelling with Data"

---

**Project Status:** ✅ Complete  
**Last Updated:** December 2025  
**Dashboard Pages:** 2  
**Total Visualizations:** 7  
**Data Points:** 51,289 orders  
**Time Period:** 2021-2024 (4 years)

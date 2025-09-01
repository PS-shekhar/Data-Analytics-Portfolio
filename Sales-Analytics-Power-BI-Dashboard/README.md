**Sales & Profitability Intelligence Dashboard**

**Business Problem**

This project simulates a real-world business intelligence scenario for an e-commerce or retail company. The primary goal was to analyze a complex dataset to answer critical business questions related to:

**Seller performance
Product profitability
Customer behavior**

The final output is a 4-page interactive Power BI dashboard, designed for executive-level stakeholders to support data-driven decision-making.

**Tools Used**

**Power BI** - Data modeling, DAX calculations, interactive dashboards
**Microsoft Excel** - Primary data source
**Power Query** - ETL (Extract, Transform, Load) processes

**Dashboard Walkthrough & Key Insights**

**Page 1: Seller Performance Overview**

**Objective**: Provide a high-level snapshot of seller performance.
**Visuals**: KPIs for Total Revenue ($87.95K), Total Profit ($43.21K), and Total Sales (3K units). Stacked bar charts show seller-wise units sold by product.
**Key Insight**: Identified top-performing sellers like Uncle Joe's Prep Shop with 951 units sold.

**Page 2: Seller Profitability & Trends**

**Objective**: Analyze profitability and performance beyond just sales volume.
**DAX Implementation**: Custom "Seller Profit Tiers" (High, Mid, Low) and "Seller Tiers" (Top, Mid, Low) using SWITCH(TRUE()) and ISINSCOPE().
**Key Insight**: Sellers with high sales volume are not always the most profitable, highlighting areas for margin optimization.

**Page 3: Product Analysis & Profit Margins**

**Objective**: Identify most and least profitable products.
**DAX Implementation**: Calculated Profit Margin % using:

Profit Margin % = DIVIDE(Products[Price] - Products[Production Cost], Products[Price]) * 100

**Key Insight:**

High margin products: Waterproof Matches (64%), N95 Mask (63%), Weatherproof Jacket (62%)
Low margin product: Duct Tape (22%) - indicates pricing/sourcing issues

**Page 4: Buyer & Customer Segmentation**

**Objective**: Understand customer base and purchasing patterns.
**Analysis**: Segmented buyers by state and age groups using a SWITCH(TRUE()) DAX formula.
**Key Insigh**t: Revealed key demographics and regional hotspots for targeted marketing campaigns.

**Key DAX Formulas**

**Total Profit**
Total Profit =
SUMX (
    'Sales',
    (RELATED(Products[Price]) - RELATED(Products[Production Cost]))
    * Sales[Units Sold]
)

**Seller Tier**
Seller Tier =
IF (
    ISINSCOPE(Sales[Seller]),
    SWITCH (
        TRUE(),
        [Total Unit Sold] >= 900, "Top Tier",
        [Total Unit Sold] >= 700, "Mid Tier",
        "Low Tier"
    )
)

**Profit Margin %**
Profit Margin % =
DIVIDE (
    Products[Price] - Products[Production Cost],
    Products[Price]
) * 100

**Deliverables**

4-page Power BI Dashboard (Sellers, Profitability, Products, Buyers)
Interactive filters for Seller, Product, Age Group, State
Executive-ready KPI cards, charts, and segmentation views

# AtliQ Inventory Management Dashboard  
> A dashboard helps warehouse managers make smart inventory decisions to optimize stock, cut costs, and improve cash flow.

## Table of Contents
- [1. Project Background](#1-project-background)
- [2. About the Dataset](#2-about-the-dataset)
- [3. Analytical Framework: Why ABC Analysis?](#3-analytical-framework-why-abc-analysis)
- [4. Exploratory Data Analysis: Key Findings](#4-exploratory-data-analysis-key-findings)
  - [4.1 Revenue Concentration: A Small Set of SKUs Drives Profit](#41-revenue-concentration-a-small-set-of-skus-drives-profit)
  - [4.2 Inventory Turnover: Most Products Move Slowly](#42-inventory-turnover-most-products-move-slowly)
- [5. Solution Design: Tableau Dashboard for Action](#5-solution-design-tableau-dashboard-for-action)
  - [5.1 Core Objective](#51-core-objective)
  - [5.2 “Good” and “Bad” Product Filters](#52-good-and-bad-product-filters)
  - [5.3 SKU-Level Performance Drill-Down](#53-sku-level-performance-drill-down)
- [6. Conclusion](#6-conclusion)

## 1. Project Background
Inventory inefficiency is one of the most common challenges in retail operations. Today, many store and warehouse managers still rely heavily on personal experience when deciding **what to reorder, how much to stock, and which products to prioritize**. While experience is valuable, this approach often leads to overstocking items. These issues directly affect **revenue, cash flow by** rising warehousing costs. 

To address this problem, this project introduces a **Tableau inventory management dashboard** built on **ABC analysis**, enabling managers to make **data-driven inventory decisions** instead of relying on intuition alone. Here is a preview....

<p align="center">
  <img src="https://github.com/user-attachments/assets/5c61ac44-7514-4365-865b-ff2b2be47c22" alt="Preview" width="980"/>
</p>

## 2. About the Dataset
The analysis draws from operational data supplied by an **AtliQ IT solutions client**. The dataset contains 34,222 rows covering 2020 to 2021, featuring key performance indicators like **historical sales, inventory levels, turnover metrics, and safety stock details**, which make it suitable for both performance analysis and operational decision support.

## 3. Analytical Framework: Why ABC Analysis?
- The dashboard employs ABC analysis, an inventory optimization technique rooted in the Pareto Principle (80/20 rule). This method enables businesses to classify inventory into A items (high impact), B items (moderate impact), and C items (low impact), so as to better allocate their resource by prioritizing items.
- In this project, the procedure is **extended by** applying it independently across **three KPIs, revenue, turnover ratio, and safety stock requirement** for a multi-dimensional perspective.

> In case you care about the maths, the process begins by computing the annual usage value $v_i = q_i \times c_i$ for each SKU $i$, where $q_i$ is units sold per year and $c_i$ is cost per unit. SKUs are then sorted in descending order of $v_i$, and the cumulative value $V_k = \sum_{i=1}^{k} v_i$ is calculated along with the cumulative percentage $p_k = \frac{V_k}{V_n} \times 100$, where $n$ is the total number of SKUs. Categories are assigned using thresholds: A for $p_k \leq 80\%$, B for $80\% < p_k \leq 95\%$, and C for $p_k > 95\%$. For more details, visit [here](https://en.wikipedia.org/wiki/ABC_analysis).

## 4. Exploratory Data Analysis: Key Findings

### 4.1 Revenue Concentration: A Small Set of SKUs Drives Profit

- The data shows a clear imbalance: just **19% of SKUs** generate **83%** of total revenue. These **A-category** products are the true profit drivers.
- At the same time, nearly **70% of SKUs** generate less than **10%** of revenue. These **C-category** items add little value and increase the risk of overstocking and tied-up cash.
- This is not unusual. [Research from MIT Sloan School of Management](https://www.researchgate.net/publication/227361691_Goodbye_Pareto_Principle_Hello_Long_Tail_The_Effect_of_Search_Costs_on_the_Concentration_of_Product_Sales?referrer=grok.com) confirms that traditional retail typically follows this pattern, where around **80% of sales** come from **20% of products** (Brynjolfsson, Hu, & Simester, 2011).
- Leading retailers such as Amazon manage this by protecting best sellers—keeping higher stock and safety levels for **A-items** while strictly limiting slow movers. Reducing stock and order frequency for **C-items** lowers excess inventory, improves cash flow, and frees up warehouse space.

<p align="center">
  <img src="https://github.com/user-attachments/assets/da7f584a-1e9d-4dc4-915e-312916371051" alt="ABC Analysis Pareto Chart for Revenue" width="380"/>
</p>

### 4.2 Inventory Turnover: Most Products Move Slowly

- Revenue alone does not show efficiency. A low-price item like **a sticker** can still be valuable if it sells quickly. The inventory turnover ratio reveals how well stock is converted into cash.
- The analysis shows that about **20% of SKUs** turn over quickly, using inventory efficiently and supporting healthy cash flow.
- In contrast, nearly **three-quarters of SKUs** move very slowly, sitting in the warehouse and locking up capital.
- This pattern is well known in retail operations. [Research](https://books.google.com.hk/books/about/Inventory_Management_and_Production_Plan.html?id=GI5jQgAACAAJ&redir_esc=y) shows that most SKUs sell slowly, while a small group drives most inventory movement (Silver, Pyke, & Peterson, 1998).
- Successful retailers like Zara act on this insight: they replenish fast sellers frequently and keep minimal stock of slow movers. Applying the same approach—frequent reordering for high-turnover items and tight controls, discounts, or clearance for low-turnover items—reduces excess inventory and improves warehouse efficiency.

<p align="center">
  <img src="https://github.com/user-attachments/assets/8f986f02-2a20-4d16-a0f8-714902564a9d" alt="ABC Analysis Pareto Chart for Turnover Ratio" width="380"/>
</p>

## 5. Solution Design: Tableau Dashboard for Action

### 5.1 Core Objective
The primary objective of the dashboard is to:

- Increase the share of A-class inventory
- Reduce capital tied up in C-class inventory
- Enable fast, confident daily decision-making for managers

The design emphasizes clarity, prioritization, and minimal cognitive load.

### 5.2 “Good” and “Bad” Product Filters
A central feature of the dashboard is the Good / Bad SKU filter, which instantly segments products based on performance. These filters help managers immediately focus on what to protect and what to fix.

<p align="center">
  <img src="https://github.com/user-attachments/assets/e40b599d-4f7d-4f9d-a3d0-c3e754d31f8d" alt="Dashboard Screenshot: “Good” and “Bad” SKU Filter in Action" width="980"/>
</p>

| Filter | What It Shows | Why It Matters | Key Metrics to Watch | Manager Questions Answered |
|--------|---------------|----------------|-----------------------|-----------------------------|
| **Bad** | Only the worst items — ranked as C-category in revenue and turnover ratio. These hurt the business most and need quick fixes. | Helps spot low-performing stock that ties up money and space. | - Total warehouse inventory value tied up in bad products<br>- Total number of affected SKUs | - How big is the cleanup job?<br>- How much money can we free up from slow-selling items? |
| **Good** | Only the best products — those performing well in revenue, turnover ratio, and safety stock. These are essential to success. | Helps focus on strong items that drive profits and cash flow. | - Median safety stock level<br>- Average inventory turnover ratio | - How much stock should we keep for top items?<br>- How fast are our best items selling? |

### 5.3 SKU-Level Performance Drill-Down
The second level of filtering is by individual SKU, color-coded for quick understanding. Managers can quickly evaluate individual products by drilling down to the SKU level in the dashboard. Products are color-coded for instant recognition: **blue** for A-class (high performers), **yellow** for B-class (moderate), and **red** for C-class (low performers). Managers no longer need to dig through spreadsheets. The dashboard lets them drill down quickly and see details in this order:

<p align="center">
  <img src="https://github.com/user-attachments/assets/f7098063-1c3c-499e-ae94-a7a376f5b320" alt="Dashboard Screenshot: SKU-Level Performance Filter and Details" width="980"/>
</p>

| Step | Action on Dashboard                          | What to Look For                                      | Why It Helps Managers                                                                 |
|------|----------------------------------------------|-------------------------------------------------------|---------------------------------------------------------------------------------------|
| 1    | Select an individual SKU (click the SKU code or product name) | The view updates to show details for that single product. Color code appears: blue (A-class), yellow (B-class), red (C-class) | Quickly identifies if the product is a high, moderate, or low performer.             |
| 2    | Check **Turnover Days** first                | Number of days to sell current stock (low = fast-selling; high = slow-moving) | Spots slow-moving items early that tie up warehouse space and capital.               |
| 3    | Review **Reorder Point** next                | Stock level at which to place a new order             | Ensures timely reordering — avoids stockouts on good sellers or overstock on poor ones. |
| 4    | Examine **Stock Levels and ABC Classification** last | Current stock quantity + ABC ranks across revenue, turnover, and safety stock | Gives a complete picture: strong across all measures, mixed, or consistently weak.   |

## 6. Conclusion
By integrating ABC analysis, multi-KPI evaluation, and manager-centric dashboard design, this project bridges the gap between data and execution. The Tableau dashboard enables inventory managers to transition from intuition-based judgment to evidence-based inventory control.

The outcome is a more focused inventory portfolio, improved cash flow, reduced warehousing costs, and stronger alignment between operational decisions and business performance.

In short, the dashboard transforms inventory data into a clear story—one that tells managers where value is created, where it is lost, and what actions matter most.

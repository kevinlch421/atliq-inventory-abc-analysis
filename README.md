# AtliQ Inventory Control Dashboard – Built on ABC Analysis

- [Project Background](#project-background)
- [About the Dataset](#about-the-dataset)
- [Analytical Framework: Why ABC Analysis?](#analytical-framework-why-abc-analysis)
- [Data-Driven Insights](#data-driven-insights)
  - [Revenue Analysis](#revenue-analysis-where-the-business-really-makes-money)
  - [Turnover Ratio](#turnover-ratio-how-efficiently-stock-is-used)
- [Dashboard Design & Practical Application](#dashboard-design--practical-application)
  - [Core Objective](#core-objective)
  - [“Good” and “Bad” Product Filters](#good-and-bad-product-filters)
  - [SKU-Level Performance Analysis](#sku-level-performance-analysis)
- [Conclusion](#conclusion)

## Project Background
Inventory inefficiency is one of the most common challenges in retail operations. Today, many store and warehouse managers still rely heavily on personal experience when deciding **what to reorder, how much to stock, and which products to prioritize**. While experience is valuable, this approach often leads to overstocking items. These issues directly affect **revenue, cash flow by** rising warehousing costs. 

To address this problem, this project introduces a **Tableau inventory management dashboard** built on **ABC analysis**, enabling managers to make **data-driven inventory decisions** instead of relying on intuition alone.

## About the Dataset
The analysis draws from operational data supplied by an **AtliQ IT solutions client**. The dataset contains 34,222 rows covering 2020 to 2021, featuring key performance indicators like **historical sales, inventory levels, turnover metrics, and safety stock details**, which make it suitable for both performance analysis and operational decision support.

## Analytical Framework: Why ABC Analysis?
- The dashboard employs ABC analysis, an inventory optimization technique rooted in the Pareto Principle (80/20 rule). This method enables businesses to classify inventory into A items (high impact), B items (moderate impact), and C items (low impact), so as to better allocate their resource by prioritizing items.
- In this project, the procedure is **extended by** applying it independently across **three KPIs, revenue, turnover ratio, and safety stock requirement** for a multi-dimensional perspective.

> In case you care about the maths, the process begins by computing the annual usage value $v_i = q_i \times c_i$ for each SKU $i$, where $q_i$ is units sold per year and $c_i$ is cost per unit. SKUs are then sorted in descending order of $v_i$, and the cumulative value $V_k = \sum_{i=1}^{k} v_i$ is calculated along with the cumulative percentage $p_k = \frac{V_k}{V_n} \times 100$, where $n$ is the total number of SKUs. Categories are assigned using thresholds: A for $p_k \leq 80\%$, B for $80\% < p_k \leq 95\%$, and C for $p_k > 95\%$. For more details, visit [here](https://en.wikipedia.org/wiki/ABC_analysis).

## The Problem: EDA insights

### Revenue Analysis: Only 19% of Inventory Really Makes Money

- The data shows a clear imbalance: just **19% of SKUs** generate **83%** of total revenue. These **A-category** products are the true profit drivers.
- At the same time, nearly **70% of SKUs** generate less than **10%** of revenue. These **C-category** items add little value and increase the risk of overstocking and tied-up cash.
- This is not unusual. [Research from MIT Sloan School of Management](https://www.researchgate.net/publication/227361691_Goodbye_Pareto_Principle_Hello_Long_Tail_The_Effect_of_Search_Costs_on_the_Concentration_of_Product_Sales?referrer=grok.com) confirms that traditional retail typically follows this pattern, where around **80% of sales** come from **20% of products** (Brynjolfsson, Hu, & Simester, 2011).
- Leading retailers such as Amazon manage this by protecting best sellers—keeping higher stock and safety levels for **A-items** while strictly limiting slow movers. Reducing stock and order frequency for **C-items** lowers excess inventory, improves cash flow, and frees up warehouse space.

<img width="539" height="549" alt="download" src="https://github.com/user-attachments/assets/da7f584a-1e9d-4dc4-915e-312916371051" />

### Turnover Ratio: Only 20% of Inventory Moves Efficiently

- Revenue alone does not show efficiency. A low-price item like **a sticker** can still be valuable if it sells quickly. The inventory turnover ratio reveals how well stock is converted into cash.
- The analysis shows that about **20% of SKUs** turn over quickly, using inventory efficiently and supporting healthy cash flow.
- In contrast, nearly **three-quarters of SKUs** move very slowly, sitting in the warehouse and locking up capital.
- This pattern is well known in retail operations. [Research](https://books.google.com.hk/books/about/Inventory_Management_and_Production_Plan.html?id=GI5jQgAACAAJ&redir_esc=y) shows that most SKUs sell slowly, while a small group drives most inventory movement (Silver, Pyke, & Peterson, 1998).
- Successful retailers like Zara act on this insight: they replenish fast sellers frequently and keep minimal stock of slow movers. Applying the same approach—frequent reordering for high-turnover items and tight controls, discounts, or clearance for low-turnover items—reduces excess inventory and improves warehouse efficiency.

<img width="539" height="549" alt="download-2" src="https://github.com/user-attachments/assets/8f986f02-2a20-4d16-a0f8-714902564a9d" />

## The Solution: Dashboard Design & Practical Application

### Core Objective
The main goal of the dashboard is to increase the share of high-performing (A-class) inventory while reducing low-performing (C-class) inventory. It provides managers with quick, clear insights for daily decisions.

### “Good” and “Bad” Product Filters

![“Good” and “Bad” SKU Filter](https://github.com/user-attachments/assets/e40b599d-4f7d-4f9d-a3d0-c3e754d31f8d)

A key feature is the Good/Bad filter buttons based on product categories.

| Filter | What It Shows | Why It Matters | Key Metrics to Watch | Manager Questions Answered |
|--------|---------------|----------------|-----------------------|-----------------------------|
| **Bad** | Only the worst items — ranked as C-category in revenue and turnover ratio. These hurt the business most and need quick fixes. | Helps spot low-performing stock that ties up money and space. | - Total warehouse inventory value tied up in bad products<br>- Total number of affected SKUs | - How big is the cleanup job?<br>- How much money can we free up from slow-selling items? |
| **Good** | Only the best products — those performing well in revenue, turnover ratio, and safety stock. These are essential to success. | Helps focus on strong items that drive profits and cash flow. | - Median safety stock level<br>- Average inventory turnover ratio | - How much stock should we keep for top items?<br>- How fast are our best items selling? |

These filters help managers protect top performers, fix weak products quickly, and keep the warehouse focused on what really drives business results.

### SKU-Level Performance Analysis
The second level of filtering is by individual SKU, color-coded for quick understanding. Managers can quickly evaluate individual products by drilling down to the SKU level in the dashboard. Products are color-coded for instant recognition: **blue** for A-class (high performers), **yellow** for B-class (moderate), and **red** for C-class (low performers). Managers no longer need to dig through spreadsheets. The dashboard lets them drill down quickly and see details in this order:

![SKU-Level Performance Filter](https://github.com/user-attachments/assets/f7098063-1c3c-499e-ae94-a7a376f5b320)

| Step | Action on Dashboard                          | What to Look For                                      | Why It Helps Managers                                                                 |
|------|----------------------------------------------|-------------------------------------------------------|---------------------------------------------------------------------------------------|
| 1    | Select an individual SKU (click the SKU code or product name) | The view updates to show details for that single product. Color code appears: blue (A-class), yellow (B-class), red (C-class) | Quickly identifies if the product is a high, moderate, or low performer.             |
| 2    | Check **Turnover Days** first                | Number of days to sell current stock (low = fast-selling; high = slow-moving) | Spots slow-moving items early that tie up warehouse space and capital.               |
| 3    | Review **Reorder Point** next                | Stock level at which to place a new order             | Ensures timely reordering — avoids stockouts on good sellers or overstock on poor ones. |
| 4    | Examine **Stock Levels and ABC Classification** last | Current stock quantity + ABC ranks across revenue, turnover, and safety stock | Gives a complete picture: strong across all measures, mixed, or consistently weak.   |

Following these steps provides a fast, logical flow — from sales speed to reorder timing to overall performance — making daily inventory decisions quicker and more accurate without searching spreadsheets.
## Conclusion
By combining ABC analysis, clear visual design, and manager-focused KPIs, this Tableau dashboard bridges the gap between data and action. It empowers store and inventory managers to move from intuition-based decisions to evidence-based inventory management, delivering measurable financial and operational improvements across the business.

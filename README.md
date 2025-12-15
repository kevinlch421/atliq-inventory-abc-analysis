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

## Data-Driven Insights

### Revenue Analysis: Where the Business Really Makes Money
- The analysis shows that 19% of SKUs make 83% of total revenue. We call these A-category items. They bring in most of the profits.
- On the other hand, almost 70% of SKUs make less than 10% of revenue. These C-category items provide little financial return and can cause overstocking.
- This pattern is common in traditional retail. A study by MIT Sloan School of Management researchers found that many markets have long been dominated by a few top products, where about 80% of sales often come from 20% of products (Brynjolfsson, Hu, and Simester, 2011).
- We recommend following the example of Amazon in warehouse management: keep plenty of stock and extra safety levels for A-category items to avoid running out of best sellers. For C-category items, cut down on stock levels and order less often. Use tight rules on slow sellers to prevent extra stock and price cuts. These steps will improve cash flow and make better use of warehouse space.

### Turnover Ratio: How Efficiently Stock Is Used
- Revenue alone does not tell the full story of how fast products sell. For example, a cheap item like a sticker may make less money than a bag because its price is low. But if it sells fast, it can still be a good product.
- The analysis shows that nearly 20% of SKUs have high turnover — they sell quickly and use inventory efficiently.
- On the other hand, 74% of SKUs sell very slowly. These items stay in the warehouse a long time and hold up money that could be used elsewhere.
- This is normal in retail. Studies in operations management say most items sell slowly, while only a few move fast and make up most of the turnover (Silver, Pyke, & Peterson, *Inventory Management and Production Planning*, 1998).
- We suggest copying fast-fashion stores like Zara. They order often for fast sellers to avoid running out and keep very little stock of slow sellers. For high-turnover (A-category) items, order more often. For low-turnover (C-category) items, keep less stock, order less, and use sales or discounts to clear old items. These changes will reduce excess inventory and improve warehouse efficiency.

## Dashboard Design & Practical Application

### Core Objective
The main goal of the dashboard is to increase the share of high-performing (A-class) inventory while reducing low-performing (C-class) inventory. It provides managers with quick, clear insights for daily decisions.

### “Good” and “Bad” Product Filters
A key feature is the Good/Bad filter buttons based on product categories.

| Filter | What It Shows | Why It Matters | Key Metrics to Watch | Manager Questions Answered |
|--------|---------------|----------------|-----------------------|-----------------------------|
| **Bad** | Only the worst items — ranked as C-category in revenue and turnover ratio. These hurt the business most and need quick fixes. | Helps spot low-performing stock that ties up money and space. | - Total warehouse inventory value tied up in bad products<br>- Total number of affected SKUs | - How big is the cleanup job?<br>- How much money can we free up from slow-selling items? |
| **Good** | Only the best products — those performing well in revenue, turnover ratio, and safety stock. These are essential to success. | Helps focus on strong items that drive profits and cash flow. | - Median safety stock level<br>- Average inventory turnover ratio | - How much stock should we keep for top items?<br>- How fast are our best items selling? |

These filters help managers protect top performers, fix weak products quickly, and keep the warehouse focused on what really drives business results.

### SKU-Level Performance Analysis
The second level of filtering is by individual SKU, color-coded for quick understanding. Managers can quickly evaluate individual products by drilling down to the SKU level in the dashboard. Products are color-coded for instant recognition: **blue** for A-class (high performers), **yellow** for B-class (moderate), and **red** for C-class (low performers). Managers no longer need to dig through spreadsheets. The dashboard lets them drill down quickly and see details in this order:


| Step | Action on Dashboard                          | What to Look For                                      | Why It Helps Managers                                                                 |
|------|----------------------------------------------|-------------------------------------------------------|---------------------------------------------------------------------------------------|
| 1    | Select an individual SKU (click the SKU code or product name) | The view updates to show details for that single product. Color code appears: blue (A-class), yellow (B-class), red (C-class) | Quickly identifies if the product is a high, moderate, or low performer.             |
| 2    | Check **Turnover Days** first                | Number of days to sell current stock (low = fast-selling; high = slow-moving) | Spots slow-moving items early that tie up warehouse space and capital.               |
| 3    | Review **Reorder Point** next                | Stock level at which to place a new order             | Ensures timely reordering — avoids stockouts on good sellers or overstock on poor ones. |
| 4    | Examine **Stock Levels and ABC Classification** last | Current stock quantity + ABC ranks across revenue, turnover, and safety stock | Gives a complete picture: strong across all measures, mixed, or consistently weak.   |

Following these steps provides a fast, logical flow — from sales speed to reorder timing to overall performance — making daily inventory decisions quicker and more accurate without searching spreadsheets.
## Conclusion
By combining ABC analysis, clear visual design, and manager-focused KPIs, this Tableau dashboard bridges the gap between data and action. It empowers store and inventory managers to move from intuition-based decisions to evidence-based inventory management, delivering measurable financial and operational improvements across the business.

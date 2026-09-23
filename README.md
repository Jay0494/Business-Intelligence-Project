# 2025 Sales & Profitability Investigation

## End-to-End Data Analytics & Business Intelligence Project

An end-to-end **sales and profitability analytics project** developed in Power BI to investigate why **€404.1K in 2025 net sales generated €85.61K in contribution margin**.

The project follows a complete professional analytics workflow:

**Business Understanding → Data Understanding → Data Preparation → Data Modelling → Exploratory Analysis → Diagnostic Analysis → DAX & KPI Development → Visualisation → Insights → Recommendations**

The objective was to move beyond revenue reporting and understand **where economic value was being created, where it was being lost, and what management should investigate next**.

---

## Table of Contents

* [1. Business Understanding](#1-business-understanding)

  * [Business Problem](#business-problem)
  * [Business Questions](#business-questions)
  * [Analytical Objectives](#analytical-objectives)
* [2. Data Understanding](#2-data-understanding)

  * [Data Sources](#data-sources)
  * [Data Dictionary](#data-dictionary)
  * [Key Business Metrics](#key-business-metrics)
* [3. Data Preparation](#3-data-preparation)

  * [Data Profiling](#data-profiling)
  * [Data Quality Assessment](#data-quality-assessment)
  * [Data Cleaning](#data-cleaning)
  * [Data Transformation](#data-transformation)
* [4. Data Modelling](#4-data-modelling)

  * [Modelling Approach](#modelling-approach)
  * [Relationships](#relationships)
  * [Date Dimension](#date-dimension)
* [5. Exploratory Data Analysis](#5-exploratory-data-analysis)

  * [Overall Performance](#overall-performance)
  * [Cost Structure](#cost-structure)
  * [Category Profitability](#category-profitability)
  * [Product Profitability](#product-profitability)
  * [Promotion Analysis](#promotion-analysis)
  * [Return Analysis](#return-analysis)
  * [Fulfilment Analysis](#fulfilment-analysis)
  * [Inventory and Stockouts](#inventory-and-stockouts)
  * [Customer Profitability](#customer-profitability)
* [6. Diagnostic and Root-Cause Analysis](#6-diagnostic-and-root-cause-analysis)

  * [Contribution Leakage](#contribution-leakage)
  * [Product Economics](#product-economics)
  * [Promotion Economics](#promotion-economics)
  * [Return Drivers](#return-drivers)
  * [Fulfilment and Shipping Economics](#fulfilment-and-shipping-economics)
  * [Stockout Opportunity](#stockout-opportunity)
  * [Customer Economics](#customer-economics)
* [7. DAX and KPI Development](#7-dax-and-kpi-development)

  * [Revenue Measures](#revenue-measures)
  * [Contribution Measures](#contribution-measures)
  * [Time Intelligence](#time-intelligence)
  * [Commercial Measures](#commercial-measures)
  * [Operational Measures](#operational-measures)
* [8. Power BI Visualisation](#8-power-bi-visualisation)

  * [Visualisation Approach](#visualisation-approach)
  * [Dashboard Interactivity](#dashboard-interactivity)
* [9. Business Insights](#9-business-insights)

  * [Key Findings](#key-findings)
* [10. Recommendations](#10-recommendations)

  * [Product](#product)
  * [Promotions](#promotions)
  * [Returns](#returns)
  * [Inventory](#inventory)
  * [Fulfilment](#fulfilment)
  * [Shipping](#shipping)
  * [Customers](#customers)
* [11. Evidence vs Hypothesis](#11-evidence-vs-hypothesis)

  * [Demonstrated Evidence](#demonstrated-evidence)
  * [Potential Explanations](#potential-explanations)
  * [Further Testing Required](#further-testing-required)
* [12. Technical Stack](#12-technical-stack)
* [13. Repository Structure](#13-repository-structure)
* [14. Interactive Dashboard](#14-interactive-dashboard)
* [15. Project Outcome](#15-project-outcome)
* [16. Skills Demonstrated](#16-skills-demonstrated)
* [17. Author](#17-author)

---

# 1. Business Understanding

## Business Problem

The business generated:

* **€404.1K Net Sales**
* **€85.61K Contribution Margin**
* **21.19% Contribution Margin**

The investigation was designed to answer:

> **Why are €404.1K in sales producing only €85.61K in contribution, where is value being lost, and what evidence should guide management decisions?**

The analysis therefore focused on the economics behind revenue rather than revenue alone.

---

## Business Questions

### Product profitability

* Which categories generate the most contribution?
* Which categories generate significant revenue but limited contribution?
* Which products are loss-making?
* What factors may explain weak product economics?

### Promotions

* Which campaigns generate stronger contribution?
* How does discount depth relate to contribution?
* Are promotions generating sufficient incremental demand to justify margin sacrifice?

### Returns

* Which categories and products generate the greatest return losses?
* What return reasons dominate?
* Are return patterns different across categories and customer segments?

### Fulfilment

* Which fulfilment locations generate stronger contribution?
* How does cost-to-serve vary?
* How much shipping cost is recovered?

### Inventory

* Where are stockouts occurring?
* What is the estimated sales opportunity associated with unfulfilled demand?
* Which stockouts matter most when contribution economics are considered?

### Customers

* Which customer segments generate stronger contribution?
* Which segments are more discount-dependent?
* How do return losses affect customer economics?

---

## Analytical Objectives

The investigation aimed to:

1. Quantify overall contribution performance.
2. Identify major cost drivers.
3. Identify areas of contribution leakage.
4. Analyse product and category economics.
5. Evaluate promotion performance.
6. Investigate return losses.
7. Compare fulfilment economics.
8. Quantify stockout opportunity.
9. Analyse customer profitability.
10. Translate findings into evidence-based management recommendations.

---

# 2. Data Understanding

## Data Sources

The analysis used the supplied **2025 transactional dataset**, supporting business fields and the accompanying data dictionary.

The analytical structure supported analysis across:

* Orders
* Products
* Categories
* Customers
* Promotions
* Fulfilment
* Returns
* Shipping
* Inventory
* Dates

---

## Data Dictionary

The data dictionary was used to establish the business definitions of the key measures before developing the analytical model.

Important definitions included:

* Contribution Revenue
* Contribution Margin
* Product Cost
* Variable Costs
* Return Loss
* Lost Sales Value
* Applied Discount %
* Return Recovery %

This step ensured that the calculations reflected the intended business definitions rather than assumptions made from column names alone.

---

## Key Business Metrics

### Contribution Revenue

```text
Contribution Revenue
= Net Sales + Shipping Revenue
```

### Contribution Margin

```text
Contribution Margin
= Contribution Revenue
  - Product Cost
  - Variable Costs
```

### Contribution Margin %

```text
Contribution Margin %
= Contribution Margin / Contribution Revenue
```

### Shipping Recovery %

```text
Shipping Recovery %
= Shipping Revenue / Outbound Shipping Cost
```

### Important accounting distinction

Contribution Margin already incorporates the defined variable costs.

Therefore, the following should **not be deducted again** when reconciling contribution:

* Product Cost
* Outbound Shipping
* Return Shipping
* Fulfilment
* Payment Fees
* Allocated Marketing
* Return Processing

They are explanatory components of the existing contribution calculation.

---

# 3. Data Preparation

## Data Profiling

Before analysis, the dataset was profiled to understand:

* Dataset structure
* Fields and attributes
* Data types
* Missing values
* Duplicate records
* Identifiers
* Categorical values
* Numerical distributions
* Date ranges

---

## Data Quality Assessment

Quality checks focused on:

* Duplicate transactions
* Missing values
* Identifier consistency
* Date consistency
* Relationship integrity
* Unexpected values
* Aggregation behaviour

This was particularly important because profitability analysis can be distorted by duplicate records or incorrect relationships.

---

## Data Cleaning

The preparation process included:

* Investigating missing values
* Investigating duplicate records
* Validating identifiers
* Standardising analytical fields
* Reviewing categorical values
* Checking numerical fields
* Validating relationships

---

## Data Transformation

Power Query was used to prepare the dataset for analysis.

Transformation activities included:

* Data type management
* Field preparation
* Data standardisation
* Analytical field preparation
* Date preparation
* Relationship preparation

---

# 4. Data Modelling

## Modelling Approach

The Power BI model used a dimensional modelling approach to support analysis across:

* Date
* Product
* Category
* Customer
* Promotion
* Fulfilment
* Returns

The model was designed to support reusable DAX measures and consistent filtering across the analytical dimensions.

---

## Relationships

Relationships were configured to allow analytical filtering across the relevant business dimensions.

The repository should include the **actual Power BI model screenshot** to document the physical schema rather than relying on an assumed table structure.

---

## Date Dimension

A dedicated date dimension supported:

* Year
* Month
* Period filtering
* Time-series analysis
* Previous-year comparison
* YoY calculations

---

# 5. Exploratory Data Analysis

The exploratory phase established the overall performance profile before moving into diagnostic investigation.

---

## Overall Performance

| KPI                   |        2025 |
| --------------------- | ----------: |
| Net Sales             | **€404.1K** |
| Contribution Margin   | **€85.61K** |
| Contribution Margin % |  **21.19%** |
| Orders                |     **~4K** |
| Average Order Value   | **€109.90** |

### Year-on-Year Performance

| Metric              |         YoY |
| ------------------- | ----------: |
| Net Sales           |  **+71.0%** |
| Orders              |  **+67.4%** |
| Contribution Margin | **+103.7%** |
| AOV                 |   **+2.1%** |

The business therefore experienced substantial growth in both sales and contribution.

The next stage was to investigate the composition and quality of that contribution.

---

## Cost Structure

| Cost Component          |          2025 |
| ----------------------- | ------------: |
| Product Cost            |      €241.85K |
| Outbound Shipping       |       €36.43K |
| Payment Fees            |       €16.92K |
| Allocated Marketing     |       €15.96K |
| Fulfilment              |       €10.78K |
| Return Shipping         |        €4.72K |
| Return Processing       |        €2.25K |
| **Total Variable Cost** | **~€328.92K** |

Product cost represented approximately **73.5% of total variable cost**.

This made product economics a major area of the profitability investigation.

---

## Category Profitability

### Electronics

| Metric              |       Result |
| ------------------- | -----------: |
| Sales               | **€138.61K** |
| Contribution        |   **€4.76K** |
| Contribution Margin |    **3.43%** |

Electronics generated substantial revenue but comparatively little contribution.

Beauty, Fashion and Sports & Outdoors collectively generated approximately **79% of total contribution**.

This demonstrated that revenue scale does not necessarily correspond to contribution performance.

---

## Product Profitability

Category analysis was drilled down to product level to identify individual sources of contribution leakage.

### Tech Smart Home Plus

| Metric              |     Result |
| ------------------- | ---------: |
| Sales               |    €10.74K |
| Contribution        |  **-€438** |
| Contribution Margin | **-4.08%** |
| Discount            |      8.57% |

This product generated meaningful sales while producing negative contribution.

Potential drivers requiring investigation include:

* Product cost
* Pricing
* Discounts
* Returns
* Fulfilment costs
* Other variable costs

---

## Promotion Analysis

Promotion performance was evaluated using sales, contribution, margin, discount and return metrics.

| Promotion         | Contribution Margin |
| ----------------- | ------------------: |
| Bundle & Save     |          **28.84%** |
| Loyalty 10%       |          **27.68%** |
| Free Shipping     |          **22.82%** |
| Welcome 15%       |          **12.07%** |
| Holiday Event 20% |           **8.50%** |
| Weekend Flash 25% |           **2.53%** |
| Clearance 35%     |         **-11.26%** |

The data shows an association between deeper discounting and weaker contribution performance.

This was treated as **diagnostic evidence, not causal proof**.

Controlled testing would be required to determine whether the discounts themselves caused the weaker economics.

---

## Return Analysis

Returns were analysed across:

* Category
* Product
* Customer segment
* Return reason
* Return rate
* Return loss

### Fashion

* Return rate: **23.01%**
* Size/Fit return loss: **€12.49K**

### Electronics

* Defective-product return loss: **€10.56K**
* Damaged-in-transit return loss: **€4.02K**

The analysis indicated different return patterns across categories.

### Return Data Validation

A reconciliation issue was identified between the headline and category-level return-loss calculations.

The validated headline return-loss figure was:

**€53.17K**

while the category drill-down displayed approximately:

**€64.04K**

These figures should **not be combined**.

The difference requires reconciliation of the underlying aggregation/denominator logic before a single return-loss figure is used as a board-level KPI.

---

## Fulfilment Analysis

| Location          |    Sales |       CM % | Stockout Rate |
| ----------------- | -------: | ---------: | ------------: |
| Berlin FC         | €115.96K | **27.23%** |            5% |
| Amsterdam Hub     |  €60.72K | **25.23%** |            5% |
| Madrid Hub        |  €41.58K | **23.42%** |            3% |
| Warsaw FC         |  €61.81K | **19.58%** |            6% |
| Riga FC           |  €53.41K | **13.97%** |            6% |
| Partner Fulfilled |  €70.63K | **13.33%** |            4% |

The results show meaningful variation in contribution economics between fulfilment locations.

However, the analysis does not assume that volume should automatically be moved between locations.

Further investigation would need to consider:

* Capacity
* Geography
* Delivery performance
* Product mix
* Customer mix
* Service levels

---

## Inventory and Stockouts

2025 recorded:

* **367 stockout units**
* **5% stockout rate**
* **+180.2% YoY stockout-unit growth**
* **146 Electronics stockout units**

Electronics represented approximately **39.8% of stockout units**.

Estimated lost-sales values were treated as **opportunity estimates**, not confirmed realised revenue losses.

---

## Customer Profitability

Customer segments were evaluated using sales, contribution, margin, discount, returns, orders and AOV.

| Segment     |    Sales | Contribution |       CM % |
| ----------- | -------: | -----------: | ---------: |
| VIP         |  €66.78K |      €16.91K | **25.33%** |
| Growth      | €105.65K |      €23.95K | **22.67%** |
| Loyal       | €108.86K |      €24.18K | **22.21%** |
| New         |  €54.21K |      €10.90K | **20.11%** |
| At Risk     |  €33.95K |       €6.06K | **17.86%** |
| Deal Seeker |  €34.65K |       €3.61K | **10.41%** |

Deal Seekers had the highest average discount rate:

**14.35%**

True customer lifetime value was not established because longitudinal retention and acquisition-cost data were outside the scope of the supplied analysis.

---

# 6. Diagnostic and Root-Cause Analysis

The project moved from descriptive analysis to diagnostic analysis by investigating the factors that could explain contribution performance.

---

## Contribution Leakage

The profitability investigation considered the following interconnected areas:

```text
Product Economics
       ↓
Pricing & Discounts
       ↓
Returns
       ↓
Fulfilment & Shipping
       ↓
Inventory Availability
       ↓
Customer Economics
       ↓
Contribution
```

The objective was to identify measurable areas of value leakage while distinguishing confirmed evidence from hypotheses.

---

## Product Economics

Electronics represented the clearest category-level profitability gap:

**€138.61K sales → €4.76K contribution**

SKU-level analysis identified products with very low or negative contribution.

Further investigation should separate the impact of:

* Product cost
* Pricing
* Discounts
* Returns
* Fulfilment
* Payment and other variable costs

---

## Promotion Economics

Promotion analysis compared campaign contribution against discount levels and return behaviour.

The evidence indicates that some higher-discount campaigns generated materially weaker contribution.

However, the project does not claim that discounting alone caused those outcomes.

To establish causal impact, future testing should include:

* Control groups
* Incremental demand
* Incremental contribution
* Cannibalisation
* Customer retention

---

## Return Drivers

The analysis identified different patterns:

### Fashion

Primary investigation area:

**Size / Fit / Customer expectation**

### Electronics

Primary investigation areas:

**Defective products / Transit damage**

This supports category-specific interventions rather than a single return-reduction strategy.

---

## Fulfilment and Shipping Economics

Shipping recovery ranged from:

| Location          |   Recovery |
| ----------------- | ---------: |
| Amsterdam         | **49.98%** |
| Riga              | **28.15%** |
| Warsaw            | **23.32%** |
| Berlin            | **21.88%** |
| Partner Fulfilled | **19.51%** |
| Madrid            | **14.87%** |

Low shipping recovery indicates that a larger proportion of outbound shipping cost is being absorbed by the business.

However, recovery must be evaluated alongside contribution and cost-to-serve.

---

## Stockout Opportunity

Stockouts were evaluated using both:

* Estimated lost sales
* Contribution economics

The analysis therefore distinguishes between:

> **Sales opportunity**

and:

> **Profitable sales opportunity**

A high-demand product with negative contribution should not automatically receive the same replenishment priority as a high-demand product with healthy contribution.

---

## Customer Economics

Customer profitability analysis moved beyond sales volume to consider:

```text
Revenue
+
Discount
+
Returns
+
Cost-to-serve
=
Contribution Economics
```

The analysis identified material differences between customer segments.

---

# 7. DAX and KPI Development

Reusable DAX measures were developed to support the analytical framework.

---

## Revenue Measures

Measures included:

* Net Sales
* Contribution Revenue
* Orders
* Average Order Value
* Revenue YoY
* Revenue Growth %

---

## Contribution Measures

Measures included:

* Contribution Margin
* Contribution Margin %
* Contribution YoY
* Contribution Growth %
* Contribution by Product
* Contribution by Category
* Contribution per Unit

---

## Time Intelligence

Time intelligence supported:

* Previous-year comparisons
* YoY growth
* Annual comparisons
* Period filtering
* Year-aware KPI indicators

---

## Commercial Measures

Measures included:

* Discount %
* Promotion Sales
* Promotion Contribution
* Promotion Contribution Margin %
* Promotion Return Rate

---

## Operational Measures

Measures included:

* Return Rate
* Return Loss
* Stockout Units
* Stockout Rate
* Estimated Lost Sales
* Shipping Cost
* Shipping Recovery %
* Fulfilment Cost

---

# 8. Power BI Visualisation

## Visualisation Approach

The Power BI report translated the analytical model into an interactive business intelligence solution.

Visual analysis covered:

* Executive performance
* Category profitability
* Product profitability
* Promotion performance
* Return analysis
* Fulfilment economics
* Inventory availability
* Customer profitability

---

## Dashboard Interactivity

The report incorporated:

* Slicers
* Cross-filtering
* Drill-down
* Drill-through
* Dynamic measures
* KPI indicators
* Interactive charts
* Year-over-year analysis

The objective was to allow users to move from:

**Executive KPI → Category → Product → Driver**

rather than viewing each metric in isolation.

---

# 9. Business Insights

## Key Findings

### 1. Strong overall growth

Net sales increased **71.0% YoY**, while contribution increased **103.7%**.

### 2. Product cost was the largest variable-cost component

Product cost represented approximately **73.5% of variable costs**.

### 3. Electronics had a significant revenue-to-contribution gap

**€138.61K sales → €4.76K contribution**

### 4. Loss-making SKUs existed within high-revenue categories

Tech Smart Home Plus generated **-€438 contribution**.

### 5. Promotion economics varied substantially

Clearance 35% generated **-11.26% contribution margin**, while Bundle & Save generated **28.84%**.

### 6. Return drivers differed by category

Fashion showed significant size/fit-related losses, while Electronics showed defective-product and transit-related losses.

### 7. Fulfilment economics varied

Contribution margins ranged from **13.33% to 27.23%**.

### 8. Stockouts represented additional opportunity

367 stockout units were identified, with Electronics accounting for approximately **40%**.

### 9. Customer economics varied materially

VIP customers generated **25.33% CM**, compared with **10.41% for Deal Seekers**.

---

# 10. Recommendations

## Product

* Review negative and near-zero contribution SKUs.
* Investigate product cost and pricing.
* Assess whether low-margin products require repricing or assortment decisions.

## Promotions

* Establish contribution thresholds.
* Evaluate promotions on incremental contribution rather than revenue alone.
* Introduce controlled testing where appropriate.

## Returns

* Investigate Fashion size/fit issues.
* Investigate Electronics defects.
* Review packaging and carrier handling for transit damage.

## Inventory

* Prioritise high-demand products with healthy contribution.
* Avoid automatically replenishing loss-making products solely because demand exists.

## Fulfilment

* Investigate whether eligible volume can be allocated toward stronger contribution locations.
* Validate capacity and service-level implications before reallocating volume.

## Shipping

* Investigate low shipping-recovery areas.
* Review free-shipping thresholds.
* Evaluate customer shipping charges and route economics.

## Customers

* Monitor contribution by segment.
* Investigate discount dependency among Deal Seekers.
* Develop customer strategies based on contribution rather than revenue alone.

---

# 11. Evidence vs Hypothesis

A key principle throughout the project was separating **measured evidence from interpretation**.

## Demonstrated Evidence

* Electronics generated high revenue but low contribution.
* Product cost was the largest variable-cost component.
* Some products generated negative contribution.
* Promotion contribution varied significantly.
* Fashion had a high return rate.
* Electronics had significant defective-product and transit-related return losses.
* Fulfilment economics varied by location.
* Stockout units increased materially year-on-year.
* Customer contribution margins differed materially by segment.

## Data-driven Explanations

* Pricing does not adequately cover product economics.
* Product costs is constraining contribution.
* Certain promotions sacrifice too much margin.
* Product quality contributes to Electronics returns.
* Fulfilment allocation may not be optimal.

## Further Testing Required

* Price elasticity
* Incremental promotion demand
* Promotion cannibalisation
* Customer lifetime value
* Customer acquisition cost
* Causal fulfilment impact
* Confirmed stockout revenue impact

This distinction ensures that **correlation is not presented as causation**.

---

# 12. Technical Stack

### Data Preparation

* Microsoft Excel
* Power Query

### Data Modelling

* Microsoft Power BI
* Dimensional modelling
* Relationships
* Date dimension

### Analytics

* DAX
* Exploratory Data Analysis
* KPI development
* Contribution analysis
* Profitability analysis
* Return analysis
* Customer segmentation
* Time intelligence
* Root-cause analysis

### Visualisation

* Microsoft Power BI
* Interactive reporting
* Drill-down
* Drill-through
* Cross-filtering
* Dynamic KPI reporting

---

# 13. Repository Structure

```text
2025-sales-profitability-analysis/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── powerbi/
│   └── profitability_analysis.pbix
│
├── documentation/
│   ├── business-requirements/
│   ├── data-dictionary/
│   └── analytical-definitions/
│
├── analysis/
│   └── exploratory-analysis/
│
│   └── dashboard/
│
└── README.md
```



---

# 14. Interactive Dashboard

The completed Power BI report is available here:

**[Explore the Interactive Power BI Dashboard](https://app.powerbi.com/view?r=eyJrIjoiNmM4MzVjMzctYjVlYi00OGMzLTlhZGMtMWZjMGE4N2ZhNDZhIiwidCI6ImIyMTFiMjkwLWFkNzUtNGJlNC1iZDk3LWI5Y2MxZDlmMzdlZCJ9)**

The dashboard allows interactive investigation of:

* Products
* Categories
* Promotions
* Returns
* Customers
* Fulfilment
* Inventory
* Contribution

---

# 15. Project Outcome

The project transformed the original management question:

> **Why are €404.1K in sales producing only €85.61K in contribution?**

into a structured end-to-end analytics investigation.

```text
Business Question
        ↓
Data Understanding
        ↓
Data Quality
        ↓
Data Preparation
        ↓
Data Model
        ↓
Exploratory Analysis
        ↓
Diagnostic Analysis
        ↓
DAX & KPI Development
        ↓
Power BI Visualisation
        ↓
Business Insights
        ↓
Recommendations
```

The resulting solution provided a **contribution-led view of business performance**, identifying measurable profitability gaps while clearly separating evidence from hypotheses requiring further testing.

---

# 16. Skills Demonstrated

## Business and Analytical Skills

* Business requirements analysis
* Business-question translation
* Commercial analytics
* Profitability analysis
* Root-cause analysis
* Data storytelling
* Decision support

## Data Skills

* Data profiling
* Data quality assessment
* Data cleaning
* Data transformation
* Exploratory data analysis
* Dimensional modelling

## Power BI Skills

* Power Query
* DAX
* Data modelling
* Time intelligence
* KPI development
* Drill-down
* Drill-through
* Interactive visualisation
* Dynamic reporting

## Analytical Thinking

* Contribution analysis
* Cost-to-serve analysis
* Revenue-quality analysis
* Customer profitability
* Promotion analysis
* Return analysis
* Inventory analysis
* Correlation vs causation
* Evidence-based recommendations

---

# 17. Author

## About the Author

**Elijah Okpako**

**Data Analyst | Business Intelligence | Power BI | Data Analytics**

> Turning complex business data into structured, evidence-based insights that support better commercial decisions.

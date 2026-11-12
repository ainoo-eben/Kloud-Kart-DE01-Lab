# Situation Diagnosis

**Kloud Kart**

## 1. Executive Summary

After reviewing Kloud Kart's current data environment, I identified a number of problems that affect its daily operations, reporting, customer data management and ability to grow.

I found that Kloud Kart's main problem is not a lack of data or the absence of a data warehouse. Rather, the company lacks a reliable, controlled and consistent way to manage and use its business data.

The company currently depends on manual CSV exports and separate spreadsheets to produce reports. This approach has created performance problems for the live website, inconsistencies between Finance and Operations, and limited control over customer information.

I consider the company's handling of personal data and the performance of its production database the most urgent concerns. These issues could expose Kloud Kart to regulatory consequences, lost sales and reputational damage.

I also found that the company's interest in real-time dashboards, data lakes and machine learning does not necessarily reflect its immediate business needs. Kloud Kart needs to address its existing problems before investing in advanced data capabilities.

## 2. Current Situation

Kloud Kart is a three-year-old e-commerce company based in Accra, Ghana. It processes approximately 4,000 orders daily and is currently piloting expansion into Nigeria.

From the information provided, I understand that:

- The company stores its orders, inventory and customer accounts in a MySQL database of approximately 40 GB.
- The database runs on the same machine as the live website.
- Nana Adjei, the Head of Operations, manually exports data into CSV files to prepare weekly reports.
- Finance maintains a separate spreadsheet, and its figures do not match Nana's reports.
- Marketing exports customer lists containing approximately 300,000 people, but the company does not track how many copies exist.
- The technical team currently has one PHP/MySQL developer and no one with professional experience managing a data warehouse or writing Python.
- The company has funding for only two additional data hires this financial year.

The company has also expressed interest in a data warehouse or lakehouse, real-time dashboards and machine-learning-based demand forecasting.

However, I do not consider these requests sufficient evidence that Kloud Kart needs to implement all these technologies immediately. I first need to understand the business problems they are expected to solve.

## 3. Ranked Findings: Root Causes and Business Impact

I ranked the following findings based on their potential impact on Kloud Kart, their urgency and the risks they could create for the company.

### Finding 1: Inadequate control over personal data

**Evidence from the brief**

- Marketing exports customer lists containing approximately 300,000 people.
- The company does not track how many copies of these lists exist.
- Kloud Kart has 90 days to respond to a Data Protection Commission complaint concerning a customer's deleted information.

**Root cause**

I found that Kloud Kart lacks an effective process for tracking, protecting, retaining and deleting personal information across its systems and exported files.

For example, deleting a customer's information from the primary MySQL database does not guarantee that the same information has been removed from spreadsheets or other copies.

**Business impact**

This creates several risks for the company:

- Kloud Kart may be unable to identify and delete every copy of a customer's personal information.
- Untracked customer-data copies increase the risk of unauthorised access and exposure.
- The company may struggle to demonstrate compliance with Ghana's Data Protection Act, 2012 (Act 843).
- Failure to handle the complaint appropriately could lead to regulatory, financial and reputational consequences.

**Cost and exposure**

I cannot calculate the exact financial exposure because the brief does not provide the number of existing data copies, affected records, incident costs or applicable regulatory consequences.

However, I expect the company to spend time identifying where customer information exists, investigating the complaint, establishing deletion procedures and documenting evidence.

As an initial planning estimate, I would allow 2–4 weeks of focused work involving the existing developer, an accountable business representative and appropriate privacy or legal support. This is an estimate, not a verified project duration.

**Why I consider this important**

As Kloud Kart grows, it will collect and process more customer information. I believe the company must demonstrate that it can manage this information responsibly rather than introduce more data systems and create additional uncontrolled copies.

### Finding 2: Reporting workloads affect the live website

**Evidence from the brief**

- Kloud Kart's MySQL database is approximately 40 GB.
- The database shares a machine with the live website.
- Large Monday reporting exports have slowed the website to a crawl twice in the previous month.

**Root cause**

I found that Kloud Kart runs its analytical and operational workloads against the same database and machine.

When Nana runs large reporting queries, those queries consume resources such as CPU, memory and disk activity. The live website needs those same resources to serve customers, retrieve product information and process orders.

This creates competition between reporting activities and the company's revenue-generating operations.

**Business impact**

- Customers may experience slower website response times.
- Some customers may abandon their shopping sessions.
- The company could lose sales because of poor website performance.
- As order volumes grow, the problem could become more frequent.
- Customers may lose confidence in the reliability of the online shop.

**Cost and exposure**

I cannot calculate the exact financial loss because the brief does not provide the duration of the slowdowns, affected customer sessions, conversion rates, abandoned orders or average order value.

I would estimate the potential lost revenue using:

> *Lost sales = Affected potential orders × Average order value × Estimated lost-conversion rate.*

The company will also incur infrastructure and engineering costs when it separates reporting workloads from the production environment.

**Why I consider this important**

The live website is central to Kloud Kart's business. I would not recommend an approach that allows reporting activities to interfere with customer orders and other production operations.

The company has already approved a second server or read replica, which gives us an opportunity to isolate reporting workloads without immediately introducing an unnecessarily complex platform.

### Finding 3: Inconsistent reporting and lack of agreed business definitions

**Evidence from the brief**

- Nana rebuilds the Monday numbers using CSV exports.
- Finance maintains a separate spreadsheet.
- Their reported figures do not match.

**Root cause**

I believe Kloud Kart lacks centrally agreed definitions and calculation rules for important business metrics.

For example, Finance might calculate revenue based on confirmed payments, while Operations might calculate it based on shipped orders. Both teams could be calculating correctly according to their own definitions, but they would not be measuring the same thing.

The problem is therefore not necessarily inaccurate source data. It may be the different ways both teams interpret and calculate the same business metric.

**Business impact**

- Management cannot confidently rely on the reported figures.
- Employees spend time investigating discrepancies instead of analysing business performance.
- Board reports may contain conflicting figures.
- Management could make decisions using different interpretations of the same metric.

**Cost and exposure**

The company loses staff time through manual exports, spreadsheet preparation, data cleaning and reconciliation. Both Nana and Finance spend a noticeable part of each week preparing or reconciling reports, and this time could be used for analysing business performance instead.

The brief does not say how many hours are spent on this, so I cannot give a confirmed cost. I would first measure the time each team spends on reporting and then work out the financial cost from that.

**Why I consider this important**

I believe Kloud Kart needs to agree on how it calculates important business metrics before centralising its reporting.

A data warehouse can bring information together, but it cannot independently decide what the business means by revenue, completed orders or active customers. The business teams must agree on those definitions.

### Finding 4: Unclear requirements for real-time analytics

**Evidence from the brief**

- Investors have requested real-time dashboards.
- The brief states that stock counts cannot become stale because this could lead to overselling.
- Other business information can refresh daily.

**Root cause**

I found that Kloud Kart has not clearly distinguished between the freshness requirements of different business activities.

The request for real-time dashboards appears to be driven partly by investor expectations rather than a documented assessment of which business decisions require real-time information.

**Business impact**

- Building real-time infrastructure for every business metric could increase unnecessary costs.
- The additional complexity could exceed the team's ability to maintain the platform.
- The company could spend resources on capabilities that do not provide meaningful business value.

Inventory is different because outdated stock information could cause the company to accept orders for products that are no longer available.

Revenue and other management reports can refresh daily because the brief confirms that a daily update is acceptable.

**Cost and exposure**

A real-time analytics platform could introduce additional infrastructure, monitoring, development and maintenance costs.

The brief does not provide enough information to calculate these costs. I would therefore evaluate the actual freshness requirements before recommending a technology.

**Why I consider this important**

I do not believe Kloud Kart should build real-time analytics across the entire business simply because an investor requested it.

I would prioritise reliable inventory updates while using daily processing for management reporting where a 24-hour delay is acceptable.

### Finding 5: Limited internal technical capacity

**Evidence from the brief**

- Kloud Kart currently has one PHP/MySQL developer.
- Nobody on the existing team has professionally managed a data warehouse or written Python.
- The company has funding for only two additional data hires.

**Root cause**

I found that Kloud Kart does not currently have the specialised skills or team capacity required to build and operate a complex data platform.

**Business impact**

- A complicated architecture could become difficult to maintain.
- The company may depend heavily on external vendors or contractors.
- The team may struggle to troubleshoot pipeline failures and infrastructure problems.
- Operating and maintenance costs could increase beyond what the company can support.

**Cost and exposure**

Kloud Kart must consider the cost of recruiting two data professionals, their salaries, infrastructure, training and ongoing platform maintenance.

I cannot provide reliable salary or infrastructure estimates without an approved budget range, hiring requirements and technology choices.

**Why I consider this important**

I believe the recommended solution must match Kloud Kart's current technical capabilities.

The company needs a data platform that its existing developer and two new hires can realistically build, operate and maintain. I would avoid introducing unnecessary complexity simply to imitate the architecture of a larger organisation.

## 4. Overall Risk Ranking

Based on my assessment, I ranked the findings as follows:

| Rank | Finding | Main risk |
|---|---|---|
| 1 | Inadequate control over personal data | Regulatory and reputational exposure |
| 2 | Reporting workloads affect the live website | Revenue loss and poor customer experience |
| 3 | Inconsistent reporting | Poor management and board decisions |
| 4 | Limited internal technical capacity | Implementation and operational failure |
| 5 | Unclear requirements for real-time analytics | Unnecessary cost and complexity |

I consider the first two findings the most urgent because they expose Kloud Kart to immediate regulatory and operational risks.

The reporting inconsistency also needs attention because management and investors need reliable figures to assess the company's performance.

I ranked technical capacity as a strategic constraint because it affects the company's ability to implement and maintain every proposed solution. The real-time analytics issue is important because it could lead to unnecessary investment if the company does not first establish its actual business requirements.

## 5. Conclusion

From my assessment, Kloud Kart's main challenge is not the absence of advanced analytics technology. It is the lack of reliable data management, safe reporting practices, consistent business definitions and effective control over personal information.

I believe the company should address its personal data management and production database performance problems before investing heavily in advanced analytics.

It must also establish consistent business metrics and distinguish between information that requires frequent updates and information that can refresh daily.

My overall conclusion is that Kloud Kart needs a practical data strategy that addresses its current business risks, supports its growth and fits the technical capacity and budget available to the company.

**I would prioritise solving the existing business problems before introducing technologies that Kloud Kart may not yet need or be ready to maintain.**

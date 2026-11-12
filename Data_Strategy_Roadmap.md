# Kloud Kart: 12-Month Data Strategy Roadmap

**Objective:** Build a reliable, secure and manageable data foundation that protects website performance, improves reporting consistency and supports business growth.

| Period | Key activities | Expected outcomes and how Nana can verify them |
|---|---|---|
| **Q1: Stabilise and establish control** | - Recruit the Data Engineer (first hire).<br>- Review customer data storage, exports, access and deletion procedures.<br>- Address the existing customer data complaint and document the response process.<br>- Set up and test a MySQL read replica.<br>- Agree on definitions for key business metrics with Finance and Operations. | - Customer data locations and access are documented.<br>- A documented process exists for handling customer data access and deletion requests.<br>- Reporting can run against the replica without unacceptable impact on the live website.<br>- Finance and Operations agree on core metric definitions. |
| **Q2: Build the reporting foundation** | - Recruit the Analytics Engineer (second hire).<br>- Select and configure a cloud-managed data warehouse.<br>- Build the initial historical data load and scheduled incremental pipeline.<br>- Introduce data validation, pipeline monitoring and failure alerts.<br>- Build the first centralised Finance and Operations reports. | - Historical business data is available in the warehouse.<br>- Daily reporting runs automatically.<br>- Pipeline failures and data quality issues are visible to the team.<br>- Finance and Operations use agreed definitions in their reports. |
| **Q3: Improve reporting and data reliability** | - Expand reporting to cover sales, orders, payments and operational performance.<br>- Improve data quality checks and reconciliation.<br>- Monitor replica lag, pipeline reliability and warehouse costs.<br>- Review customer data retention, access and deletion controls.<br>- Gather feedback from Nana, Finance and Operations. | - Key business reports are available from one trusted source.<br>- Reports are reconciled against operational records.<br>- Data freshness and pipeline failures are monitored.<br>- Warehouse costs and access controls are reviewed regularly. |
| **Q4: Prepare for growth and advanced analytics** | - Evaluate whether inventory analytics needs additional processing beyond the operational system.<br>- Assess the quality and completeness of historical data for demand forecasting.<br>- Identify a suitable forecasting pilot if reliable data and business value justify it.<br>- Review platform performance, costs and capacity for expansion into Nigeria.<br>- Present the next-year data strategy and investment requirements. | - Management has a documented assessment of forecasting readiness.<br>- Any proposed forecasting pilot has a defined business objective and success measure.<br>- The platform's performance, cost and growth limitations are documented.<br>- A prioritised data strategy for the following year is presented to management. |

## Measures of success

By the end of the 12 months, Kloud Kart should have:

1. Reporting workloads separated from the live website database.
2. Automated daily reporting for Finance and Operations.
3. Agreed and consistently applied business metric definitions.
4. Documented customer data access, retention and deletion procedures.
5. Two data professionals in place: a Data Engineer and an Analytics Engineer.
6. A measured and cost-controlled data platform that can support future growth.

**Implementation principle:** I will prioritise data protection, production stability and reliable reporting before investing in real-time analytics or machine learning. Inventory availability will continue to be managed by the operational system, not by the reporting warehouse.

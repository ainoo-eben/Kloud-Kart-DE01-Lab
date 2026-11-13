# Kloud Kart: 12-Month Data Strategy Roadmap

**Objective:** Build a reliable, secure and manageable data foundation that protects website performance, improves reporting consistency and supports business growth.

## Q1: Stabilise and establish control

**Key activities**

- Recruit the Data Engineer (first hire).
- Review customer data storage, exports, access and deletion procedures.
- Address the existing customer data complaint and document the response process.
- Set up and test a MySQL read replica.
- Agree on definitions for key business metrics with Finance and Operations.

**Expected outcomes**

- Customer data locations and access are documented.
- A documented process exists for handling customer data access and deletion requests.
- Reporting can run against the replica without unacceptable impact on the live website.
- Finance and Operations agree on core metric definitions.

## Q2: Build the reporting foundation

**Key activities**

- Recruit the Analytics Engineer (second hire).
- Select and configure a cloud-managed data warehouse.
- Build the initial historical data load and scheduled incremental pipeline.
- Introduce data validation, pipeline monitoring and failure alerts.
- Build the first centralised Finance and Operations reports.

**Expected outcomes**

- Historical business data is available in the warehouse.
- Daily reporting runs automatically.
- Pipeline failures and data quality issues are visible to the team.
- Finance and Operations use agreed definitions in their reports.

## Q3: Improve reporting and data reliability

**Key activities**

- Expand reporting to cover sales, orders, payments and operational performance.
- Improve data quality checks and reconciliation.
- Monitor replica lag, pipeline reliability and warehouse costs.
- Review customer data retention, access and deletion controls.
- Gather feedback from Nana, Finance and Operations.

**Expected outcomes**

- Key business reports are available from one trusted source.
- Reports are reconciled against operational records.
- Data freshness and pipeline failures are monitored.
- Warehouse costs and access controls are reviewed regularly.

## Q4: Prepare for growth and advanced analytics

**Key activities**

- Evaluate whether inventory analytics needs additional processing beyond the operational system.
- Assess the quality and completeness of historical data for demand forecasting.
- Identify a suitable forecasting pilot if reliable data and business value justify it.
- Review platform performance, costs and capacity for expansion into Nigeria.
- Present the next-year data strategy and investment requirements.

**Expected outcomes**

- Management has a documented assessment of forecasting readiness.
- Any proposed forecasting pilot has a defined business objective and success measure.
- The platform's performance, cost and growth limitations are documented.
- A prioritised data strategy for the following year is presented to management.

## Measures of success

By the end of the 12 months, Kloud Kart should have:

1. Reporting workloads separated from the live website database.
2. Automated daily reporting for Finance and Operations.
3. Agreed and consistently applied business metric definitions.
4. Documented customer data access, retention and deletion procedures.
5. Two data professionals in place: a Data Engineer and an Analytics Engineer.
6. A measured and cost-controlled data platform that can support future growth.

**Implementation principle:** I will prioritise data protection, production stability and reliable reporting before investing in real-time analytics or machine learning. Inventory availability will continue to be managed by the operational system, not by the reporting warehouse.

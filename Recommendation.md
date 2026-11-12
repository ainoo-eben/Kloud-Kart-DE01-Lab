# Kloud Kart: Data Strategy Recommendation

A summary of the recommended data strategy for Kloud Kart, a three-year-old e-commerce company based in Accra, Ghana, which processes about 4,000 orders a day and is piloting expansion into Nigeria.

## Overview

The recommendation is to build a reliable data foundation first, rather than invest immediately in complex real-time analytics or machine learning.

The proposed approach will:

- Separate analytical reporting from the live website
- Improve consistency between Finance and Operations
- Reduce manual reporting effort
- Establish better control over business data

## Proposed Architecture

```
Production MySQL → Read Replica → Data Pipeline → Data Warehouse → Reports and Dashboards
```

| Component | Purpose |
|---|---|
| Production MySQL | Runs the live website and operations |
| Read replica | Receives changes from production so reporting does not compete with customer transactions |
| Data pipeline | Extracts data from the replica on a schedule |
| Data warehouse | Central location for cleaned, organised and historical data |
| Reports and dashboards | Consistent reporting for Finance, Operations and management |

## Key Recommendations

### 1. Separate reporting from production
- Introduce a MySQL read replica.
- The pipeline extracts from the replica, not from the live database.
- Monitor replication health and lag so delayed data is caught before reports are published.

### 2. Use a cloud-managed data warehouse
- Evaluate Amazon Redshift and Google BigQuery before choosing a provider.
- Decide based on cost, integration, security, data location and the team's ability to manage the service.
- A managed service is preferred because the company has limited technical capacity.

### 3. Load data incrementally
- Do one full load of historical data, then incremental loads for daily operations.
- Capture new and modified records, prevent duplicates, validate loaded data and record successful or failed runs.
- Only advance the processing watermark after a successful load and validation.
- Refresh most management reports daily, and show the last successful refresh time on each report.

### 4. Keep inventory management operational
- Stock availability checks, reservations and updates stay in the operational application and primary database.
- The warehouse supports inventory analysis and reporting only. It must not decide whether a customer can buy available stock.
- Company-wide real-time reporting is not recommended.

## Data Governance and Compliance

Kloud Kart needs to improve how it tracks, protects, retains and deletes customer information. Recommended actions:

- Maintain an inventory of systems and locations holding customer data, including exported spreadsheets
- Introduce role-based access controls
- Set retention and deletion procedures that cover downstream copies
- Assign ownership and responsibility for important datasets
- Document data access and deletion activities

These controls should support compliance with Ghana's Data Protection Act, 2012 (Act 843). The existing customer data complaint should be prioritised, with appropriate privacy or legal support.

## Reporting Consistency

A warehouse alone will not fix the disagreement between Finance and Operations. Both teams must agree on shared definitions.

- Nana coordinates Finance and Operations to define: **orders placed**, **orders paid**, **orders shipped** and **revenue reported**.
- The data team implements these definitions centrally so both departments use the same figures.

## Hiring Plan

| Order | Role | Responsibilities |
|---|---|---|
| 1st hire | **Data Engineer** | Set up and monitor the read replica; build extraction and loading pipelines; establish the warehouse; implement data validation and pipeline monitoring; secure data movement and access |
| 2nd hire | **Analytics Engineer** | Agree metric definitions with Finance and Operations; transform data into reliable reporting datasets; build shared reporting models and dashboards; maintain reporting logic and support Nana's information needs |

A Data Scientist is not a priority at this stage. Demand forecasting should come after reliable historical data and consistent business measures exist.

## Cost and Investment Considerations

| Area | Expected cost |
|---|---|
| Read replica | Additional computing and storage |
| Data warehouse | Storage and query processing |
| Data pipeline | Data movement and processing |
| Reporting | Dashboard tools and possible licences |
| Staffing | Two data professionals |
| Governance | Security, monitoring and privacy support |

A reliable total cost cannot be given without actual infrastructure requirements, provider pricing and salary information. Before committing to a provider:

- Compare expected monthly operating costs
- Test the architecture with representative data
- Set up budget alerts and usage monitoring

## What Is Postponed

| Item | Reason |
|---|---|
| Company-wide real-time dashboards | Most management reports can refresh daily. Near-real-time should only be added where a specific business need justifies it. |
| Lakehouse or large data lake | Immediate needs centre on structured transactional data and reporting. |
| Machine-learning forecasting | Should follow reliable historical data and consistent reporting. |

These can be reconsidered as the business grows and its requirements become clearer.

## Conclusion

Prioritise a reliable data foundation built around a read replica, a cloud-managed warehouse and scheduled data pipelines. This addresses website performance, inconsistent reporting and uncontrolled customer data copies, while respecting the company's budget and limited technical capacity.

Solve the current data problems first, and expand into advanced analytics only when the business has a clear need and the capacity to support it.

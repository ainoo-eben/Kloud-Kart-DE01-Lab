# Kloud Kart: Data Strategy Recommendation

A summary of the recommended data strategy for Kloud Kart, a three-year-old e-commerce company based in Accra, Ghana, which processes about 4,000 orders a day and is piloting expansion into Nigeria.

## Overview

I recommend building a reliable data foundation first, rather than investing immediately in complex real-time analytics or machine learning.

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
- I recommend introducing a MySQL read replica.
- I recommend extracting data from the replica, not the live database.
- I recommend monitoring replication health and lag so delayed data is caught before reports are published.

### 2. Use a cloud-managed data warehouse
- I will evaluate Amazon Redshift and Google BigQuery based on cost, integration, security, data location and the team's ability to manage the service.
- I recommend a managed service because the company has limited technical capacity.

### 3. Load data incrementally
- I recommend an initial full load of historical data, followed by incremental loads for daily operations.
- The pipeline should capture new and modified records, prevent duplicates, validate loaded data and record successful or failed runs.
- The processing watermark should advance only after a successful load and validation.
- I recommend refreshing most management reports daily and showing the last successful refresh time on each report.

### 4. Keep inventory management operational
- I recommend keeping stock availability checks, reservations and updates in the operational application and primary database.
- I recommend limiting the warehouse to inventory analysis and reporting; it should not decide whether a customer can buy available stock.
- I do not recommend company-wide real-time reporting.

## Data Governance and Compliance

I recommend that Kloud Kart improve how it tracks, protects, retains and deletes customer information:

- Maintain an inventory of systems and locations holding customer data, including exported spreadsheets
- Introduce role-based access controls
- Set retention and deletion procedures that cover downstream copies
- Assign ownership and responsibility for important datasets
- Document data access and deletion activities

These controls should support compliance with Ghana's Data Protection Act, 2012 (Act 843). I recommend prioritising the existing customer data complaint and seeking appropriate privacy or legal support.

## Reporting Consistency

A warehouse alone will not fix the disagreement between Finance and Operations. I recommend that both teams agree on shared definitions.

- I recommend that Nana coordinate Finance and Operations to define **orders placed**, **orders paid**, **orders shipped** and **revenue reported**.
- I recommend that the data team implement these definitions centrally so both departments use the same figures.

## Hiring Plan

| Order | Role | Responsibilities |
|---|---|---|
| 1st hire | **Data Engineer** | Set up and monitor the read replica; build extraction and loading pipelines; establish the warehouse; implement data validation and pipeline monitoring; secure data movement and access |
| 2nd hire | **Analytics Engineer** | Agree metric definitions with Finance and Operations; transform data into reliable reporting datasets; build shared reporting models and dashboards; maintain reporting logic and support Nana's information needs |

I do not recommend hiring a Data Scientist at this stage. I recommend pursuing demand forecasting only after reliable historical data and consistent business measures are in place.

## Cost and Investment Considerations

| Area | Expected cost |
|---|---|
| Read replica | Additional computing and storage |
| Data warehouse | Storage and query processing |
| Data pipeline | Data movement and processing |
| Reporting | Dashboard tools and possible licences |
| Staffing | Two data professionals |
| Governance | Security, monitoring and privacy support |

I cannot provide a reliable total cost without actual infrastructure requirements, provider pricing and salary information. Before committing to a provider, I recommend that Kloud Kart:

- Compare expected monthly operating costs.
- Test the architecture with representative data.
- Set up budget alerts and usage monitoring.

## What Is Postponed

| Item | Reason |
|---|---|
| Company-wide real-time dashboards | Most management reports can refresh daily. I recommend adding near-real-time reporting only where a specific business need justifies it. |
| Lakehouse or large data lake | Immediate needs centre on structured transactional data and reporting. |
| Machine-learning forecasting | I recommend pursuing it only after reliable historical data and consistent reporting are in place. |

I would reconsider these as the business grows and its requirements become clearer.

## Conclusion

I recommend prioritising a reliable data foundation built around a read replica, a cloud-managed warehouse and scheduled data pipelines. This would address website performance, inconsistent reporting and uncontrolled customer data copies while respecting the company's budget and limited technical capacity.

I recommend solving the current data problems first and expanding into advanced analytics only when the business has a clear need and the capacity to support it.

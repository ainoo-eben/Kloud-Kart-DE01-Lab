# ADR-002: Use a Cloud-Managed Data Warehouse for Analytics

- **Status:** Proposed
- **Date:** 2026-11-12
- **Decision owner:** Ebenezer Ainoo
- **Approval:** Kloud Kart Management (required)

## Context

Kloud Kart stores its operational data in a MySQL database that supports the live website. Operations and Finance currently export data into separate spreadsheets, leading to inconsistent reports and repeated manual work.

The company needs a central location for historical and cleaned data so that both teams can work from consistent business metrics. However, Kloud Kart has limited technical capacity, with only one existing developer and funding for two data hires.

The solution must be manageable, cost-conscious and capable of supporting the company's expected growth.

## Decision

I recommend using a cloud-managed data warehouse as the central storage and reporting platform for Kloud Kart's analytical data.

I will evaluate suitable providers, including Amazon Redshift and Google BigQuery, based on operating cost, integration, security, scalability and the team's ability to manage the platform. The final provider will be selected after a practical cost and capability assessment.

## Alternatives considered

### Alternative A: Build a self-managed PostgreSQL data warehouse

- **How it would work:** Deploy PostgreSQL on a separate server and use it to store transformed historical data for reporting.
- **Why it is attractive:** It offers control over infrastructure, avoids committing to a specialised warehouse service and may have lower initial costs.
- **Why rejected:** Kloud Kart would be responsible for database maintenance, backups, scaling, performance tuning and infrastructure monitoring. This adds operational responsibilities to an already small technical team.

### Alternative B: Build a data lake or lakehouse

- **How it would work:** Store raw data in a data lake, or use a lakehouse platform that supports both raw data storage and analytical processing.
- **Why it is attractive:** It offers flexibility for different data formats and could support future machine learning and advanced analytics.
- **Why rejected:** Kloud Kart's immediate requirements are structured reporting, historical analysis and consistent business metrics. A lake or lakehouse introduces additional architectural and governance considerations that are not yet justified by the current needs.

## Consequences

- **What this buys:** A central location for analytical data, more consistent reporting across departments, reduced dependence on spreadsheets and a platform that can scale as the business grows. A managed service also reduces the infrastructure maintenance burden on the team.
- **What this costs:** Warehouse storage and query charges, data transfer, pipeline development, monitoring and staff time. Costs may increase as data volumes and reporting activity grow. Budget alerts, access controls and regular cost reviews will be required.
- **What it costs the client if I am wrong:** Kloud Kart could commit to a platform that becomes expensive, difficult to integrate or unsuitable for its reporting needs. Moving to another provider later could require additional migration work and cost.
- **What would make me revisit this:** Unexpectedly high operating costs, poor integration with existing systems, security or data-location requirements that the selected provider cannot satisfy, or a significant change in analytical workloads.

## What this survives

If the business grows or investors demand more advanced analytics, a managed warehouse provides a foundation that can be expanded without immediately redesigning the entire data platform.

If costs increase beyond what Kloud Kart can justify, management can review warehouse usage, optimise queries and storage, or compare alternative providers before committing to further investment.

If future machine learning or varied data workloads become genuine business requirements, Kloud Kart can assess whether additional data lake or lakehouse capabilities are justified rather than building them prematurely.

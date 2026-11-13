# ADR-003: Use Scheduled Batch Processing for Most Reporting

- **Status:** Proposed
- **Date:** 2026-11-12
- **Decision owner:** Ebenezer Ainoo
- **Approval:** Kloud Kart Management (required)

## Context

Kloud Kart's investors have expressed interest in real-time analytics. However, the business requirements show that inventory counts must remain current to prevent overselling, while other management and financial reports can be refreshed daily.

Building real-time data pipelines for every reporting need would introduce additional infrastructure, monitoring and maintenance costs. This is a concern because Kloud Kart has limited technical capacity and funding for only two data hires.

We need a processing approach that meets actual business needs without introducing unnecessary complexity.

## Decision

I recommend using scheduled batch processing for most analytical data, with daily warehouse updates for management reporting.

Inventory availability, reservations and stock updates will remain within the live operational system, where transactions are handled directly. More frequent analytical processing will only be introduced when a clearly defined business requirement justifies it.

## Alternatives considered

### Alternative A: Build real-time streaming pipelines for all data

- **How it would work:** Continuously capture and process database changes, making analytical data available shortly after transactions occur.
- **Why it is attractive:** It provides fresher analytical data and could support future real-time dashboards and monitoring.
- **Why rejected:** Most of Kloud Kart's reporting needs can be met through daily updates. Streaming introduces additional infrastructure, monitoring and operational complexity without a demonstrated business benefit for every dataset.

### Alternative B: Use less frequent batch processing, such as weekly updates

- **How it would work:** Extract and load data into the warehouse once a week for reporting.
- **Why it is attractive:** It reduces processing frequency and may lower operational costs.
- **Why rejected:** Weekly updates would leave management working with outdated information for too long. Daily processing provides a better balance between freshness, cost and operational simplicity.

## Consequences

- **What this buys:** A simpler and more manageable data pipeline, predictable reporting schedules and lower complexity than a company-wide streaming architecture. It also aligns processing frequency with actual business requirements.
- **What this costs:** Reports will not contain every transaction immediately after it happens. The team must maintain scheduled jobs, monitor failures and ensure reports are clearly labelled with their last successful update time.
- **What it costs the client if I am wrong:** If managers need information more frequently than once a day for certain decisions, delayed reports could affect their ability to respond quickly. The business may need additional processing infrastructure and development work to meet those requirements.
- **What would make me revisit this:** A documented business requirement for more frequent analytical updates, measurable losses caused by delayed information, or operational use cases that cannot be supported by the current reporting schedule.

## What this survives

If investors continue to demand real-time analytics, Kloud Kart can demonstrate that its processing approach is based on business requirements rather than technology trends. Specific datasets can move to more frequent processing when their value is established.

If the business expands into Nigeria or its operational needs change, processing schedules can be reviewed and adjusted without immediately replacing the entire architecture.

Inventory accuracy will remain protected because stock availability and reservations are handled by the operational application, not by the analytical warehouse.

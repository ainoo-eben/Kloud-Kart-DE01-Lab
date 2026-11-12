# ADR-004: Use Incremental Data Loading After an Initial Historical Load

- **Status:** Proposed
- **Date:** 2026-11-12
- **Decision owner:** Kloud Kart Management (approval required)

## Context

Kloud Kart's MySQL database contains approximately 40 GB of operational data and handles around 4,000 orders daily. The business expects continued growth, so the amount of data that needs to be processed will increase over time.

The warehouse needs an initial historical load, followed by regular updates. Repeatedly extracting and loading all available records would consume unnecessary resources and increase processing time.

We need a loading approach that supports daily reporting while maintaining data completeness and consistency.

## Decision

I recommend performing an initial historical load into the warehouse, followed by scheduled incremental loads that capture new and changed records.

The pipeline must use a reliable change-tracking method, prevent duplicate records, validate each load and record its execution status. It must only advance its loading checkpoint after a successful load and validation.

## Alternatives considered

### Alternative A: Perform a full data reload every day

- **How it would work:** Extract all relevant records from MySQL and reload the warehouse tables during every scheduled run.
- **Why it is attractive:** It is relatively straightforward to understand and can capture changes to historical records without requiring a separate change-tracking mechanism.
- **Why rejected:** As data volumes grow, repeatedly processing unchanged records wastes computing resources, increases processing time and creates unnecessary load on the extraction system.

### Alternative B: Use continuous change data capture (CDC)

- **How it would work:** Capture database changes continuously from MySQL's transaction logs and send them to the warehouse or an intermediate processing system.
- **Why it is attractive:** It can provide more frequent updates and capture changes without repeatedly scanning entire tables.
- **Why rejected:** Kloud Kart's current reporting requirements are mostly daily. Continuous CDC introduces additional infrastructure, monitoring and operational complexity that is not yet justified.

## Consequences

- **What this buys:** Reduced unnecessary data extraction, more efficient daily processing and a loading approach that can accommodate business growth. The initial historical load also gives management access to past data for trend analysis.
- **What this costs:** The team must implement and maintain change tracking, loading checkpoints, duplicate prevention, validation and recovery procedures. The initial historical load will also require careful planning because of its size and potential impact on the source database.
- **What it costs the client if I am wrong:** If the change-tracking method misses updates or the pipeline advances its checkpoint incorrectly, warehouse records could become incomplete or outdated. Management could then make decisions using inaccurate reports.
- **What would make me revisit this:** Persistent missed updates, unreliable change-tracking fields, unacceptable processing times, or a business requirement for more frequent updates that daily incremental processing cannot meet.

## What this survives

If Kloud Kart's data volume increases, incremental loading avoids repeatedly processing the entire historical dataset. The pipeline can be optimised as volumes and processing requirements grow.

If investors demand more frequent updates, the company can assess CDC for specific datasets rather than replacing the entire batch-processing approach.

If a pipeline run fails, the team must be able to retry it safely without duplicating records or losing changes. Loading checkpoints should only advance after successful validation, and the process should support reconciliation against the source data.

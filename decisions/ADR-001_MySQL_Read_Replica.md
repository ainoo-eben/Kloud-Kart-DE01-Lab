# ADR-001: Use a MySQL Read Replica for Reporting Extraction

- **Status:** Proposed
- **Date:** 2026-11-12
- **Decision owner:** Ebenezer Ainoo
- **Approval:** Kloud Kart Management (required)

## Context

Kloud Kart's production MySQL database shares a machine with its live website. Reporting exports have slowed the website twice because analytical queries compete with customer transactions for computing resources.

The company has already approved a second server or read replica. We need to separate reporting workloads from the production database without disrupting normal website operations.

## Decision

I recommend creating a MySQL read replica and directing reporting extraction queries to it instead of querying the production database directly.

I will require monitoring of replication health and lag, data freshness checks before extraction, and validation of extracted records.

## Alternatives considered

### Alternative A: Query the production database directly

- **How it would work:** The reporting pipeline connects directly to the existing production MySQL database and extracts the required records.
- **Why it is attractive:** It requires no additional database server and is initially cheaper and simpler.
- **Why rejected:** Reporting queries would continue competing with live website transactions for resources. This does not address the performance problem already experienced by Kloud Kart.

### Alternative B: Use periodic database exports

- **How it would work:** Export data from the production database periodically and load the exported files into a separate reporting database.
- **Why it is attractive:** Reporting would use a separate database, and the approach could be implemented with relatively simple tools.
- **Why rejected:** Export operations would still place load on the production database. Large exports could continue affecting website performance, and managing export schedules, file transfers and failed exports introduces additional operational work.

## Consequences

- **What this buys:** Reduces direct reporting query load on the production database, protects website performance and provides a separate source for scheduled warehouse extraction.
- **What this costs:** An additional server or replica, storage, replication bandwidth, monitoring and maintenance. Replication also consumes resources and may introduce data lag.
- **What it costs the client if I am wrong:** If the replica creates excessive resource overhead or falls behind, Kloud Kart could still experience production performance problems or produce reports using incomplete or outdated data. The company could incur additional infrastructure costs without achieving the expected benefits.
- **What would make me revisit this:** Persistent replication lag, unacceptable production performance impact, rising infrastructure costs or a change in reporting requirements that the replica cannot support reliably.

## What this survives

If investors demand more frequent reporting, the replica provides a separate extraction source that can support more frequent processing, subject to testing and monitoring.

If replication overhead or lag becomes unacceptable, I would reassess the extraction architecture rather than allow the replica to compromise the live website or the accuracy of reports.

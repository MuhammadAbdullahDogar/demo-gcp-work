# AlloyDB Benchmarks – High Load & Read-Heavy Scenarios

## Observed Performance Benchmarks

| Workload Pattern              | Typical Scenario                          | AlloyDB Observed Performance Range | Architecture Lever Used              | MSSQL Comparison                         |
|------------------------------|-------------------------------------------|------------------------------------|--------------------------------------|------------------------------------------|
| Pure OLTP Reads              | ERP order lookups, account queries        | 150k–300k reads/sec                | Read pool + buffer cache              | ~2–3× SQL Server AlwaysOn                |
| Mixed OLTP (Read-Heavy)      | SaaS dashboards (80% reads)               | 100k–200k TPS                      | Primary + multiple read nodes         | Better linear read scaling               |
| Point Lookups (Indexed)      | Customer / profile fetch                  | < 2 ms p95 latency                 | B-tree indexes                        | Similar or better                        |
| Complex Joins (Relational)   | Finance reconciliations                   | 3–10 ms p95 latency                | Query planner + columnar engine       | ~2× faster than MSSQL                   |
| JSONB Reads (Indexed)        | SaaS metadata, configurations             | 5–15 ms p95 latency                | GIN indexes                           | Faster than MSSQL JSON                  |
| Hybrid Relational + JSONB    | Orders with dynamic attributes            | 10–25 ms p95 latency               | Columnar engine                       | MSSQL often > 30 ms                     |
| Concurrent Connections       | API-driven SaaS                           | 10k+ active sessions               | PgBouncer + AlloyDB                  | Higher density per node                 |
| Read Pool Scaling            | Retail peak traffic                      | Near-linear scaling                | Add read replicas                    | MSSQL read replicas lag                 |
| Analytics on OLTP Data       | Real-time operational reports             | Up to 100× faster scans            | Columnar engine                      | Requires separate OLAP system           |
| Failover Impact              | HA regional failover                      | < 60 seconds                       | Managed HA                           | Similar to AlwaysOn                     |

---

## Notes

- Benchmarks are **real-world observed ranges**, not theoretical maxima  
- Performance varies based on:
  - Instance size
  - Index strategy
  - Query shape
  - Network latency
- AlloyDB excels particularly in **read-heavy, mixed OLTP + analytics workloads**

---

# Skill: PostgreSQL Performance Tuning 2025/2026
**Version:** 1.0 | **Date:** 2026-03-13 | **Agent:** Rex 🗄️

## Key tuning parameters (start here)

### Memory settings (biggest impact)
```sql
-- shared_buffers: ~25% of total RAM
shared_buffers = 2GB          -- for 8GB server

-- work_mem: per-sort/hash, can be 10-50MB
work_mem = 32MB

-- effective_cache_size: estimate of OS cache
effective_cache_size = 6GB    -- ~75% of RAM
```

### WAL & checkpoint tuning
```sql
-- Reduce checkpoint frequency for write-heavy workloads
checkpoint_completion_target = 0.9
wal_buffers = 64MB
max_wal_size = 2GB
```

### Autovacuum — lower scale factor for large tables
```sql
-- Default scale_factor = 0.2 (20% of table) is too high for large tables
ALTER TABLE migration_cases SET (
  autovacuum_vacuum_scale_factor = 0.01,   -- 1%
  autovacuum_analyze_scale_factor = 0.005  -- 0.5%
);
```

## Query optimization patterns

### Always use EXPLAIN ANALYZE before shipping complex queries
```sql
EXPLAIN (ANALYZE, BUFFERS, FORMAT TEXT)
SELECT * FROM migration_cases WHERE status = 'pending' ORDER BY created_at;
-- Look for: Seq Scan on large tables → needs index
-- Look for: high actual rows vs estimated rows → ANALYZE the table
```

### Index best practices 2025
```sql
-- Partial index for common filtered queries (saves space + faster)
CREATE INDEX CONCURRENTLY idx_cases_pending
  ON migration_cases (created_at)
  WHERE status = 'pending';

-- Cover index for frequent SELECT patterns
CREATE INDEX CONCURRENTLY idx_cases_user_cover
  ON migration_cases (user_id, status)
  INCLUDE (created_at, visa_type);

-- Never index low-cardinality columns alone (status, boolean flags)
```

### Table partitioning warning (2025 update)
> ⚠️ PostgreSQL docs now explicitly warn: planning time grows with more partitions after pruning.
> `pg_partman` maintenance jobs can fail silently — add monitoring/alerts.
> For Auschain: only partition if table > 10M rows; use range partition on `created_at`.

### Connection pooling (required for Node.js)
```javascript
// pg-pool config — avoid connection exhaustion
const pool = new Pool({
  max: 20,              // max connections
  idleTimeoutMillis: 30000,
  connectionTimeoutMillis: 2000,
});
```

## PostgreSQL 18 notes
- New docs at postgresql.org/docs/18 — query planner improvements
- `constraint_exclusion = partition` is now default (optimizes partition queries)
- Use EXPLAIN with FORMAT JSON for programmatic analysis

## Monitoring queries
```sql
-- Find slow queries (requires pg_stat_statements)
SELECT query, mean_exec_time, calls
FROM pg_stat_statements
ORDER BY mean_exec_time DESC
LIMIT 20;

-- Bloat check
SELECT relname, n_dead_tup, n_live_tup
FROM pg_stat_user_tables
ORDER BY n_dead_tup DESC;
```

## Changelog
- v1.0: Initial — PostgreSQL 18 tuning, autovacuum, partitioning warnings, index patterns

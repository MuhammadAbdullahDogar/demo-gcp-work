# BigQuery Capabilities for Handling JSONB-like Data

| Capability | BigQuery Support | Description | Example |
|-----------|----------------|-------------|---------|
| Native JSON data type | Yes | BigQuery provides a native JSON column type, equivalent to PostgreSQL JSONB | profile JSON |
| Read JSON fields | Yes | Access JSON fields using dot notation or JSON functions | profile.name |
| Write JSON data | Yes | Insert JSON literals directly into JSON columns | JSON {"a":1} |
| Store nested objects | Yes | Fully supports nested JSON objects | { "a": { "b": 1 } } |
| Store arrays | Yes | Supports JSON arrays | ["x", "y"] |
| Schema-less ingestion | Yes | No fixed schema required during ingestion | Load raw JSON |
| Convert JSON to STRUCT | Yes | Extract JSON fields into typed STRUCT columns | JSON_VALUE() |
| Convert STRUCT to JSON | Yes | Convert structured data back into JSON | TO_JSON() |
| Indexing JSON | No | Traditional indexes are not supported for JSON | Columnar scan |
| Query performance | Medium | JSON queries are slower than STRUCT-based queries | Prefer STRUCT |
| JSON validation | Yes | JSON is validated during insert and load | Invalid JSON rejected |
| Update JSON fields | Limited | Requires rewriting the entire row | JSON_SET() |
| Partial field updates | No | Partial row updates are not supported | Rewrite row |
| Field-level access control | No | Access control is column-level only | Not supported |
| Streaming JSON data | Yes | Supports streaming inserts | Streaming API |
| Load JSON files | Yes | Supports NDJSON and JSON file loads | GCS to BigQuery |
| JSONPath support | Partial | Supported via JSON functions | JSON_VALUE() |
| PostgreSQL JSONB equivalence | Yes | BigQuery JSON provides equivalent functionality | Functional match |

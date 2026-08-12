---
name: workfront-search-and-bulk-update-records
description: Find Workfront Planning records with a typed filter and safely apply a bulk change to
  them — search, page through the results, patch in batches, and reconcile partial failures — using
  only operations that exist in the published OpenAPI.
api: openapi/workfront-planning-v2-openapi.json
base_url: https://{customer-domain}/maestro/api
operations:
- searchRecordsPost
- searchRecordsGet
- getRecordsByRecordType
- getRecord
- patchRecord
- bulkPatchRecords
- bulkUpdateRecords
- bulkDeleteRecords
- getHistory
- moveRecords
method: generated
source: openapi/workfront-planning-v2-openapi.json + conventions/workfront-conventions.yml
generated: '2026-08-12'
---

# Search and bulk-update Workfront Planning records

Every `operationId` below was verified against `openapi/workfront-planning-v2-openapi.json`.

## Find the records

- **`searchRecordsPost`** (`POST /v2/record-types/{recordTypeId}/records/search`) is the operation to
  use. The filter is a **typed composite filter group** with explicit logical operators, sent as a
  JSON property in the body.
- `searchRecordsGet` takes the same filter as a JSON-encoded `filter` query parameter. Prefer the POST
  form: a non-trivial filter will blow past URI limits.
- `getRecordsByRecordType` (`GET /v2/record-types/{recordTypeId}/records`) lists without a filter.
- Search and list results are **cursor-paginated**. Follow the cursor to completion before you start
  writing — a bad filter that matches more than you expect is much cheaper to discover during the read
  pass.
- Use **field projection** to request only the fields you need. It is the difference between a fast
  page and a slow one.

## Apply the change

- One record: **`patchRecord`** (`PATCH /v2/records/{id}`) — partial update, only the fields you send
  are modified.
- Many records: **`bulkPatchRecords`** (`PATCH /v2/record-types/{recordTypeId}/records/bulk`) for
  partial updates, **`bulkUpdateRecords`** (`PUT …/bulk`) for full replacement, **`bulkDeleteRecords`**
  (`DELETE …/bulk`) to remove.
- To reorder or reparent, use **`moveRecords`** (`POST /v2/record-types/{recordTypeId}/records/move`),
  not a patch.

## Rules that will bite you

- **`PUT` replaces, `PATCH` merges.** `bulkUpdateRecords` is a full replacement — any field you omit
  is cleared. Reach for `bulkPatchRecords` unless you genuinely intend a replacement.
- **207 Multi-Status is the normal bulk outcome.** Treat any bulk response as a per-item result set:
  walk it, collect the failures, and re-drive only those. Do not re-send the whole batch.
- **There is no idempotency key.** A re-sent bulk request is a second write, not a replay of the
  first. Reconcile with `getRecord` before retrying anything that may have partially landed.
- **409 Conflict is optimistic-concurrency, not a rate limit.** Something else wrote the record while
  you were working. Re-read, re-apply, re-submit.
- **Branch on `errorCode`, not on `status`.** The RFC 7807 body carries `errorCode` (a string in v2),
  `requestId`, and an `errors[]` array of `{field, message, code}` for validation failures. `403` in
  particular is frequently a capacity limit — e.g. `RECORD_CONNECTION_LIMIT_EXCEEDED`,
  `HIERARCHY_RECORD_CONNECTION_LIMIT_EXCEEDED` — rather than a permission problem.
- **Audit what you changed.** `getHistory` (`GET /v2/records/{id}/history`) returns the record change
  log; it is the only published way to prove after the fact what a bulk run did.
- **Cross-surface caution.** Planning records are *not* Workfront projects, tasks or issues. Those
  live on the core `/attask/api` surface, which has no OpenAPI, different auth (`SessionID` header),
  offset pagination (`$$FIRST`/`$$LIMIT`, max 2000) and a `{"error": {...}}` envelope. Do not carry
  these conventions across. See `conventions/workfront-conventions.yml`.

---
name: workfront-build-planning-workspace
description: Stand up a Workfront Planning workspace end to end over the Planning API v2 — create the
  workspace, add record types, add fields to each record type, create a view, then load records —
  using only operations that exist in the published OpenAPI.
api: openapi/workfront-planning-v2-openapi.json
base_url: https://{customer-domain}/maestro/api
operations:
- createWorkspace
- createRecordType
- getRecordTypesByWorkspace
- createField
- getFieldsByRecordType
- createView
- createRecord
- bulkCreateRecords
- getWorkspace
method: generated
source: openapi/workfront-planning-v2-openapi.json + conventions/workfront-conventions.yml
generated: '2026-08-12'
---

# Build a Workfront Planning workspace

Every `operationId` below was verified against `openapi/workfront-planning-v2-openapi.json`. Do not
invent operations — the Planning API has 49 of them and no others.

## Before you start

- **Auth is OAuth 2.0 only.** `sessionID` and `apiKey` are not accepted by the Planning API. Get a
  bearer token from an Adobe Developer Console credential — server-to-server (client credentials) for
  automation, authorization code for acting as a user. See `authentication/workfront-authentication.yml`.
- **The published spec declares no `securitySchemes`.** A generated client will omit the
  `Authorization` header. Add it yourself.
- **Base URL is templated.** `https://{customer-domain}/maestro/api/v2/...` where `{customer-domain}`
  is the organization's own Workfront host (`<yourdomain>.my.workfront.adobe.com`), found in
  Workfront under Setup > System > Customer Info.
- **Planning requires an entitled package.** If the organization's Workfront package does not include
  Adobe Workfront Planning, every call here returns 403.

## Steps

1. **Create the workspace** — `createWorkspace` (`POST /v2/workspaces`). Returns the workspace id.
2. **Add record types** — `createRecordType` (`POST /v2/workspaces/{workspaceId}/record-types`), one
   call per type. Confirm with `getRecordTypesByWorkspace` (`GET /v2/workspaces/{workspaceId}/record-types`).
3. **Add fields** — `createField` (`POST /v2/record-types/{recordTypeId}/fields`) per field. Read
   back with `getFieldsByRecordType`.
4. **Create a view** — `createView` (`POST /v2/record-types/{recordTypeId}/views`).
5. **Load records** — one at a time with `createRecord`
   (`POST /v2/record-types/{recordTypeId}/records`), or in batches with `bulkCreateRecords`
   (`POST /v2/record-types/{recordTypeId}/records/bulk`).
6. **Verify** — `getWorkspace` (`GET /v2/workspaces/{id}`).

## Rules that will bite you

- **There is no idempotency key.** Retrying a failed `createWorkspace`, `createRecordType` or
  `createRecord` creates a duplicate. Before any retry, read back with the matching `get*` operation
  and only re-issue if the object is genuinely absent.
- **Bulk is partial-success.** `bulkCreateRecords` returns **207 Multi-Status** when some items
  succeed and some fail. A 207 is not a success — walk the per-item results and re-drive only the
  failures.
- **409 means someone else wrote first.** Re-read the object and re-apply your change; do not blind
  retry.
- **403 is usually a limit, not a permission.** Planning encodes capacity as 403 with a named
  `errorCode`: `WORKSPACE_LIMIT_EXCEEDED`, `RECORD_TYPE_LIMIT_EXCEEDED`,
  `RECORD_TYPE_RECORD_LIMIT_EXCEEDED`, `FIELD_LIMIT_EXCEEDED`, `VIEW_LIMIT_EXCEEDED`,
  `RECORD_CONNECTION_LIMIT_EXCEEDED`, `FIELD_DISPLAY_NAME_NOT_UNIQUE`. Branch on `errorCode`, never
  on the status alone.
- **Errors are RFC 7807 problem details.** Required fields are `title`, `status`, `detail`,
  `errorCode`, `requestId`. Branch on `errorCode`; quote `requestId` to Adobe support.
- **429 has no headers.** Workfront documents a 429 but publishes no `RateLimit-*` or `Retry-After`
  header, so back off exponentially on your own schedule.
- **v1 is a different contract.** If you are pinned to v1 (Workfront Fusion still is), there is no
  `PATCH`, every success is `200`, and errors use a numeric `type` with a `report` object.

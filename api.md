# BoxFleet hosted control plane (boxfleet.io) Kotlin API

<!-- omniwrap-api-reference eyJjb250cmFjdF9maW5nZXJwcmludCI6ImUzZmQ0Yzc0NGFlODkzM2MwZTBiZDBjMjFhNjkyODk3Nzk1YTE0NjU3ZTU3N2ZiODIxMDg1MDBkMzlmMmFjOGQiLCJvcGVyYXRpb25fY291bnQiOjU2LCJyZW5kZXJlciI6ImtvdGxpbiIsInZlcnNpb24iOiIxLjUuMCJ9 -->

This generated index is tied to Semantic IR `1.14.0` and contract fingerprint `e3fd4c744ae8933c0e0bd0c21a692897795a14657e577fb82108500d39f2ac8d`. Every operation below is rendered from the same semantic contract and artifact-attested public member allocation as the SDK.

SDK maturity: **experimental**  
Artifact evidence: [`omniwrap-artifact.json`](omniwrap-artifact.json) binds this file by SHA-256 and is revalidated by the package gate.

## Client hooks and tracing

`ClientOptions(hooks = RequestHooks(...))` registers four callbacks. Every attempt starts with `beforeRequest` and ends with exactly one of `onRetry` (another attempt follows), `afterResponse` (the success the call returns) or `onError` (the failure the call reports). Each receives the operation id, the HTTP method, the URL, the request headers, the attempt number (from 1), the time elapsed since the call started and, once the server answered, the HTTP status. No context carries a credential: `Authorization`, `Proxy-Authorization`, `Cookie`, every API-key header and API-key query parameter, and any configured credential value read `[redacted]`. Every context is an immutable `HookContext`: no hook can change the request.

`ClientOptions(tracer = ...)` opens one span per call through the tracer interface this SDK defines, named after the operation id, with `http.request.method`, `http.response.status_code` and `http.request.resend_count`. It needs no tracing library; README.md maps it onto the OpenTelemetry API.

## Shared types

- `HostedPersistentBoxClose`
- `HostedPersistentBoxRead`
- `HostedPersistentUsageMeter`
- `HostedPersistentUsageRead`
- `ObservedBox`

## Resource `accounts`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhY2NvdW50cy5nZXRBY2NvdW50c0NvbmZpZyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEFjY291bnRzQ29uZmlnIiwicGF0aCI6Ii92MS9hY2NvdW50cy9jb25maWciLCJyZXNvdXJjZSI6ImFjY291bnRzIiwic2VjdGlvbl9zaGEyNTYiOiI3ZjU1ZWI4MTNmMDdhNGQzZTRkZjI3NjI4M2YwZGQ4YmQ2NWU1OTMzZWUyY2JiMWVhZDU5OTQ1YzRiZWJmYjE5Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImRlMmFiM2UxNTU0MWFkYjMzYmRhNTgyNzFiNzk1NjE1M2ZjNjg0ZGQ3Y2Y5ZmUwNmEwYmIxNWMyN2QzMDhlYWEifQ -->
### `client.accounts.getAccountsConfig`

Operation ID: `getAccountsConfig`  
Route: `GET` `/v1/accounts/config`  
Equivalent member: `client.getAccountsConfig`  

#### Signature

```kotlin
suspend fun getAccountsConfig(params: GetAccountsConfigParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.accounts.getAccountsConfig()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBY2NvdW50c0NvbmZpZyJ9 -->

## Resource `admin`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi5jb250cm9sVXNlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjb250cm9sVXNlciIsInBhdGgiOiIvdjEvYWRtaW4vdXNlcnMiLCJyZXNvdXJjZSI6ImFkbWluIiwic2VjdGlvbl9zaGEyNTYiOiJhOWE3NjFkZWE4NDNlNWNlNmNhMWNiZjZmMzEwMGU5NGYyNTQzNmY3NTE0NmI1OWFkMWYzMWE1MzU2NzVjMTFmIiwic2lnbmF0dXJlX3NoYTI1NiI6ImM1MTk4YmE1ZjI2ZGI0MTQzYTdmOGE1YWYwMDc0ZDVlZGZlZGYxMGM3MTFiMTZhNzBlMjc4ZWUzOThmYjI1N2IifQ -->
### `client.admin.controlUser`

Operation ID: `controlUser`  
Route: `POST` `/v1/admin/users`  
Equivalent member: `client.controlUser`  

#### Signature

```kotlin
suspend fun controlUser(params: ControlUserParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Applied | none |
| `401` | Admin token required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.admin.controlUser(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjb250cm9sVXNlciJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi5nZXRBZG1pbkNvbnNvbGUiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRBZG1pbkNvbnNvbGUiLCJwYXRoIjoiL3YxL2FkbWluL2NvbnNvbGUiLCJyZXNvdXJjZSI6ImFkbWluIiwic2VjdGlvbl9zaGEyNTYiOiIyZTFiYjVhZTc0MDU0ZmEzNjIzZGUwMDFiZTg0M2U5OGQxZThjZWViMjk2YTg1NzRhNTc0ZjRkNzg5YzZiYThmIiwic2lnbmF0dXJlX3NoYTI1NiI6ImVlMzYxYWNlN2NkMWQ0MGIzY2RlMzA2YzVjOGVkOTM4MzlmZWQwNjFjYzQzZWY3ZmZiYzBhMzFmYzhiZjRlNjAifQ -->
### `client.admin.getAdminConsole`

Operation ID: `getAdminConsole`  
Route: `GET` `/v1/admin/console`  
Equivalent member: `client.getAdminConsole`  

#### Signature

```kotlin
suspend fun getAdminConsole(params: GetAdminConsoleParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Console | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.admin.getAdminConsole()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBZG1pbkNvbnNvbGUifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi5nZXRBZG1pblBsYW5zIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0QWRtaW5QbGFucyIsInBhdGgiOiIvdjEvYWRtaW4vcGxhbnMiLCJyZXNvdXJjZSI6ImFkbWluIiwic2VjdGlvbl9zaGEyNTYiOiI5MzE0MTk4YzE5NWViMTZlY2M5MTdjZGZhYjljZWUzZTgyZTk3YzdiMzRkMGZiYzFkZWM1YzgxMjE2ZTJkM2JiIiwic2lnbmF0dXJlX3NoYTI1NiI6IjNlNTg5NzJkNDliMzU3OGZmNmJiOTJiZjc0NWYxNmUyODQyZWVkZGU1MjI0N2VmMmUzOTNjNmExOWI3ODAzNTEifQ -->
### `client.admin.getAdminPlans`

Operation ID: `getAdminPlans`  
Route: `GET` `/v1/admin/plans`  
Equivalent member: `client.getAdminPlans`  

#### Signature

```kotlin
suspend fun getAdminPlans(params: GetAdminPlansParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Plans | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.admin.getAdminPlans()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBZG1pblBsYW5zIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi5saXN0VXNlcnMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0VXNlcnMiLCJwYXRoIjoiL3YxL2FkbWluL3VzZXJzIiwicmVzb3VyY2UiOiJhZG1pbiIsInNlY3Rpb25fc2hhMjU2IjoiMTNlZWM4MjY2NjcyNzE4NmI5Zjk4NmIyYjc2OWFiNzEyZmE3MDg2ZTNjNWNkMTAxOTgzNWRkY2JkNzI4OTRlYSIsInNpZ25hdHVyZV9zaGEyNTYiOiJhZjM4ODJjMmFhYzZkYTRmOTBhNTExMGM2MDM1OGQ4ZTViYjNlMDdjOTIyMzgwZGIyMTk2ZjE2MzBjYWNhY2NiIn0 -->
### `client.admin.listUsers`

Operation ID: `listUsers`  
Route: `GET` `/v1/admin/users`  
Equivalent member: `client.listUsers`  

#### Signature

```kotlin
suspend fun listUsers(params: ListUsersParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Users | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.admin.listUsers()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0VXNlcnMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi5yZWFkVGVsZW1ldHJ5IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoicmVhZFRlbGVtZXRyeSIsInBhdGgiOiIvdjEvYWRtaW4vdGVsZW1ldHJ5IiwicmVzb3VyY2UiOiJhZG1pbiIsInNlY3Rpb25fc2hhMjU2IjoiNjIzNjdhNDYxYzA5NTNlYzdhMDBmN2Y3MzJhMDU5YWViYjJkZDU0NDBhNjRhNWZlZGE5NTYzMDZkY2ZmODU3NyIsInNpZ25hdHVyZV9zaGEyNTYiOiIwOWI3OTIyNGQwMDFlMWMxMTJjMzk1MzZhNDE0NjU0YzA5NTcwNzlhMDUxYWMwMmUwNjY2ZDkxN2FkZGUxM2NkIn0 -->
### `client.admin.readTelemetry`

Operation ID: `readTelemetry`  
Route: `GET` `/v1/admin/telemetry`  
Equivalent member: `client.readTelemetry`  

#### Signature

```kotlin
suspend fun readTelemetry(params: ReadTelemetryParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Events | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.admin.readTelemetry()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWFkVGVsZW1ldHJ5In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhZG1pbi51cGRhdGVQbGFuIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InVwZGF0ZVBsYW4iLCJwYXRoIjoiL3YxL2FkbWluL3BsYW5zIiwicmVzb3VyY2UiOiJhZG1pbiIsInNlY3Rpb25fc2hhMjU2IjoiNDNkYjZiZTIzMWRiY2MxZTE0ODliMDU3ODJmM2I4MDU4ZDk3MzI5ZThiYWQyNzBmY2QxMjEzMGNmZjc2ZjM3MiIsInNpZ25hdHVyZV9zaGEyNTYiOiI4MzA5MTY0OTk0OTk4ZDU2NWI3MDJhMDNjNDUyMGM3YzQ4MzIyNGY2MWY1ZjU1ZGViNzJjYzI1YTJlMmVmYjI0In0 -->
### `client.admin.updatePlan`

Operation ID: `updatePlan`  
Route: `POST` `/v1/admin/plans`  
Equivalent member: `client.updatePlan`  

#### Signature

```kotlin
suspend fun updatePlan(params: UpdatePlanParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Updated | none |
| `401` | Admin token required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.admin.updatePlan(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ1cGRhdGVQbGFuIn0 -->

## Resource `auth`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhdXRoLmdldEF1dGhHYXRlIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0QXV0aEdhdGUiLCJwYXRoIjoiL3YxL2F1dGgvZ2F0ZSIsInJlc291cmNlIjoiYXV0aCIsInNlY3Rpb25fc2hhMjU2IjoiYWFlOTNmNmFjZGZlMTMwYzNkZTEyNjc2ZmJiNTNiOTNlNmRiNTJhMjIwNTY1OGI0MzJkNGE1OGQ1MmFjOTllNiIsInNpZ25hdHVyZV9zaGEyNTYiOiJlZGQyOGUwNDk2OWRjNGQ2MmU4ODczMDZkN2M1MGRkZDZiZTk5N2I5YTQyYzY2MjNmYmVhMTIyZjQ4NTZmNWE1In0 -->
### `client.auth.getAuthGate`

Operation ID: `getAuthGate`  
Route: `GET` `/v1/auth/gate`  
Equivalent member: `client.getAuthGate`  

#### Signature

```kotlin
suspend fun getAuthGate(params: GetAuthGateParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.auth.getAuthGate()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRBdXRoR2F0ZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhdXRoLnJlZ2lzdGVyIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InJlZ2lzdGVyIiwicGF0aCI6Ii92MS9hdXRoL3JlZ2lzdGVyIiwicmVzb3VyY2UiOiJhdXRoIiwic2VjdGlvbl9zaGEyNTYiOiI1ZDU4MGE1NmE1ZDY4OTQ1MzM3MjNiMTllMmE2NGM5ZmNhZTAzZjZhYzc2MmVkNDFkYjNmZmNhNTkyZmY1MTc3Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjNmNWM1ZjFlOWI4YWVhNDQwNTM3NzQ0N2JjNWVjOGJiNDBlZjQ3OGFlN2RlZTQ0MmY2NzkzZTQyNWVkZDJjMDcifQ -->
### `client.auth.register`

Operation ID: `register`  
Route: `POST` `/v1/auth/register`  
Equivalent member: `client.register`  

#### Signature

```kotlin
suspend fun register(params: RegisterParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | License issued | none |
| `202` | Verification code sent (or withheld by the resend cooldown) | none |
| `400` | Invalid or expired code | none |
| `403` | Not invited or refused | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |
| `429` | Rate limited | none |
| `503` | Registration not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.auth.register(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWdpc3RlciJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhdXRoLnVwZGF0ZUF1dGhHYXRlIiwibWV0aG9kIjoiUFVUIiwib3BlcmF0aW9uX2lkIjoidXBkYXRlQXV0aEdhdGUiLCJwYXRoIjoiL3YxL2F1dGgvZ2F0ZSIsInJlc291cmNlIjoiYXV0aCIsInNlY3Rpb25fc2hhMjU2IjoiYmU5Y2Y4YzA1OWI2NzdhYTNmZGY5NGE3YmQ1M2Q3NTUzN2ExOWUyNmQzYWFiNjNkOTcxMGNmZmE2OWYxMTY5YSIsInNpZ25hdHVyZV9zaGEyNTYiOiJmY2Q0ZTA3ODE1MjMxYmVlZGEzMTUyNWQzMWI4NWZkNjkxNjA0YjQ2MjcyMWM5ZjQ2YTYyNTlhMjMwNDEyOTgyIn0 -->
### `client.auth.updateAuthGate`

Operation ID: `updateAuthGate`  
Route: `PUT` `/v1/auth/gate`  
Equivalent member: `client.updateAuthGate`  

#### Signature

```kotlin
suspend fun updateAuthGate(params: UpdateAuthGateParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Updated | none |
| `401` | Admin token required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.auth.updateAuthGate(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ1cGRhdGVBdXRoR2F0ZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJhdXRoLnZlcmlmeUxpY2Vuc2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoidmVyaWZ5TGljZW5zZSIsInBhdGgiOiIvdjEvYXV0aC92ZXJpZnkiLCJyZXNvdXJjZSI6ImF1dGgiLCJzZWN0aW9uX3NoYTI1NiI6ImYwYzc0ZGFiNWQxODA0MGMxZDIwNmNlY2Y3YjZlMDQzMjc2OTg4NWRhY2M2ZGQ0NDcwMzM3NzY0ZDQ1YzkxZDAiLCJzaWduYXR1cmVfc2hhMjU2IjoiY2U4ZWY0ZGQyYjJhZDU2MjNjNGExOTVjYTA3NjMwOTkyNDg3MzhhM2IxMWI4MTg5OWU0NDkzNGEwYmRiYTU0MiJ9 -->
### `client.auth.verifyLicense`

Operation ID: `verifyLicense`  
Route: `POST` `/v1/auth/verify`  
Equivalent member: `client.verifyLicense`  

#### Signature

```kotlin
suspend fun verifyLicense(params: VerifyLicenseParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Valid | none |
| `401` | Invalid license | none |
| `403` | Refused | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |
| `503` | Verification not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.auth.verifyLicense(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ2ZXJpZnlMaWNlbnNlIn0 -->

## Resource `billing`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJiaWxsaW5nLnN0cmlwZVdlYmhvb2siLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoic3RyaXBlV2ViaG9vayIsInBhdGgiOiIvdjEvYmlsbGluZy9zdHJpcGUvd2ViaG9vayIsInJlc291cmNlIjoiYmlsbGluZyIsInNlY3Rpb25fc2hhMjU2IjoiYzFmOWE2M2JmZTZlZDg5N2Q4MTkxZmVjOGE5NDcxYjM3N2Y1MDc5OGVjZmViOGZkZmFjYmIxOTBkYTRjMTk0MyIsInNpZ25hdHVyZV9zaGEyNTYiOiI1OGEwY2UzOTkwZWZmNzY3NTQyZDQ2ZjhhOWYyOTlkMzZkNGYyMWMyZDkyYmRlYjE5YWY2OTA4YmY3ODNmMjEwIn0 -->
### `client.billing.stripeWebhook`

Operation ID: `stripeWebhook`  
Route: `POST` `/v1/billing/stripe/webhook`  
Equivalent member: `client.stripeWebhook`  

#### Signature

```kotlin
suspend fun stripeWebhook(params: StripeWebhookParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Received | none |
| `400` | Invalid signature or payload | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.billing.stripeWebhook()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdHJpcGVXZWJob29rIn0 -->

## Resource `health`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJoZWFsdGguZ2V0SGVhbHRoIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0SGVhbHRoIiwicGF0aCI6Ii9oZWFsdGgiLCJyZXNvdXJjZSI6ImhlYWx0aCIsInNlY3Rpb25fc2hhMjU2IjoiN2NjMjE0ZDFkMjAyYTIxOTM2NzU2NmEzMzRjOWUwMDU2MjgzMzZkNTRkMDJjYTA1Mzc1NGZjMjA0ZDZiZGJmYyIsInNpZ25hdHVyZV9zaGEyNTYiOiI2NGNhZmRlNGUzMWFmNWIxMDMxYjZmYjk5ZWFlMWRkMGJmZWJkMzhiMGExYWRjMmIyYzJjY2JhNWU3ZWZiNDcyIn0 -->
### `client.health.getHealth`

Operation ID: `getHealth`  
Route: `GET` `/health`  
Equivalent member: `client.getHealth`  

#### Signature

```kotlin
suspend fun getHealth(params: GetHealthParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.health.getHealth()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIZWFsdGgifQ -->

## Resource `jobs`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJqb2JzLmNhbmNlbEpvYiIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjYW5jZWxKb2IiLCJwYXRoIjoiL3YxL2pvYnMve2pvYklkfS9jYW5jZWwiLCJyZXNvdXJjZSI6ImpvYnMiLCJzZWN0aW9uX3NoYTI1NiI6ImMxZWQzZjQ3ZmFhNjdhMzA4Y2E0YWIxYmFiYzlhMWI2ZGRhZjM2YmI5ZTRjZDE5YmQ2MjA4NmE2MWRiNGZhMTQiLCJzaWduYXR1cmVfc2hhMjU2IjoiMDJhZGRiODA0ZjQ4MGJjYmFlMmVjNWVhNmZjNmU3MjM1NjExMjA0MTEwMzRhZjI4N2Y1OWNkNzFkNDZiNjFhNyJ9 -->
### `client.jobs.cancelJob`

Operation ID: `cancelJob`  
Route: `POST` `/v1/jobs/{jobId}/cancel`  
Equivalent member: `client.cancelJob`  

#### Signature

```kotlin
suspend fun cancelJob(params: CancelJobParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.jobs.cancelJob(jobId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjYW5jZWxKb2IifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJqb2JzLmdldEpvYiIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEpvYiIsInBhdGgiOiIvdjEvam9icy97am9iSWR9IiwicmVzb3VyY2UiOiJqb2JzIiwic2VjdGlvbl9zaGEyNTYiOiI1NTdkOWEwY2I3MThiYzM1NzE3ZmRmNGJlZGIyOGVjMWE0NmU4N2UzYTg0MWViMWNkMTFiYjU2NzIyNWYwZmVjIiwic2lnbmF0dXJlX3NoYTI1NiI6ImU4YzM0MGIyYjVkNGE4ZTlmYWFmYThiNjk3MWQ4ZjgxYzg2ZTRhZjI1ZDRkOTBlYTI4NTRlNDY5ODQ5ZjU3MWUifQ -->
### `client.jobs.getJob`

Operation ID: `getJob`  
Route: `GET` `/v1/jobs/{jobId}`  
Equivalent member: `client.getJob`  

#### Signature

```kotlin
suspend fun getJob(params: GetJobParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.jobs.getJob(jobId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRKb2IifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJqb2JzLmxpc3RKb2JFdmVudHMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0Sm9iRXZlbnRzIiwicGF0aCI6Ii92MS9qb2JzL3tqb2JJZH0vZXZlbnRzIiwicmVzb3VyY2UiOiJqb2JzIiwic2VjdGlvbl9zaGEyNTYiOiIzMTg1YzEyNjEyYTA5NjIxODhmMzRmNzFlYmJjZDQ1YWRhMzFjZTQ1NTY4YjdkOTEwZTEwZjJhZDc3N2MxZGExIiwic2lnbmF0dXJlX3NoYTI1NiI6IjRmYTZmMDdmYmExZmY5NDlkOTZmZmMzYTZiZDY4NzRmNjAwZTE1MWNiNTk4YzU2ZTM2Njc2ODg4NTU2NTAwYzYifQ -->
### `client.jobs.listJobEvents`

Operation ID: `listJobEvents`  
Route: `GET` `/v1/jobs/{jobId}/events`  
Equivalent member: `client.listJobEvents`  

#### Signature

```kotlin
suspend fun listJobEvents(params: ListJobEventsParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `jobId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "jobId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.jobs.listJobEvents(jobId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Sm9iRXZlbnRzIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJqb2JzLmxpc3RKb2JzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdEpvYnMiLCJwYXRoIjoiL3YxL2pvYnMiLCJyZXNvdXJjZSI6ImpvYnMiLCJzZWN0aW9uX3NoYTI1NiI6ImY4MDcxNWMzZGJiYmQ2ZTFmZTdhZjNmYzJlYTIzMDRjNDA0ZGE2NTU1OTgyM2QwZjY3Njg5MzY4OGRlNGM1MDUiLCJzaWduYXR1cmVfc2hhMjU2IjoiZjI2YmJjNjUwY2NhNzgzZTc0NmJkZjAzNDFlOTliNzc2MzcxNjRiMmI1MWI1ZGNmYzliMzU2YTgzZmM2ZDc3MSJ9 -->
### `client.jobs.listJobs`

Operation ID: `listJobs`  
Route: `GET` `/v1/jobs`  
Equivalent member: `client.listJobs`  

#### Signature

```kotlin
suspend fun listJobs(params: ListJobsParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Jobs | none |
| `401` | Session required | none |
| `503` | Storage not configured | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.jobs.listJobs()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Sm9icyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJqb2JzLnN1Ym1pdEpvYiIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJzdWJtaXRKb2IiLCJwYXRoIjoiL3YxL2pvYnMiLCJyZXNvdXJjZSI6ImpvYnMiLCJzZWN0aW9uX3NoYTI1NiI6IjNlODA2OTEyN2VkNTE2YTlmOWZkNWQzYWEwMzc3Mjk2OTJjMjRlYmJiM2M1OGVjODBiYjBmZTY3YmE1YWY3N2MiLCJzaWduYXR1cmVfc2hhMjU2IjoiMzVjZWM4ZGY2YTA1YTRjMGViNTJlMDE2NTI3NGIwYzNjYzc0ODYwN2Y0MDMwYzAzYmUxNWQ3MzQxNjBlNmVhMiJ9 -->
### `client.jobs.submitJob`

Operation ID: `submitJob`  
Route: `POST` `/v1/jobs`  
Equivalent member: `client.submitJob`  

#### Signature

```kotlin
suspend fun submitJob(params: SubmitJobParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Replayed | none |
| `201` | Created | none |
| `401` | Session required | none |
| `503` | Storage not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.jobs.submitJob(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdWJtaXRKb2IifQ -->

## Resource `organizations`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmNsb3NlUGVyc2lzdGVudEJveCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjbG9zZVBlcnNpc3RlbnRCb3giLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9wZXJzaXN0ZW50LWJveGVzL3tib3hJZH0vY2xvc2UiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImVkMjkwNGRiMzM0YjAyOWE3Y2Q1ZjMzZTg4ZDVlNjgzZjlkZWMwYjA5NGQyOWM3NDJlMmVkNGZhYWI1ZmQ4ZTEiLCJzaWduYXR1cmVfc2hhMjU2IjoiOWY2OGY4MjkyMzdmNGZiZmZiNjU0NGJjMDE1OGM5YTdlMTM5ZTUyNjQ1NGVlYzI5MzY1NjQ4NGU1MTk2OWFmNCJ9 -->
### `client.organizations.closePersistentBox`

Operation ID: `closePersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/close`  
Equivalent member: `client.closePersistentBox`  

#### Signature

```kotlin
suspend fun closePersistentBox(params: ClosePersistentBoxParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<HostedPersistentBoxClose>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Closure is recorded; repeat requests return the same result without deleting again. | application/json (HostedPersistentBoxClose) |
| `202` | Closure is unconfirmed. Lost, late, negative or mismatched acknowledgements and failed receipt persistence retain reservations. Repeat requests never dispatch another deletion; operator reconciliation is required. | application/json (HostedPersistentBoxClose) |
| `400` | Invalid UUID, body or query parameters. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied cleanup or the organization/product/environment differs. | none |
| `404` | No durable box in this exact target scope. | none |
| `409` | Unconfirmed or changed provider allocation requires operator reconciliation. | none |
| `503` | Authority or storage unavailable, or no matching operator provider adapter. Missing configuration refuses before any close intention or deletion. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-c54d-988d0e4e7e77"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.closePersistentBox(organizationId = "example", boxId = "00000000-0000-0000-c54d-988d0e4e7e77")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjbG9zZVBlcnNpc3RlbnRCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmNyZWF0ZUJpbGxpbmdQb3J0YWwiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoiY3JlYXRlQmlsbGluZ1BvcnRhbCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2JpbGxpbmcvcG9ydGFsIiwicmVzb3VyY2UiOiJvcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiJkMTA4MzY4NTViMDY3YWZlZTAwMWMxMzYzZDI0NjFkMGNhNDU0MTUwZjkwZGQ2ZTgwODZhZGJhNzEyYWEwNTY1Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImRkODAyNzNlMWI1YzNhZDlkNjBmZWNkNDgxMjIxZDQxOTM1NGVmMzhhNTBhM2RjMGYyNDY3NjYyYjRkMTE4YTkifQ -->
### `client.organizations.createBillingPortal`

Operation ID: `createBillingPortal`  
Route: `POST` `/v1/organizations/{organizationId}/billing/portal`  
Equivalent member: `client.createBillingPortal`  

#### Signature

```kotlin
suspend fun createBillingPortal(params: CreateBillingPortalParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | portalUrl | none |
| `404` | No Stripe customer yet | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.createBillingPortal(organizationId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVCaWxsaW5nUG9ydGFsIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmNyZWF0ZUJveCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJjcmVhdGVCb3giLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9ib3hlcyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiNTVmYTQ1MDdiMmFhYTFkMDJkYWE1MTM0Mjc3NTFlMjZiYzVlMTliZmQzNDQxNWZmMzAxOTY3ZjcyM2FlZGUxMiIsInNpZ25hdHVyZV9zaGEyNTYiOiJjZWYyMDYyM2NlNGU1YTZkYjIwNmQ2ZjQyZDdjMGJmN2QyNDEwODQ3MGM5ZTBmMmMwOGU4ZjA1ODNkY2MxY2EyIn0 -->
### `client.organizations.createBox`

Operation ID: `createBox`  
Route: `POST` `/v1/organizations/{organizationId}/boxes`  
Equivalent member: `client.createBox`  

#### Signature

```kotlin
suspend fun createBox(params: CreateBoxParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Box running at the provider | none |
| `402` | Concurrent-box limit reached | none |
| `502` | The provider refused; recorded as failed | none |
| `503` | No provider or no storage | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.createBox(organizationId = "example", body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmNyZWF0ZUNoZWNrb3V0IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNyZWF0ZUNoZWNrb3V0IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vYmlsbGluZy9jaGVja291dCIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiMGU2MTk1ZTBkYjc4NDJiMjExNjc4ODQyYjM4N2U1MmY4ZWZiNWZjOTYzOWMxMGI4ZGI2ZmNiZjU3MjljYjEwYSIsInNpZ25hdHVyZV9zaGEyNTYiOiI2ZmNjOTg3YTJjNTJmZDFkNThjMjUwMDg1NjYyYzE4MDRkZTIyNzg0NDBjOGRkMzZkNmRhOWQwZjYwZDc4MWE3In0 -->
### `client.organizations.createCheckout`

Operation ID: `createCheckout`  
Route: `POST` `/v1/organizations/{organizationId}/billing/checkout`  
Equivalent member: `client.createCheckout`  

#### Signature

```kotlin
suspend fun createCheckout(params: CreateCheckoutParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | checkoutUrl of the Stripe Checkout Session | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. Autonomous mode: Plan not on sale or subscription exists | none |

#### Canonical required-input example

```json
{
  "body": {
    "planKey": "pro"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.createCheckout(organizationId = "example", body = {"planKey": "pro"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjcmVhdGVDaGVja291dCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldEJpbGxpbmciLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRCaWxsaW5nIiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vYmlsbGluZyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiNjUyMGY3YzViNjQ1YTU2NjViYzljMmE5ODYyNmJjYmFjZTQ4Zjk0MDYzOWNmYjdkNGNhZDA5MzllYTVkZDBjMyIsInNpZ25hdHVyZV9zaGEyNTYiOiJiODRlZDgxNTU3OWRlYmE1NWY2OGNiMzA2ZmU4NDJlZmNlMDcwNjEyZDU2NmUzYmY2NDhjYjM0YjY3MjEyMDZhIn0 -->
### `client.organizations.getBilling`

Operation ID: `getBilling`  
Route: `GET` `/v1/organizations/{organizationId}/billing`  
Equivalent member: `client.getBilling`  

#### Signature

```kotlin
suspend fun getBilling(params: GetBillingParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Billing status | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.getBilling(organizationId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRCaWxsaW5nIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldEJveCIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEJveCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2JveGVzL3tib3hJZH0iLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImIwMjUwNDJmMjRkMzM2YzdiNjI3N2Q3Y2U1NTdjMDI0YmI5M2Q4YjU4ZjhlN2JkZjRkMWYzODhhOWQ1M2UzYTYiLCJzaWduYXR1cmVfc2hhMjU2IjoiNGY4Y2FmYzAyODY1NzQ3OGM5OGQ5NmE5YWYxNWM5N2JjMjE4OWFjZjc0NGU3Mjg1MmMzMTYxMjk2OGZlNTIxZSJ9 -->
### `client.organizations.getBox`

Operation ID: `getBox`  
Route: `GET` `/v1/organizations/{organizationId}/boxes/{boxId}`  
Equivalent member: `client.getBox`  

#### Signature

```kotlin
suspend fun getBox(params: GetBoxParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored box | none |
| `404` | Unknown box | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-d32a-0e84cb70d88a"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.getBox(organizationId = "example", boxId = "00000000-0000-0000-d32a-0e84cb70d88a")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldEVudGl0bGVtZW50cyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEVudGl0bGVtZW50cyIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2VudGl0bGVtZW50cyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiZmViNTNjYzc4ZWIyOWI0YzRlZjFmYmFmOWVlMGFlOGQyYWZjYjgyZTExYTc0NGZkNzJlNzNkN2VjYzZhYjJmZSIsInNpZ25hdHVyZV9zaGEyNTYiOiI4Y2FmNWYwNTkzNzQyNGZmMTA4MDU1NjFkNjA4NDg4NWJkYjY3ZjllNTgzYmJkNDFiNGEyMTM3YzcxZWQzN2ExIn0 -->
### `client.organizations.getEntitlements`

Operation ID: `getEntitlements`  
Route: `GET` `/v1/organizations/{organizationId}/entitlements`  
Equivalent member: `client.getEntitlements`  

#### Signature

```kotlin
suspend fun getEntitlements(params: GetEntitlementsParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Entitlements and usage | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.getEntitlements(organizationId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRFbnRpdGxlbWVudHMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldEZsZWV0IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0RmxlZXQiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9mbGVldCIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiNWY0Nzg2MzllODgzNTM1ODdkMTU1YTM4NzY1YWNiYzVmM2QzMzVlNzRmYjFjNzcxOTRhNGZmNmM5MDU5YTdkYiIsInNpZ25hdHVyZV9zaGEyNTYiOiI2OTFjNGIyNDlkZTc4YjFhMzdiMzQ1ODI5OWIyYjM0YWVjZjA3OWIzNmI3MDA0NmUwZGM2Y2JlZTc0MjBjYjc0In0 -->
### `client.organizations.getFleet`

Operation ID: `getFleet`  
Route: `GET` `/v1/organizations/{organizationId}/fleet`  
Equivalent member: `client.getFleet`  

#### Signature

```kotlin
suspend fun getFleet(params: GetFleetParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored fleet | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.getFleet(organizationId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRGbGVldCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldEZsZWV0UG9saWN5IiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0RmxlZXRQb2xpY3kiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9mbGVldC9wb2xpY3kiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImZmOWIyM2MyN2Y4ZDlmYmI3ZmU5MTIzYmQwMzRkNmNhNDNlMDA2NmJhYmFlOTc2MTA0NjBiYWIxNGY1YWY3YWUiLCJzaWduYXR1cmVfc2hhMjU2IjoiZmVlOTQ4OGI1NjA4OGIzODlmNTFiNGY5MWZhNjY5NTNmZGQxYjU2MjA2NTNhMzQ3MzUxOTM5Nzk4ODRiYmNjNyJ9 -->
### `client.organizations.getFleetPolicy`

Operation ID: `getFleetPolicy`  
Route: `GET` `/v1/organizations/{organizationId}/fleet/policy`  
Equivalent member: `client.getFleetPolicy`  

#### Signature

```kotlin
suspend fun getFleetPolicy(params: GetFleetPolicyParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Effective policy | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.getFleetPolicy(organizationId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRGbGVldFBvbGljeSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldFBlcnNpc3RlbnRCb3giLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJnZXRQZXJzaXN0ZW50Qm94IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vcGVyc2lzdGVudC1ib3hlcy97Ym94SWR9IiwicmVzb3VyY2UiOiJvcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiI4N2YxNjljNmQ0Y2Y3NzA3ZjMxZGI5YWY2ZTZhNjczNDA3MTIyZDYzMTIxNWQxNmRiNTRhNWQxNzUwY2I1YWE5Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjBkY2NhZDZhMTRlOGM5MGJiYzc3YTQwOTczODBhZmQyOGJjMDlhODkxYTYzMDRlMmU3ODE2OTVlMGY4YWE1N2UifQ -->
### `client.organizations.getPersistentBox`

Operation ID: `getPersistentBox`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}`  
Equivalent member: `client.getPersistentBox`  

#### Signature

```kotlin
suspend fun getPersistentBox(params: GetPersistentBoxParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Private stored record and reserved budget; runtime status is not-metered. | application/json (object) |
| `400` | Invalid UUID or query parameters. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied access or the organization/product/environment differs. | none |
| `404` | No durable box in this exact target scope. | none |
| `503` | Authority or durable record storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-098c-d4f2b24057fb"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.getPersistentBox(organizationId = "example", boxId = "00000000-0000-0000-098c-d4f2b24057fb")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQZXJzaXN0ZW50Qm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmdldFBlcnNpc3RlbnRCb3hQcm92aWRlclVzYWdlIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoiZ2V0UGVyc2lzdGVudEJveFByb3ZpZGVyVXNhZ2UiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9wZXJzaXN0ZW50LWJveGVzL3tib3hJZH0vdXNhZ2UiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImVhZjk0Nzk4ODFmYjc2ODA2NDNkMWRjZDE1NGFjYTNjNDg0OGRkMWQzZTc1NGU0ZGYyYTY4NmFhMDRlODI1MmUiLCJzaWduYXR1cmVfc2hhMjU2IjoiOWU1Mzg5MzRlMWJkNDU0ZmI2MGY1MTEyODgxZGUxMTVjMzA5MzlmY2I5MmIwYzRmMjYzYzdhYmFiNmNhM2E2MyJ9 -->
### `client.organizations.getPersistentBoxProviderUsage`

Operation ID: `getPersistentBoxProviderUsage`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/usage`  
Equivalent member: `client.getPersistentBoxProviderUsage`  

#### Signature

```kotlin
suspend fun getPersistentBoxProviderUsage(params: GetPersistentBoxProviderUsageParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `from` | `query` | yes | `string&lt;date-time&gt;` |  |
| `to` | `query` | yes | `string&lt;date-time&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Private provider evidence summary with explicit interval coverage. | application/json (object) |
| `400` | Invalid box ID or bounded UTC window. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied access or target scope differs. | none |
| `404` | No durable box in this exact target scope. | none |
| `413` | Stored evidence exceeds the per-read record bound; select a smaller window. | none |
| `503` | Authority or usage storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-0848-7a89fcbe4ab4"
    },
    {
      "in": "query",
      "name": "from",
      "value": "2026-01-01T00:00:00Z"
    },
    {
      "in": "query",
      "name": "to",
      "value": "2026-01-01T00:00:27Z"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.getPersistentBoxProviderUsage(organizationId = "example", boxId = "00000000-0000-0000-0848-7a89fcbe4ab4", from = "2026-01-01T00:00:00Z", to = "2026-01-01T00:00:27Z")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQZXJzaXN0ZW50Qm94UHJvdmlkZXJVc2FnZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RCb3hlcyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RCb3hlcyIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2JveGVzIiwicmVzb3VyY2UiOiJvcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiJiYjQ0Y2JjMGZmODIzMTE0YWFmYjA4M2IzYjdjZmFmNWI0OTU2NWRkNDhkNmEzYmFiZDVlY2U3YTgyMDM0MWQ1Iiwic2lnbmF0dXJlX3NoYTI1NiI6IjAxMmU2Y2I3YjQ0YjdjYTdkNDk1NDJjY2VmNTk0ZjIzYTZhYmM0ODE5NTYzYzgyZDQ2ZGM4NGRjOWMxMzhlMmIifQ -->
### `client.organizations.listBoxes`

Operation ID: `listBoxes`  
Route: `GET` `/v1/organizations/{organizationId}/boxes`  
Equivalent member: `client.listBoxes`  

#### Signature

```kotlin
suspend fun listBoxes(params: ListBoxesParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored boxes with their provider state | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.listBoxes(organizationId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0Qm94ZXMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RJbnZvaWNlcyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6Imxpc3RJbnZvaWNlcyIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L2JpbGxpbmcvaW52b2ljZXMiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImExNDA3ZWM1NjQwYWI1Mjc2NmQ1NTBhZDFjMzRhMmE4ZGQ5ZTFiNTdhYTJhZGQ5NGI3ZDljMTBjNGUzY2NjYTciLCJzaWduYXR1cmVfc2hhMjU2IjoiNGE2Y2E3MjFjMDkwYzc3YTUzYjYwNTg4NjE3YTAwODkwNjY3YWJmMDI4NjdkYTliODlkNGM4YzdlMWMyZWQzZiJ9 -->
### `client.organizations.listInvoices`

Operation ID: `listInvoices`  
Route: `GET` `/v1/organizations/{organizationId}/billing/invoices`  
Equivalent member: `client.listInvoices`  

#### Signature

```kotlin
suspend fun listInvoices(params: ListInvoicesParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Invoices | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.listInvoices(organizationId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0SW52b2ljZXMifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RNZW1iZXJzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdE1lbWJlcnMiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9tZW1iZXJzIiwicmVzb3VyY2UiOiJvcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiIyMTY2M2RlNDA1OTc4OTFjN2ZlMThlOWFhZTk1MzUyZjhjMjQxNmZiOTc1OGFjOTc0NTg2NTRiMWQ0ZDczMjgyIiwic2lnbmF0dXJlX3NoYTI1NiI6IjgyNzRhM2JmZWJiOTRhNWE5ODMzN2IyZDBhZWI0OGIwMWQ0ZjBhZTVmNDYwZjVjYjA3MDdkZWUyZjc3NzU2ZjQifQ -->
### `client.organizations.listMembers`

Operation ID: `listMembers`  
Route: `GET` `/v1/organizations/{organizationId}/members`  
Equivalent member: `client.listMembers`  

#### Signature

```kotlin
suspend fun listMembers(params: ListMembersParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored members and the plan seat limit | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.listMembers(organizationId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0TWVtYmVycyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RPYnNlcnZlZEJveGVzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdE9ic2VydmVkQm94ZXMiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9vYnNlcnZlZC1ib3hlcyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiZDA1Njk5OTk3MGE4MGRhMGE2ODgyMjMyZmU4ZGVhYTRhYjgyNWRkYTg5NmYyZjgyYjk4NTBmYTU5OWRjMmMwZiIsInNpZ25hdHVyZV9zaGEyNTYiOiI3MzdjOTgxN2U3Y2JhNjVkNzdhNGNlMWNhZjAwMmJmZDk0ZTc0ZGI2ZGNkOTY2NWRhZTQ0ODUyZjQyZWYyZDg1In0 -->
### `client.organizations.listObservedBoxes`

Operation ID: `listObservedBoxes`  
Route: `GET` `/v1/organizations/{organizationId}/observed-boxes`  
Equivalent member: `client.listObservedBoxes`  

#### Signature

```kotlin
suspend fun listObservedBoxes(params: ListObservedBoxesParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Up to 100 non-expired client snapshots, private and not cacheable. | application/json (object) |
| `401` | No valid product session. | none |
| `403` | Organization or scope denied. | none |
| `503` | Inventory storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.listObservedBoxes(organizationId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0T2JzZXJ2ZWRCb3hlcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RQZXJzaXN0ZW50Qm94T2ZmZXJzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdFBlcnNpc3RlbnRCb3hPZmZlcnMiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9wZXJzaXN0ZW50LWJveGVzL29mZmVycyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiNzY5YTNhYzk1NWZkNDZjZjMxMjI0OTgyYTFlOTJkZjNiZGVmOWRlY2U4ZTExZTcyMTExN2Y2MzVkNjM2NjE1OCIsInNpZ25hdHVyZV9zaGEyNTYiOiIyOTMzMzgxZDMwODQ5ZWJlM2M3ZjlkMTc0MDY1ODlhYjEyYjBmOGE1YjgxOGRmZDI4YWI1NWVjNmJkMWVhY2M4In0 -->
### `client.organizations.listPersistentBoxOffers`

Operation ID: `listPersistentBoxOffers`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes/offers`  
Equivalent member: `client.listPersistentBoxOffers`  

#### Signature

```kotlin
suspend fun listPersistentBoxOffers(params: ListPersistentBoxOffersParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Private configured offers. | application/json (object) |
| `401` | Product session required. | none |
| `403` | Current read authority denied. | none |
| `503` | Storage or operator offer configuration unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.listPersistentBoxOffers(organizationId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0UGVyc2lzdGVudEJveE9mZmVycyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLmxpc3RQZXJzaXN0ZW50Qm94ZXMiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0UGVyc2lzdGVudEJveGVzIiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vcGVyc2lzdGVudC1ib3hlcyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiMjhjYTYzYTA2NTJmNjQ1ZTY0YTIyYmQzYjE2NjZmMTQ3M2FjNDhhODBiYzYzOTg2YjBiMzU1NjljZDg1NTk2YSIsInNpZ25hdHVyZV9zaGEyNTYiOiJkMTQ1ZmRmN2U5MWE2Mzg1MWNmMDdkOGFhMmNlMzY2ZjBjNDZmNzY1ZWI5MjExZmFiZWJlMjUxMjAyZWFkZmM4In0 -->
### `client.organizations.listPersistentBoxes`

Operation ID: `listPersistentBoxes`  
Route: `GET` `/v1/organizations/{organizationId}/persistent-boxes`  
Equivalent member: `client.listPersistentBoxes`  

#### Signature

```kotlin
suspend fun listPersistentBoxes(params: ListPersistentBoxesParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `limit` | `query` | no | `integer` | Maximum recent records; duplicates and other query parameters are rejected. |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Bounded stored records, private and not cacheable. limitReached indicates the requested bound was filled, not an exact total or proof that more records exist. | application/json (object) |
| `400` | Invalid query parameters. | none |
| `401` | Missing or rejected product session. | none |
| `403` | Current authority denied access or the organization/product/environment differs. | none |
| `503` | Authority or durable record storage unavailable. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.listPersistentBoxes(organizationId = "example", /* optional: limit */)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0UGVyc2lzdGVudEJveGVzIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnByb3Zpc2lvblBlcnNpc3RlbnRCb3giLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicHJvdmlzaW9uUGVyc2lzdGVudEJveCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L3BlcnNpc3RlbnQtYm94ZXMiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImMzYTcyODE5NmYwZDQwNTU4ZDAwMzZlZjQyNmE4ZjgwMWIxZTE3ZGIzZjk4ZDE0MzVkNGFkZmIxMDZkMjExYmMiLCJzaWduYXR1cmVfc2hhMjU2IjoiN2Y5MWRhNDY5YzliOTNiNjUzOGMzM2ZmNDA5NDY1YjE3MzQ1MGM2YmQyMGU4OWVlMjlhM2Y0OTY2M2U5Mzc3NCJ9 -->
### `client.organizations.provisionPersistentBox`

Operation ID: `provisionPersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes`  
Equivalent member: `client.provisionPersistentBox`  

#### Signature

```kotlin
suspend fun provisionPersistentBox(params: ProvisionPersistentBoxParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `Idempotency-Key` | `header` | no | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Previously recorded running or closed allocation; replayed is true. | none |
| `201` | Provider allocation confirmed and recorded as running. Runtime remains reserved, not measured. | application/json (object) |
| `202` | The reservation is held and the allocation remains unconfirmed. Repeated requests never dispatch create again; operator reconciliation is required. | none |
| `400` | Invalid body, unsupported fields, query parameters or idempotency key. | none |
| `401` | Missing or rejected product session. | none |
| `402` | Missing durable entitlement, bounded allowance or available capacity. | none |
| `403` | Current authority denied the operation or target scope. | none |
| `409` | Idempotency conflict, unresolved prior budget or UTC month boundary. | none |
| `413` | Request body exceeds 4 KiB. | none |
| `503` | Authority, storage, operator offer or independent runtime enforcement unavailable. Missing configuration is refused before reservation. | none |

#### Canonical required-input example

```json
{
  "body": {
    "offer": "example",
    "reserveMinutes": 1
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.provisionPersistentBox(organizationId = "example", body = {"offer": "example", "reserveMinutes": 1}, /* optional: Idempotency-Key */)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwcm92aXNpb25QZXJzaXN0ZW50Qm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnB1dEZsZWV0UG9saWN5IiwibWV0aG9kIjoiUFVUIiwib3BlcmF0aW9uX2lkIjoicHV0RmxlZXRQb2xpY3kiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9mbGVldC9wb2xpY3kiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6ImQ1NDRiZWI0MmEwNmFjOTgwYWZkZjFmYTM2OWJmYTk4YTgxZDBhZWU5MzYyZTc5NmFlZjIxY2E4ZDVmMzNhYzYiLCJzaWduYXR1cmVfc2hhMjU2IjoiNGJlNjAxNzEwNTE0NzBiNGNiZWZkNzVhOTgwMmE2YjA4Mjc4Mjc5NjRmODQ2YzU5OTM0YzkzZGFjYWU3MDg3MSJ9 -->
### `client.organizations.putFleetPolicy`

Operation ID: `putFleetPolicy`  
Route: `PUT` `/v1/organizations/{organizationId}/fleet/policy`  
Equivalent member: `client.putFleetPolicy`  

#### Signature

```kotlin
suspend fun putFleetPolicy(params: PutFleetPolicyParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stored policy | none |
| `400` | Invalid or unenforced field | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.putFleetPolicy(organizationId = "example", body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJwdXRGbGVldFBvbGljeSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnJlY29uY2lsZVBlcnNpc3RlbnRCb3giLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicmVjb25jaWxlUGVyc2lzdGVudEJveCIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L3BlcnNpc3RlbnQtYm94ZXMve2JveElkfS9yZWNvbmNpbGUiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjE3OWE2YmRkNDM3MjQzNGZiNzBhYjdlZWQ1YzMyNTE3OGNhOGMxM2FhODljMDQ3MzI1MTU0MDAxMjMzMWU3MzkiLCJzaWduYXR1cmVfc2hhMjU2IjoiOTkzM2Q4ZDA3MTYzYzcxYzcxNTFjNGQ4MDVlM2FlZmQyZDM3ZDQ3MzE0M2Y0Zjc4ZjQwMjAzNDg5YmZkMmU0OSJ9 -->
### `client.organizations.reconcilePersistentBox`

Operation ID: `reconcilePersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/reconcile`  
Equivalent member: `client.reconcilePersistentBox`  

#### Signature

```kotlin
suspend fun reconcilePersistentBox(params: ReconcilePersistentBoxParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Confirmed operation or replayed receipt. | application/json (object) |
| `202` | Operation remains unconfirmed; reconcile its operation ID without repeating the mutation. | application/json (object) |
| `400` | Invalid bounded lifecycle request. | none |
| `401` | Product session required. | none |
| `402` | Durable feature or quota denied. | none |
| `403` | Fresh operation authority denied. | none |
| `404` | Box or operation missing in the exact organization and deployment. | none |
| `409` | Conflicting operation, unresolved evidence or unavailable runtime budget. | none |
| `503` | Authority, storage or matching operator adapter unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {
    "operationId": "00000000-0000-0000-f735-3d332872b96e"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-a264-3ce9cdfbbeff"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.reconcilePersistentBox(organizationId = "example", boxId = "00000000-0000-0000-a264-3ce9cdfbbeff", body = {"operationId": "00000000-0000-0000-f735-3d332872b96e"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWNvbmNpbGVQZXJzaXN0ZW50Qm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnJlbW92ZU1lbWJlciIsIm1ldGhvZCI6IkRFTEVURSIsIm9wZXJhdGlvbl9pZCI6InJlbW92ZU1lbWJlciIsInBhdGgiOiIvdjEvb3JnYW5pemF0aW9ucy97b3JnYW5pemF0aW9uSWR9L21lbWJlcnMve3VzZXJJZH0iLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjBkNjcxM2U3N2M3NjUyZmFlMWEyYzQ0ZWI1NzA0ZmZlZjZjMjJlNmY2MzI5YmRhODFiMjE3MTM2NWZjYTNhMGQiLCJzaWduYXR1cmVfc2hhMjU2IjoiZjhjZDcxYWI3ZTU0NWFjZWY3NGY4NmJhMjhlNDM1Zjk4OTEyZDI3Y2Y3NzM3MmFjNGZlODUxNDYwZmQ3ZmQ1NSJ9 -->
### `client.organizations.removeMember`

Operation ID: `removeMember`  
Route: `DELETE` `/v1/organizations/{organizationId}/members/{userId}`  
Equivalent member: `client.removeMember`  

#### Signature

```kotlin
suspend fun removeMember(params: RemoveMemberParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `userId` | `path` | yes | `string` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Removed | none |
| `404` | Unknown member | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "userId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.removeMember(organizationId = "example", userId = "example")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZW1vdmVNZW1iZXIifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnN0YXJ0UGVyc2lzdGVudEJveCIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJzdGFydFBlcnNpc3RlbnRCb3giLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9wZXJzaXN0ZW50LWJveGVzL3tib3hJZH0vc3RhcnQiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6Ijk2YzEyNTQzNTMxOGQyNDdkN2VmMjAyNmY3MDUxMTA1Zjg1ZGYwZjZlMmJjMGY1NzQ4OWZiYjYwMzRhNGM2MmUiLCJzaWduYXR1cmVfc2hhMjU2IjoiYWZjNWZiNDA4N2M2ZmQxOTBhODA5MDE1OWNiMTY3ZGM5OTEwNTA3YjhhZTMwNzEzNTBhNmUxNmM4ZjU3MmM1YiJ9 -->
### `client.organizations.startPersistentBox`

Operation ID: `startPersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/start`  
Equivalent member: `client.startPersistentBox`  

#### Signature

```kotlin
suspend fun startPersistentBox(params: StartPersistentBoxParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `Idempotency-Key` | `header` | no | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Confirmed operation or replayed receipt. | application/json (object) |
| `202` | Operation remains unconfirmed; reconcile its operation ID without repeating the mutation. | application/json (object) |
| `400` | Invalid bounded lifecycle request. | none |
| `401` | Product session required. | none |
| `402` | Durable feature or quota denied. | none |
| `403` | Fresh operation authority denied. | none |
| `404` | Box or operation missing in the exact organization and deployment. | none |
| `409` | Conflicting operation, unresolved evidence or unavailable runtime budget. | none |
| `503` | Authority, storage or matching operator adapter unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {
    "reserveMinutes": 1
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-d7e8-d81c5e30ed9a"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.startPersistentBox(organizationId = "example", boxId = "00000000-0000-0000-d7e8-d81c5e30ed9a", body = {"reserveMinutes": 1}, /* optional: Idempotency-Key */)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdGFydFBlcnNpc3RlbnRCb3gifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnN0b3BCb3giLCJtZXRob2QiOiJERUxFVEUiLCJvcGVyYXRpb25faWQiOiJzdG9wQm94IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vYm94ZXMve2JveElkfSIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiNWFiYjY1NjRlNmU0YmVlM2Y1MjVjMWZmMWM5Zjc1ZGIzZmFmYTA5YzMxNWM0NTEyZDE3MDM3NGZiNGI4ZDJhOCIsInNpZ25hdHVyZV9zaGEyNTYiOiJlYmU4NzgzOTg5NzE5NGZlYTBlZTA0YjkwYWY2MDEwZjIzZGVjMTA2NTZmZTNlNDNhZDAyYmY2YzAxN2Q3Y2UxIn0 -->
### `client.organizations.stopBox`

Operation ID: `stopBox`  
Route: `DELETE` `/v1/organizations/{organizationId}/boxes/{boxId}`  
Equivalent member: `client.stopBox`  

#### Signature

```kotlin
suspend fun stopBox(params: StopBoxParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Stopped | none |
| `502` | The provider refused; state unchanged | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-265e-7c895c60153e"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.stopBox(organizationId = "example", boxId = "00000000-0000-0000-265e-7c895c60153e")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdG9wQm94In0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnN0b3BQZXJzaXN0ZW50Qm94IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InN0b3BQZXJzaXN0ZW50Qm94IiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vcGVyc2lzdGVudC1ib3hlcy97Ym94SWR9L3N0b3AiLCJyZXNvdXJjZSI6Im9yZ2FuaXphdGlvbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjBiNmM1MjJkMjI3ODIwNDYyNjlhMDNiMTQzZTVjZmM4MTZmNDc2Y2NhMzE4ZTRjYjhhOTA5MmJhMDQ2MDVkY2MiLCJzaWduYXR1cmVfc2hhMjU2IjoiNWRjNDczMzEzZTY4ZTE4YzgxOTYxZjZmNGZmYTgxZjRkMzg2M2MyN2Y4YjAwMWM1NjUwM2U0YzkzNTQzZTZlZiJ9 -->
### `client.organizations.stopPersistentBox`

Operation ID: `stopPersistentBox`  
Route: `POST` `/v1/organizations/{organizationId}/persistent-boxes/{boxId}/stop`  
Equivalent member: `client.stopPersistentBox`  

#### Signature

```kotlin
suspend fun stopPersistentBox(params: StopPersistentBoxParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `boxId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `Idempotency-Key` | `header` | no | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Confirmed operation or replayed receipt. | application/json (object) |
| `202` | Operation remains unconfirmed; reconcile its operation ID without repeating the mutation. | application/json (object) |
| `400` | Invalid bounded lifecycle request. | none |
| `401` | Product session required. | none |
| `402` | Durable feature or quota denied. | none |
| `403` | Fresh operation authority denied. | none |
| `404` | Box or operation missing in the exact organization and deployment. | none |
| `409` | Conflicting operation, unresolved evidence or unavailable runtime budget. | none |
| `503` | Authority, storage or matching operator adapter unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    },
    {
      "in": "path",
      "name": "boxId",
      "value": "00000000-0000-0000-978f-a93165cf6579"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.stopPersistentBox(organizationId = "example", boxId = "00000000-0000-0000-978f-a93165cf6579", body = {}, /* optional: Idempotency-Key */)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzdG9wUGVyc2lzdGVudEJveCJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnN5bmNPYnNlcnZlZEJveGVzIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InN5bmNPYnNlcnZlZEJveGVzIiwicGF0aCI6Ii92MS9vcmdhbml6YXRpb25zL3tvcmdhbml6YXRpb25JZH0vb2JzZXJ2ZWQtYm94ZXMvc3luYyIsInJlc291cmNlIjoib3JnYW5pemF0aW9ucyIsInNlY3Rpb25fc2hhMjU2IjoiNTA2NWM1NjE1MDdiYzVlZjc4MzljMGY5YTFlMjVhYjkxOThiNTA4MzFmNmRiMDUwMzIzOGQxNWNlZDBjMzliYiIsInNpZ25hdHVyZV9zaGEyNTYiOiI2ZGE3NjMyMzRhNzlkODNlYTUzMDViOWY4MmZiOGY2MjIwMGJmYjQ0OTMyMmQyZWYzNTA0MmQ5NTA5MzVmODhjIn0 -->
### `client.organizations.syncObservedBoxes`

Operation ID: `syncObservedBoxes`  
Route: `POST` `/v1/organizations/{organizationId}/observed-boxes/sync`  
Equivalent member: `client.syncObservedBoxes`  

#### Signature

```kotlin
suspend fun syncObservedBoxes(params: SyncObservedBoxesParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Map<String, Any?>>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Snapshot accepted; private and not cacheable. | application/json (object) |
| `400` | Invalid observation snapshot. | none |
| `401` | No valid product session. | none |
| `403` | Organization or scope denied. | none |
| `413` | Snapshot exceeds 64 KiB. | none |
| `503` | Inventory storage unavailable. | none |

#### Canonical required-input example

```json
{
  "body": {
    "boxes": [
      {
        "boxId": "example",
        "kind": "provider-list",
        "provider": "example",
        "state": "running"
      }
    ],
    "sourceId": "00000000-0000-0000-ae61-93cfab8e5e4b"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.syncObservedBoxes(organizationId = "example", body = {"boxes": [{"boxId": "example", "kind": "provider-list", "provider": "example", "state": "running"}], "sourceId": "00000000-0000-0000-ae61-93cfab8e5e4b"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJzeW5jT2JzZXJ2ZWRCb3hlcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJvcmdhbml6YXRpb25zLnVwc2VydE1lbWJlciIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJ1cHNlcnRNZW1iZXIiLCJwYXRoIjoiL3YxL29yZ2FuaXphdGlvbnMve29yZ2FuaXphdGlvbklkfS9tZW1iZXJzIiwicmVzb3VyY2UiOiJvcmdhbml6YXRpb25zIiwic2VjdGlvbl9zaGEyNTYiOiIwNTg1NGY5NmIyY2QwN2E0NDE1NDFjYTI1YjhjYjU5ZjYyMDRmODMyNGI0OTRmZGMwODdiNzhjMjJkN2ZkNGIzIiwic2lnbmF0dXJlX3NoYTI1NiI6IjUxZjlmOTQxNDkwYTU1YTg5ZTI4ZGM5MmU4MDFiOWI2ODE5NTYxNjIyNTY1N2NmNzk4NjRkMmU1YTliYTE4NzIifQ -->
### `client.organizations.upsertMember`

Operation ID: `upsertMember`  
Route: `POST` `/v1/organizations/{organizationId}/members`  
Equivalent member: `client.upsertMember`  

#### Signature

```kotlin
suspend fun upsertMember(params: UpsertMemberParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `organizationId` | `path` | yes | `string` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Member updated | none |
| `201` | Member added | none |
| `402` | Seat limit reached or entitlement missing | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "body": {
    "email": "example-f35c@example.test",
    "role": "owner"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "organizationId",
      "value": "example"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.organizations.upsertMember(organizationId = "example", body = {"email": "example-f35c@example.test", "role": "owner"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJ1cHNlcnRNZW1iZXIifQ -->

## Resource `plans`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJwbGFucy5nZXRQbGFucyIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldFBsYW5zIiwicGF0aCI6Ii92MS9wbGFucyIsInJlc291cmNlIjoicGxhbnMiLCJzZWN0aW9uX3NoYTI1NiI6IjU4ZWIwMzliNmIxY2RlYzNlOTU1YjA0NDNlYTA5MjZlYjE3ZTY4MDY5YmUwYzI0NjVmZmM2ZGRmZjM0ZjlmMmUiLCJzaWduYXR1cmVfc2hhMjU2IjoiNmVjMDc3OTk3MzVmYjJiN2U4Mjg1NzE3ZjQzNzNlNzQ4MzMyZmZlNmZkOGJmMzdmZTVhZWRlOGMwYWFiMjcxZSJ9 -->
### `client.plans.getPlans`

Operation ID: `getPlans`  
Route: `GET` `/v1/plans`  
Equivalent member: `client.getPlans`  

#### Signature

```kotlin
suspend fun getPlans(params: GetPlansParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | OK | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.plans.getPlans()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRQbGFucyJ9 -->

## Resource `telemetry`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ0ZWxlbWV0cnkuaW5nZXN0VGVsZW1ldHJ5IiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImluZ2VzdFRlbGVtZXRyeSIsInBhdGgiOiIvdjEvdGVsZW1ldHJ5L2luZ2VzdCIsInJlc291cmNlIjoidGVsZW1ldHJ5Iiwic2VjdGlvbl9zaGEyNTYiOiIwYjQ2Y2Y3NjUxNmFhY2Y3Y2I4YmFmY2NkMGY2ZmI2OTk5MzFiYTE4MzczYzZiYTAwYTA4MGNmNWZhZDI1NDY3Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImI5ZmE5MzAxN2IxYzk3MDRiNWZmOWFmODA0MjU3NjUwNjg3ZGJmZWQ5YmZkMDBjMDJmNzU4NjdhNGEwNmUwMzEifQ -->
### `client.telemetry.ingestTelemetry`

Operation ID: `ingestTelemetry`  
Route: `POST` `/v1/telemetry/ingest`  
Equivalent member: `client.ingestTelemetry`  

#### Signature

```kotlin
suspend fun ingestTelemetry(params: IngestTelemetryParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `201` | Stored | none |
| `400` | Invalid event | none |
| `401` | License required | none |
| `409` | Managed account authority required; use the returned JackAISaaS accountUrl or portalUrl. | none |
| `413` | Body too large | none |
| `503` | Ingestion not configured | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.telemetry.ingestTelemetry(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJpbmdlc3RUZWxlbWV0cnkifQ -->

## Resource `waitlist`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5saXN0V2FpdGxpc3QiLCJtZXRob2QiOiJHRVQiLCJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QiLCJwYXRoIjoiL3YxL3dhaXRsaXN0IiwicmVzb3VyY2UiOiJ3YWl0bGlzdCIsInNlY3Rpb25fc2hhMjU2IjoiM2M4ZGFmYmZjZWJjNTRhZWRhYmRjMDA4ZDM3NWJmNjZiZDc0NWRiYWYxMjA2MzgzNzJmZGVkZWNjNWVjMzI1YyIsInNpZ25hdHVyZV9zaGEyNTYiOiI3MGRjZTZlMTQ3NzU2ZTIzYTYwYTZlZmVkYzJhYjgyODJjYzQ5YTU1YjBjMGU5ODQyZDkwOThiNDhlOGE3ZDE2In0 -->
### `client.waitlist.listWaitlist`

Operation ID: `listWaitlist`  
Route: `GET` `/v1/waitlist`  
Equivalent member: `client.listWaitlist`  

#### Signature

```kotlin
suspend fun listWaitlist(params: ListWaitlistParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Requests | none |
| `401` | Admin token required | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.waitlist.listWaitlist()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0V2FpdGxpc3QifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3YWl0bGlzdC5yZXF1ZXN0QWNjZXNzIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6InJlcXVlc3RBY2Nlc3MiLCJwYXRoIjoiL3YxL3dhaXRsaXN0IiwicmVzb3VyY2UiOiJ3YWl0bGlzdCIsInNlY3Rpb25fc2hhMjU2IjoiNDRmODM0ZDgwMjIwOGIxZTMwNGYzMjg0NDgzNmM0NTcxOGMyZmQ2YzkzNGZkMWQ2NzVjNWRiMTAxZmE4MGNhNyIsInNpZ25hdHVyZV9zaGEyNTYiOiJmZTQxOTg3N2I2OTZmNTZlMTZmMmMyZjNiNGFhYzlhNTk4NTVlMThjNzBkMTE5YWIzZTc2MDBlN2NjOTI0ZWUxIn0 -->
### `client.waitlist.requestAccess`

Operation ID: `requestAccess`  
Route: `POST` `/v1/waitlist`  
Equivalent member: `client.requestAccess`  

#### Signature

```kotlin
suspend fun requestAccess(params: RequestAccessParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `202` | Received | none |
| `400` | Invalid email | none |
| `413` | Body too large | none |
| `429` | Rate limited | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.waitlist.requestAccess(body = {})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZXF1ZXN0QWNjZXNzIn0 -->

## Resource `workspaces`

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLmNsb3NlSG9zdGVkV29ya3NwYWNlIiwibWV0aG9kIjoiUE9TVCIsIm9wZXJhdGlvbl9pZCI6ImNsb3NlSG9zdGVkV29ya3NwYWNlIiwicGF0aCI6Ii92MS93b3Jrc3BhY2VzL3t3b3Jrc3BhY2VJZH0vY2xvc2UiLCJyZXNvdXJjZSI6IndvcmtzcGFjZXMiLCJzZWN0aW9uX3NoYTI1NiI6ImVkNWJlNGE3MTYzM2ZhNGQ1MjRiYWUyZmExNWY2YTFmZGM2NmYzNDIwYTM5MzI3ZGNmYzU4ZmRhNzk5NmJjNjUiLCJzaWduYXR1cmVfc2hhMjU2IjoiZGUxNTNjOWIwMTU0ODE5MGVmMTkxODQwZGMyMTUxYmFhZjIzMTI3MjhiYTA5N2QzYzJhYWQzODU3NzM2MWU2ZCJ9 -->
### `client.workspaces.closeHostedWorkspace`

Operation ID: `closeHostedWorkspace`  
Route: `POST` `/v1/workspaces/{workspaceId}/close`  
Equivalent member: `client.closeHostedWorkspace`  

#### Signature

```kotlin
suspend fun closeHostedWorkspace(params: CloseHostedWorkspaceParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-6658-e129a559a4dd"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.workspaces.closeHostedWorkspace(workspaceId = "00000000-0000-0000-6658-e129a559a4dd")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJjbG9zZUhvc3RlZFdvcmtzcGFjZSJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLmdldEhvc3RlZFdvcmtzcGFjZSIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEhvc3RlZFdvcmtzcGFjZSIsInBhdGgiOiIvdjEvd29ya3NwYWNlcy97d29ya3NwYWNlSWR9IiwicmVzb3VyY2UiOiJ3b3Jrc3BhY2VzIiwic2VjdGlvbl9zaGEyNTYiOiI3MzFhM2M5ODY0OTFlNmEwODVmZmRhODVlMTFlZjQ4NmM2ZTViMWI4Y2M3MzVhNzhkYzIwOTI3ZDgxNzE5ZTg4Iiwic2lnbmF0dXJlX3NoYTI1NiI6ImUxZGU3Mzc4ZTA2MmZmMzY5NTA0NTBkOTNiNTMyZWI4Y2FhNjNlNjhhNjU0YWQwYjBiOTFlM2Q1ODllYWI1Y2QifQ -->
### `client.workspaces.getHostedWorkspace`

Operation ID: `getHostedWorkspace`  
Route: `GET` `/v1/workspaces/{workspaceId}`  
Equivalent member: `client.getHostedWorkspace`  

#### Signature

```kotlin
suspend fun getHostedWorkspace(params: GetHostedWorkspaceParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-dd2f-cd2edd1eeb24"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.workspaces.getHostedWorkspace(workspaceId = "00000000-0000-0000-dd2f-cd2edd1eeb24")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIb3N0ZWRXb3Jrc3BhY2UifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLmdldEhvc3RlZFdvcmtzcGFjZU9wZXJhdGlvbiIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEhvc3RlZFdvcmtzcGFjZU9wZXJhdGlvbiIsInBhdGgiOiIvdjEvd29ya3NwYWNlcy97d29ya3NwYWNlSWR9L29wZXJhdGlvbnMve29wZXJhdGlvbklkfSIsInJlc291cmNlIjoid29ya3NwYWNlcyIsInNlY3Rpb25fc2hhMjU2IjoiMzZjMTlkNTJhYjI0OWU5NWRhOGUwNDlhMmRjMzU2OWFhNmI2YjlmNjUyOWNhYjFjZjg3MzNkMWI5ZDdkYmJjZiIsInNpZ25hdHVyZV9zaGEyNTYiOiI3NWNiZTVmMjhlNjE4NmEyZWMxN2Y0MDE4NzM3ZDlmNTkwM2JkNTA0ODhlMGE0NGY3NjExODc4MTE3ZGRmZTkyIn0 -->
### `client.workspaces.getHostedWorkspaceOperation`

Operation ID: `getHostedWorkspaceOperation`  
Route: `GET` `/v1/workspaces/{workspaceId}/operations/{operationId}`  
Equivalent member: `client.getHostedWorkspaceOperation`  

#### Signature

```kotlin
suspend fun getHostedWorkspaceOperation(params: GetHostedWorkspaceOperationParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `operationId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-7261-284a8b699ebd"
    },
    {
      "in": "path",
      "name": "operationId",
      "value": "00000000-0000-0000-5ba1-19fa55640b6d"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.workspaces.getHostedWorkspaceOperation(workspaceId = "00000000-0000-0000-7261-284a8b699ebd", operationId = "00000000-0000-0000-5ba1-19fa55640b6d")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIb3N0ZWRXb3Jrc3BhY2VPcGVyYXRpb24ifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLmdldEhvc3RlZFdvcmtzcGFjZVNvdXJjZSIsIm1ldGhvZCI6IkdFVCIsIm9wZXJhdGlvbl9pZCI6ImdldEhvc3RlZFdvcmtzcGFjZVNvdXJjZSIsInBhdGgiOiIvdjEvd29ya3NwYWNlcy97d29ya3NwYWNlSWR9L3NvdXJjZSIsInJlc291cmNlIjoid29ya3NwYWNlcyIsInNlY3Rpb25fc2hhMjU2IjoiYTg3ODMzMzQyNDY2ZWQwNzlkODJiZjMwYWYzNzU3ZmVhN2Y2MjJjZDYzN2I5ZWZkMWQyNzU0Mjg1MmUzMWMxMyIsInNpZ25hdHVyZV9zaGEyNTYiOiI0NTdjY2I2NTYwZGQxNjYyNjc4MjgxYzNlYzVhMzUxMTJmNDg1OTA1MDk4ZmI4MDg5NGYxMjYzNmI4MzdlZTdmIn0 -->
### `client.workspaces.getHostedWorkspaceSource`

Operation ID: `getHostedWorkspaceSource`  
Route: `GET` `/v1/workspaces/{workspaceId}/source`  
Equivalent member: `client.getHostedWorkspaceSource`  

#### Signature

```kotlin
suspend fun getHostedWorkspaceSource(params: GetHostedWorkspaceSourceParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-43c8-d895a22336ed"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.workspaces.getHostedWorkspaceSource(workspaceId = "00000000-0000-0000-43c8-d895a22336ed")
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJnZXRIb3N0ZWRXb3Jrc3BhY2VTb3VyY2UifQ -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLmxpc3RIb3N0ZWRXb3Jrc3BhY2VzIiwibWV0aG9kIjoiR0VUIiwib3BlcmF0aW9uX2lkIjoibGlzdEhvc3RlZFdvcmtzcGFjZXMiLCJwYXRoIjoiL3YxL3dvcmtzcGFjZXMiLCJyZXNvdXJjZSI6IndvcmtzcGFjZXMiLCJzZWN0aW9uX3NoYTI1NiI6IjA3MjBlYzg5ZjQyNTRiOTczZmMzNjgzZTU5ZDkyNWUyMjViMDIyOWI5NjYyYjcwZTIyMWVlY2NlNjhiYTQzMDciLCJzaWduYXR1cmVfc2hhMjU2IjoiNGM2ODdhMmVkMGFlOTUxMzRjZWY0ZDUxN2M5MDI1MDcwNjMyZTk0ZmI1MGJjYjc5NWM1YjdiNzMzZjRjMWZmZiJ9 -->
### `client.workspaces.listHostedWorkspaces`

Operation ID: `listHostedWorkspaces`  
Route: `GET` `/v1/workspaces`  
Equivalent member: `client.listHostedWorkspaces`  

#### Signature

```kotlin
suspend fun listHostedWorkspaces(params: ListHostedWorkspacesParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| _none_ | | | | |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.workspaces.listHostedWorkspaces()
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJsaXN0SG9zdGVkV29ya3NwYWNlcyJ9 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLm9wZW5Ib3N0ZWRXb3Jrc3BhY2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoib3Blbkhvc3RlZFdvcmtzcGFjZSIsInBhdGgiOiIvdjEvd29ya3NwYWNlcyIsInJlc291cmNlIjoid29ya3NwYWNlcyIsInNlY3Rpb25fc2hhMjU2IjoiYjE1MDg3MjA1YjQyMjNiZmE4OThiZThlNWVmYzM1MmVhZjM4ZTkyYWJkYjg0ZGU2YTRiYmIyZWJkMzdhY2VkZSIsInNpZ25hdHVyZV9zaGEyNTYiOiJmNzFkMjMzMGQwZDRkMmNlMjg2MDc5OWMwMTU4ZDYxNjE5NmFkYzNmMjJmNWJhZTdmYWQ4NmJhNTY3M2UwMDk5In0 -->
### `client.workspaces.openHostedWorkspace`

Operation ID: `openHostedWorkspace`  
Route: `POST` `/v1/workspaces`  
Equivalent member: `client.openHostedWorkspace`  

#### Signature

```kotlin
suspend fun openHostedWorkspace(params: OpenHostedWorkspaceParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `Idempotency-Key` | `header` | no | `string` | Required here or in the idempotencyKey body field. Replays never allocate or execute again. |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `201` | Prepared workspace; source and provider allocation recorded durably | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "body": {},
  "content_type": "application/json",
  "parameters": []
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.workspaces.openHostedWorkspace(body = {}, /* optional: Idempotency-Key */)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJvcGVuSG9zdGVkV29ya3NwYWNlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLnJlY292ZXJIb3N0ZWRXb3Jrc3BhY2UiLCJtZXRob2QiOiJQT1NUIiwib3BlcmF0aW9uX2lkIjoicmVjb3Zlckhvc3RlZFdvcmtzcGFjZSIsInBhdGgiOiIvdjEvd29ya3NwYWNlcy97d29ya3NwYWNlSWR9L3JlY292ZXIiLCJyZXNvdXJjZSI6IndvcmtzcGFjZXMiLCJzZWN0aW9uX3NoYTI1NiI6ImU0ODJlNWU5ZDlmYWJhNjM0NDJhN2E5ZjFjNDE3NTU1ZGQwNmNhN2JkYTBjOGE3MGYxOTIzZDQ1OTcxNmFhZGUiLCJzaWduYXR1cmVfc2hhMjU2IjoiNDg1NTM2NjUzMmZiMDlkNGQ2NjFlNjE1ZmI5Y2Q1YzY5ZDQxNGQ5YzRjNjVmOTVhN2NmNjk4YWI2NzU0OTczYSJ9 -->
### `client.workspaces.recoverHostedWorkspace`

Operation ID: `recoverHostedWorkspace`  
Route: `POST` `/v1/workspaces/{workspaceId}/recover`  
Equivalent member: `client.recoverHostedWorkspace`  

#### Signature

```kotlin
suspend fun recoverHostedWorkspace(params: RecoverHostedWorkspaceParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `202` | No verified terminal receipt yet; workspace remains unavailable for new commands | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "body": {
    "operationId": "00000000-0000-0000-d4ac-b0b84827b6d9"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-973a-c9ae0260973d"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.workspaces.recoverHostedWorkspace(workspaceId = "00000000-0000-0000-973a-c9ae0260973d", body = {"operationId": "00000000-0000-0000-d4ac-b0b84827b6d9"})
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJyZWNvdmVySG9zdGVkV29ya3NwYWNlIn0 -->

<!-- omniwrap-api-operation eyJleGFtcGxlX3JlYXNvbiI6bnVsbCwiZXhhbXBsZV9zdGF0dXMiOiJnZW5lcmF0ZWQiLCJtZW1iZXIiOiJ3b3Jrc3BhY2VzLnJ1bkhvc3RlZFdvcmtzcGFjZSIsIm1ldGhvZCI6IlBPU1QiLCJvcGVyYXRpb25faWQiOiJydW5Ib3N0ZWRXb3Jrc3BhY2UiLCJwYXRoIjoiL3YxL3dvcmtzcGFjZXMve3dvcmtzcGFjZUlkfS9ydW4iLCJyZXNvdXJjZSI6IndvcmtzcGFjZXMiLCJzZWN0aW9uX3NoYTI1NiI6ImJiZjM2OGIyYmY1ZDk1MDFmOTA5YzI3OGVkZDc0MjUyMjQ3YmY2NGJiMjc2NWM1ZWZkZTNkNjQ0ZDY3MGMxODEiLCJzaWduYXR1cmVfc2hhMjU2IjoiYzU0ZDkzMzZmY2ZmNzFkMDMzMjM0NDAyZGEzOWE3ZTcyMzQxYWFkNjMyMTg2Mzk5MDZlNDAxOGE1MTUxYTgxNiJ9 -->
### `client.workspaces.runHostedWorkspace`

Operation ID: `runHostedWorkspace`  
Route: `POST` `/v1/workspaces/{workspaceId}/run`  
Equivalent member: `client.runHostedWorkspace`  

#### Signature

```kotlin
suspend fun runHostedWorkspace(params: RunHostedWorkspaceParams, requestOptions: RequestOptions = RequestOptions()): ApiResult<Unit>
```

#### Parameters

| Name | In | Required | Contract type | Description |
| --- | --- | --- | --- | --- |
| `workspaceId` | `path` | yes | `string&lt;uuid&gt;` |  |
| `Idempotency-Key` | `header` | no | `string` | Required here or in the idempotencyKey body field. Replays never allocate or execute again. |
| `body` | body | yes | `object` |  |

#### Responses

| Status | Description | Content |
| --- | --- | --- |
| `200` | Authorized workspace state or result | none |
| `202` | Running or uncertain operation; inspect or explicitly recover, never resend with a new key | none |
| `400` | Invalid bounded request | none |
| `401` | Product session rejected | none |
| `402` | Hub entitlement or atomic quota denied | none |
| `403` | Operation or fleet policy denied | none |
| `404` | Resource not found in the authorized tenant and product environment | none |
| `409` | Idempotency conflict, incompatible state or cleanup unconfirmed | none |
| `503` | Operator provider, template, storage or authority unavailable | none |

#### Canonical required-input example

```json
{
  "body": {
    "command": "example"
  },
  "content_type": "application/json",
  "parameters": [
    {
      "in": "path",
      "name": "workspaceId",
      "value": "00000000-0000-0000-4862-6c003dd1756b"
    }
  ]
}
```

#### SDK call example

Example status: `generated`  
```kotlin
val result = client.workspaces.runHostedWorkspace(workspaceId = "00000000-0000-0000-4862-6c003dd1756b", body = {"command": "example"}, /* optional: Idempotency-Key */)
```

<!-- omniwrap-api-operation-end eyJvcGVyYXRpb25faWQiOiJydW5Ib3N0ZWRXb3Jrc3BhY2UifQ -->


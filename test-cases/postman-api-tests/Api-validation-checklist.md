REST API Validation Checklist (Postman)

1. Authentication & Authorization Checks
- Valid Credentials (200 OK): Verify response schema, token issuance, and user role mapping.
- Invalid Credentials (401 Unauthorized): Verify generic error message (no user enumeration) and clean JSON error format.
- Missing / Expired Token (401 Unauthorized): Ensure protected student progress endpoints reject unauthenticated requests.
- Cross-Account Access (403 Forbidden): Attempt to access another student's assessment or progress record using a valid token from a different account.

2. Payload & Boundary Validation
- Missing Required Fields (400 / 422): Omit student_id, topic_id, or answer and verify graceful validation errors.
- Invalid Data Types (400 / 422): Send string values for numeric score/difficulty fields and confirm the API does not throw a 500 Internal Server Error.
- Duplicate Submission Handling: Submit the same assessment completion payload twice and verify idempotency (no duplicate memory or score records created).

3. Rate Limiting & Reliability
- Burst Requests (429 Too Many Requests): Send rapid consecutive requests to auth and submission endpoints to verify throttling thresholds.
- Response Time SLA: Verify core read/write endpoints respond within acceptable latency under normal load.

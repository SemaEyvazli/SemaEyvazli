# Quality Assurance Specialist
**Testing Scope:** Manual, Integration & API Security Testing

---

## Test Suite & Documentation

### Test Case 1: Application Submission via UI & API Verification
* **Category:** Integration Testing (Web UI + Backend API)
* **Pre-conditions:** User is logged in; active Bearer Token is available.

#### Execution Steps:
1. Navigate to the **Smplifai** web application.
2. Click the **'New Application'** button.
3. Input valid details into the **'Email'** and **'Phone'** fields.
4. Click **'Choose'** -> **'Browse files'** and upload the required document.
5. Click **'Next'** and confirm the *"Document successfully uploaded"* notification.

---

### Test Case 2: API Endpoint Validation
* **Category:** API & Integration Testing

#### Execution Steps:
1. Send request to the target API endpoint.
2. Validate response status code and payload structure.

---

### Test Case 3: DELETE Request & Authorization Security Verification
* **Category:** API Security & Error Recovery Testing
* **Target Endpoint:** `DELETE https://smplifai-backend.vercel.app/api/applications/{id}`

#### Scenario A: Negative Test (Unauthenticated Deletion Attempt)
1. Open Swagger API Docs and navigate to `DELETE /api/applications/{id}`.
2. Enter Application ID: `72a38e24-5f54-43d5-82bc-d20bad9734e5`.
3. Click **Execute** *WITHOUT* setting the `Authorize Bearer Token`.
4. Verify system blocks request and returns `HTTP 401 Unauthorized`:

```json
{
  "success": false,
  "message": "Unauthorized access"
}


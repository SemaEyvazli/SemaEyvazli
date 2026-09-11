# 🧪 Smplifai Web QA & API Test Suite

This repository documents automated/manual test execution suites, integration flows, and API security test cases for the **Smplifai** web application and backend API services.

---

## 📌 Executive Summary

* **Testing Scope:** Web UI Integration Testing, Backend API Endpoint Verification, Security & Authorization Controls
* **Base API URL:** `https://smplifai-backend.vercel.app`
* **Authentication Method:** `Bearer <JWT_TOKEN>`

---

## 📂 Test Cases

### 1. Application Creation (`POST /api/applications`)

* **Category:** Backend API / Functional Testing
* **Target Endpoint:** `POST https://smplifai-backend.vercel.app/api/applications`
* **Pre-conditions:** Active Bearer Token configured in API Client / Swagger Docs.

#### Execution Steps:
1. Open API Documentation (Swagger).
2. Configure authentication header with a valid `Bearer Token`.
3. Construct the payload to initialize a new application draft.
4. Execute `POST` request to `/api/applications`.
5. Verify response payload schema and HTTP status code.

#### cURL Request:
```bash
curl -X 'POST' \
  'https://smplifai-backend.vercel.app/api/applications' \
  -H 'accept: application/json' \
  -H 'Authorization: Bearer <YOUR_ACCESS_TOKEN>' \
  -H 'Content-Type: application/json' \
  -d '{
    "type": "My Passport"
  }'
```

#### Expected Response Body:
```json
{
  "id": "f6c4373c-e6b9-4727-ab2e-73fac97f10e7",
  "user_id": "54efe78c-f0d3-4ee2-a318-2d1ad24941b9",
  "type": "My Passport",
  "email": null,
  "phone": null,
  "passport_data": null,
  "file_url": null,
  "status": "DRAFT",
  "created_at": "2026-09-09T16:04:44.747629+00:00",
  "updated_at": "2026-09-09T16:04:44.747629+00:00",
  "documents_uploaded": false,
  "reject_reason": null
}
```

* **Status Code:** `201 Created` — **PASSED**

---

### 2. UI Submission & API Integration Verification

* **Category:** End-to-End (Web UI + Backend Integration)
* **Pre-conditions:** User is logged in to the Smplifai web application with active session credentials.

#### Execution Steps:
1. Navigate to the **Smplifai** web portal.
2. Click on the **'New Application'** button.
3. Enter valid user credentials into the **Email** and **Phone** input fields.
4. Click **'Choose'** $\rightarrow$ **'Browse files'** and select the document for upload.
5. Click **'Next'** and confirm the *"Document successfully uploaded"* UI notification.
6. Open Swagger API Docs to verify application record persistence via backend API query.

#### Endpoint Verification:
`GET https://smplifai-backend.vercel.app/api/applications`

#### Expected Response Body:
```json
{
  "id": "ad25b048-bfec-4feb-87a2-11d9c49e3d20",
  "user_id": "54efe78c-f0d3-4ee2-a318-2d1ad24941b9",
  "type": "Enrollment Agreement",
  "email": "smaeyvazli@gmail.com",
  "phone": "+112265666665",
  "passport_data": null,
  "file_url": null,
  "status": "documents_uploaded",
  "created_at": "2026-09-08T16:07:31.67857+00:00",
  "updated_at": "2026-09-08T16:07:31.67857+00:00",
  "documents_uploaded": false,
  "reject_reason": null,
  "filled_forms": [],
  "filled_form_url": null
}
```

* **Status Code:** `200 OK` — **PASSED**

---

### 3. Application Deletion & Authorization Security Verification (`DELETE /api/applications/{id}`)

* **Category:** API Security & Authorization Error Recovery
* **Target Endpoint:** `DELETE https://smplifai-backend.vercel.app/api/applications/{id}`

#### Pre-conditions:
* Target Application ID created: `72a38e24-5f54-43d5-82bc-d20bad97dd81`.

---

#### Scenario A: Unauthorized Deletion Attempt (Negative Test)

**Steps:**
1. Access Swagger API Docs.
2. Navigate to `DELETE /api/applications/{id}`.
3. Provide Application ID: `72a38e24-5f54-43d5-82bc-d20bad97dd81`.
4. Execute request **WITHOUT** providing a valid `Bearer Token` in header.

**Actual Response Body:**
```json
{
  "success": false,
  "message": "Unauthorized"
}
```

* **Status Code:** `401 Unauthorized` — **PASSED (Security Assertion Verified)**

---

#### Scenario B: Recovery & Authorized Deletion (Positive Test)

**Steps:**
1. Click the **Authorize** button in Swagger API Docs.
2. Input valid `Bearer <JWT_TOKEN>` credentials and click **Authorize**.
3. Re-execute the `DELETE` request with Application ID `72a38e24-5f54-43d5-82bc-d20bad97dd81`.
4. Confirm response confirmation and record removal.

* **Expected Status Code:** `200 OK` — **PASSED**

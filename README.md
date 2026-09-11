# Quality Assurance Specialist
**Testing Scope:** Manual, Integration & API Security Testing

---

## Test Cases

### Test Case 1: Application Submission via UI & API Verification
* **Category:** Integration Testing (Web UI + Backend API)
* **Pre-conditions:** User is logged in; active Bearer Token is available.

#### Execution Steps:
1. Navigate to the **Smplifai** web application.
2. Click the **'New Application'** button.
3. Input valid details into the **'Email'** and **'Phone'** fields.
4. Click **'Choose'** -> **'Browse files'** and upload the required document.
5. Click **'Next'** and confirm the *"Document successfully uploaded"* notification.Smplifai API & Web QA Test Suite

End-to-End Test Cases & API Verification Portfolio Documentation

Project Name

Target URL

Smplifai Web & API Platform

https://smplifai-backend.vercel.app

QA Engineer

Testing Type

Quality Assurance Specialist

Manual, Integration & API Security Testing

Test Case 1: Application Submission via UI & API Verification

Category: Integration Testing (Web UI + Backend API)

Pre-conditions: User is logged in; active Bearer Token is available.

Execution Steps:

Navigate to the Smplifai web application.

Click the 'New Application' button.

Input valid details into the 'Email' and 'Phone' fields.

Click 'Choose' -> 'Browse files' and upload the required document.

Click 'Next' and confirm the 'Document successfully uploaded' notification.

Access Swagger API Docs and verify the newly generated record via GET/POST endpoints.

Expected API Response Body (200 OK):

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


Test Case 2: Direct API Draft Application Creation

Category: Backend API Testing

Pre-conditions: Valid Authorization Bearer Token included in headers.

cURL Request Template:

curl -X 'POST' \
  'https://smplifai-backend.vercel.app/api/applications' \
  -H 'Authorization: Bearer <YOUR_BEARER_TOKEN>' \
  -H 'Content-Type: application/json'


Expected API Response Body (201 Created):

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


Test Case 3: DELETE Request & Authorization Security Verification

Category: API Security & Error Recovery Testing

Target Endpoint: DELETE https://smplifai-backend.vercel.app/api/applications/{id}

Scenario A: Negative Test (Unauthenticated Deletion Attempt)

Open Swagger API Docs and navigate to DELETE /api/applications/{id}.

Enter Application ID: 72a38e24-5f54-43d5-82bc-d20bad97dd81.

Click Execute WITHOUT setting the Authorize Bearer Token.

Verify system blocks request and returns HTTP 401 Unauthorized.

{
  "success": false,
  "message": "Unauthorized"
}
/* HTTP Status Code: 401 Unauthorized (PASSED) */


Scenario B: Positive Test (Authenticated Deletion & Recovery)

Click the 'Authorize' button in Swagger UI.

Paste a valid Bearer Token and click Authorize.

Re-execute the DELETE request for Application ID: 72a38e24-5f54-43d5-82bc-d20bad97dd81.

Verify the deletion succeeds with HTTP Status 200 OK.

/* Response Status: 200 OK (PASSED - Record successfully deleted) */


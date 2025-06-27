
---

### 🧍 User Story: Patient Registration

> **"As a patient, I want to register with my demographic and insurance details."**

---

## 🔹 Background Scenario

A new patient visits the healthcare portal for the first time. They want to register themselves with basic demographic information and insurance coverage details so they can schedule appointments, view health records, and receive updates. The information must be securely stored, properly validated, and made accessible to various subsystems such as billing, observation, and appointments.

---

## ✅ Functional Requirements (FR)

| ID     | Functional Requirement                                                                                                      |
| ------ | --------------------------------------------------------------------------------------------------------------------------- |
| FR-001 | The portal must present a registration form to collect demographic (name, DOB, gender, email, phone) and insurance details. |
| FR-002 | The system must validate inputs for correct formats (e.g., email, phone number, insurance ID).                              |
| FR-003 | On successful registration, create a FHIR-compliant `Patient` resource in the database.                                     |
| FR-004 | Trigger an event on Kafka topic `patient.created` for downstream services (billing, appointments).                          |
| FR-005 | Send a welcome notification via email/SMS using the `notification-service`.                                                 |

---

## 🚫 Non-Functional Requirements (NFR)

| ID      | NFR Requirement                                                                                           |
| ------- | --------------------------------------------------------------------------------------------------------- |
| NFR-001 | Registration response time should be < 2 seconds.                                                         |
| NFR-002 | All Personally Identifiable Information (PII) must be encrypted in transit (HTTPS) and at rest (AES-256). |
| NFR-003 | The system must ensure idempotent registration using email/mobile as a unique key.                        |
| NFR-004 | High availability of 99.9% SLA for the patient-service API.                                               |
| NFR-005 | Audit logs must be captured for all create/update actions.                                                |

---

## 🎯 Roles & RBAC

| Role           | Permission                                                 |
| -------------- | ---------------------------------------------------------- |
| `Patient`      | Can register and update their own profile.                 |
| `Admin`        | Can search, merge, or anonymize patient records.           |
| `Doctor/Nurse` | Can view but not edit patient registration info.           |
| `System`       | Has read/write access to `Patient` for inter-service sync. |

RBAC is enforced using `role-management-service`. Permissions are verified before performing actions on the `Patient` resource using token claims in JWT.

---

## 🔄 Integration Architecture

### Microservices Involved:

* `patient-service`
* `notification-service`
* `audit-logging-service`
* `role-management-service`
* `analytics-service` (optional enrichment)
* Kafka for asynchronous communication

### Kafka Topics:

* `patient.created`
* `patient.updated`
* `patient.failed`

---

## 🧰 API Contracts

**POST /api/v1/patient/register**

```json
{
  "firstName": "John",
  "lastName": "Doe",
  "dob": "1990-01-01",
  "email": "john.doe@example.com",
  "phone": "+91-9876543210",
  "insurance": {
    "provider": "HealthCo",
    "policyId": "HC123456789"
  }
}
```

**Response:**

```json
{
  "status": "success",
  "patientId": "MRN_8371ad2",
  "message": "Patient registered successfully."
}
```

---

## 🗄️ Database Schema (MongoDB / PostgreSQL with FHIR Layer)

**Collection/Table: `patients`**

| Field     | Type   | Notes         |
| --------- | ------ | ------------- |
| patientId | String | Unique MRN    |
| firstName | String | Required      |
| lastName  | String | Required      |
| dob       | Date   | Required      |
| email     | String | Unique        |
| phone     | String | Unique        |
| insurance | Object | Embedded JSON |
| createdAt | Date   | Auto          |
| updatedAt | Date   | Auto          |

FHIR Resource Example:

* `Patient.name`, `Patient.telecom`, `Patient.identifier`, `Patient.address`

---

## 🎨 UI/UX (Simplified Screens)

1. **Step 1: Personal Info**

   * Fields: Name, DOB, Gender, Email, Phone
   * Validations: real-time, red text error indicators

2. **Step 2: Insurance Info**

   * Fields: Provider, Policy Number, Valid From/To
   * Auto-suggestions for provider list

3. **Step 3: Review & Submit**

   * Summary view
   * Consent checkbox: "I consent to data usage..."

4. **Confirmation Page**

   * Success message, patient ID, next steps link

🖼️ UI Wireframe: *(Can be generated separately in Figma or HTML)*

---

## 📊 Workflow (System Interaction)

```plaintext
[UI Form Submission]
      ↓
[patient-service: POST /register]
      ↓
[DB: Save Patient Info]
      ↓
[Kafka: patient.created]
      ↓
→ notification-service (send welcome email/SMS)
→ audit-logging-service (log creation)
→ analytics-service (enrich demographic stats)
```

---

## 🧠 Business Validation & Edge Cases

* Duplicate Email or Phone: Must be rejected with clear message.
* Incomplete Form: Show UI validation.
* Malformed Insurance ID: Pattern-based validation using regex.
* Consent Not Given: Prevent submission.

---

## 📣 Monitoring & Observability

| Metric               | Tool                                  |
| -------------------- | ------------------------------------- |
| API Latency          | Prometheus/Grafana                    |
| Failed Registrations | Kafka DLQ Monitor                     |
| Audit Trail          | ELK Stack                             |
| Consent Status Logs  | FHIR `Consent` resource & Mongo Index |

---


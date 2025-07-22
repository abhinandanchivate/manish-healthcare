


1. **Screen-by-screen UI requirements**
2. **Forms, controls, validations**
3. **Tabular reports**
4. **Navigation & layout**
5. **HL7 relevance**

---

## ✅ Multi-Page Application (MPA) — UI Requirements Specification

---

### 🔷 **1. Dashboard (Home)**

#### 🧩 Purpose:

High-level summary with quick links to key modules.

#### 🖥 UI Requirements:

| Component          | Type        | Description                                                      |
| ------------------ | ----------- | ---------------------------------------------------------------- |
| Module Quick Links | Button Grid | Links to all core modules                                        |
| Patient Search     | Search Box  | Search by MRN / Name / Phone                                     |
| Stats Cards        | Info Boxes  | Counts: Total Patients, Admitted, Discharged, Appointments today |
| Activity Feed      | Table/List  | Recent events (registrations, encounters, appointments)          |

---

### 🔷 **2. Patient Registration**

#### 🧩 Purpose:

Register or update patient demographic info.

#### 🖥 UI Requirements:

| Field Name     | Type     | Validation / Requirement                     |
| -------------- | -------- | -------------------------------------------- |
| Patient ID     | Auto-gen | Read-only; displayed but not editable        |
| Full Name      | Textbox  | Required, min 3 chars, only letters/spaces   |
| Date of Birth  | Date     | Required, must be <= today                   |
| Gender         | Dropdown | Required: Male/Female/Other                  |
| Contact Number | Textbox  | 10-digit validation                          |
| Email          | Textbox  | Optional, must be valid email                |
| Address        | Textarea | Optional                                     |
| Blood Group    | Dropdown | Optional                                     |
| ID Proof Type  | Dropdown | Aadhar, Passport, DL, Voter ID               |
| ID Number      | Textbox  | Conditional; required if Proof Type selected |

#### 📊 Report View:

| Column     | Description              |
| ---------- | ------------------------ |
| Patient ID | Unique auto-generated ID |
| Name       | Full name                |
| DOB        | Formatted date           |
| Gender     | M / F / O                |
| Phone      | Mobile number            |
| Status     | Active / Inactive        |

---

### 🔷 **3. Encounter Management**

#### 🧩 Purpose:

Track admission, discharge, transfers.

#### 🖥 UI Requirements:

| Field Name       | Type       | Validation / Requirement           |
| ---------------- | ---------- | ---------------------------------- |
| Encounter ID     | Auto-gen   | Display only                       |
| Patient ID       | Searchable | Required; link to existing patient |
| Encounter Date   | DateTime   | Required                           |
| Visit Type       | Dropdown   | OP / IP / ER                       |
| Department       | Dropdown   | Required                           |
| Room / Ward      | Textbox    | Required if IP                     |
| Attending Doctor | Dropdown   | Required                           |
| Visit Reason     | Textbox    | Optional                           |

#### 📊 Report View:

| Column         | Description                         |
| -------------- | ----------------------------------- |
| Encounter ID   | Unique per visit                    |
| Patient Name   | Auto-fetched                        |
| Department     | Assigned department                 |
| Status         | Admitted / Discharged / Transferred |
| Length of Stay | Auto-calculated if discharged       |

---

### 🔷 **4. Provider Assignment**

#### 🧩 Purpose:

Assign clinical staff to encounters.

#### 🖥 UI Requirements:

| Field Name         | Type       | Validation / Requirement           |
| ------------------ | ---------- | ---------------------------------- |
| Provider Name      | Dropdown   | From pre-loaded list               |
| Role               | Dropdown   | Attending / Referring / Consulting |
| Specialization     | Textbox    | Optional                           |
| Assigned Encounter | Searchable | Link to active encounter           |

#### 📊 Report View:

| Column           | Description                 |
| ---------------- | --------------------------- |
| Provider Name    | Doctor/Nurse                |
| Role             | Attending, etc.             |
| Linked Encounter | Encounter ID                |
| Patient          | Auto-fetched from encounter |

---

### 🔷 **5. Appointment Scheduling**

#### 🧩 Purpose:

Manage upcoming/past appointments.

#### 🖥 UI Requirements:

| Field Name     | Type       | Validation / Requirement          |
| -------------- | ---------- | --------------------------------- |
| Appointment ID | Auto-gen   | Display only                      |
| Patient ID     | Searchable | Required                          |
| Date & Time    | DateTime   | Required, must be in future       |
| Provider       | Dropdown   | Required                          |
| Reason         | Textarea   | Optional                          |
| Status         | Dropdown   | Scheduled / Completed / Cancelled |

#### 📊 Report View:

| Column       | Description      |
| ------------ | ---------------- |
| Date & Time  | Scheduled slot   |
| Patient Name | Auto-resolved    |
| Provider     | Attending doctor |
| Status       | Current status   |

---

### 🔷 **6. Insurance / Payer Info**

#### 🧩 Purpose:

Capture insurance and guarantor details.

#### 🖥 UI Requirements:

| Field Name        | Type     | Validation / Requirement       |
| ----------------- | -------- | ------------------------------ |
| Insurance ID      | Textbox  | Required                       |
| Payer Name        | Textbox  | Required                       |
| Coverage Type     | Dropdown | Primary / Secondary / Self-pay |
| Effective Date    | Date     | Required                       |
| Expiry Date       | Date     | Optional                       |
| Guarantor Name    | Textbox  | Optional                       |
| Guarantor Contact | Textbox  | Optional                       |

#### 📊 Report View:

| Column          | Description           |
| --------------- | --------------------- |
| Patient ID      | Mapped from insurance |
| Payer Name      | Insurance provider    |
| Policy Validity | Effective → Expiry    |
| Guarantor       | If available          |

---

### 🔷 **7. Clinical Summary (View Only)**

#### 🧩 Purpose:

Aggregate patient-centric data across modules.

#### 🖥 UI Elements:

* **Tabs**: Demographics, Encounters, Appointments, Providers, Insurance
* **Timeline**: Display encounter and appointment history chronologically
* **Download Summary**: PDF export button

---

## 🔁 General UI Design Principles

| Principle            | Requirement                                      |
| -------------------- | ------------------------------------------------ |
| Navigation           | Top-level tabs or side menu with icons           |
| Accessibility        | Labels, tooltips, tab order must be logical      |
| Validation           | Client-side & server-side checks                 |
| Mobile Support       | Forms and tables must be responsive              |
| Export/Print         | Reports should support CSV/PDF export            |
| HL7 Message Triggers | Based on action (e.g., ADT^A01 on new encounter) |

---


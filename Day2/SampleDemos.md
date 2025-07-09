Here are **step-by-step guided messaging workflow scenarios**

## 📘 SCENARIO 1: **Patient Admission in Emergency Department**

**Objective**: Patient walks into ER. Hospital creates a new visit and assigns a bed.

### 🔁 HL7 Messaging Workflow:

| **Step** | **Action**                         | **System**               | **HL7 Message**    |
| -------- | ---------------------------------- | ------------------------ | ------------------ |
| 1️⃣      | Patient registers at reception     | EMR                      | `ADT^A01` (Admit)  |
| 2️⃣      | Demographics sent to other systems | EMR → LIS/RIS/Billing    | `ADT^A01`          |
| 3️⃣      | Nurse assigns bed in ER            | EMR updates PV1 segment  | `ADT^A08` (Update) |
| 4️⃣      | Wristband printed with MRN         | HIS prints barcode label | –                  |

---

## 🧪 SCENARIO 2: **Doctor Orders a Blood Test**

**Objective**: Doctor orders CBC. Lab receives and processes it.

### 🔁 HL7 Messaging Workflow:

| **Step** | **Action**                 | **System**                  | **HL7 Message**       |
| -------- | -------------------------- | --------------------------- | --------------------- |
| 1️⃣      | Doctor orders CBC in EMR   | EMR                         | `ORM^O01` (Order)     |
| 2️⃣      | Order sent to LIS          | EMR → LIS                   | `ORM^O01`             |
| 3️⃣      | Phlebotomist draws blood   | LIS updates status          | `ORM^O01` with status |
| 4️⃣      | Test performed             | Lab system generates result | –                     |
| 5️⃣      | Result sent to EMR         | LIS → EMR                   | `ORU^R01` (Result)    |
| 6️⃣      | Doctor views result in EMR | EMR                         | –                     |

---

## 🖼️ SCENARIO 3: **Radiology Exam & Reporting**

**Objective**: CT Chest is ordered and reviewed by radiologist.

### 🔁 HL7 Messaging Workflow:

| **Step** | **Action**                      | **System**                    | **HL7 Message** |
| -------- | ------------------------------- | ----------------------------- | --------------- |
| 1️⃣      | Doctor orders CT Chest          | EMR                           | `ORM^O01`       |
| 2️⃣      | Order sent to RIS               | EMR → RIS                     | `ORM^O01`       |
| 3️⃣      | RIS schedules scan              | RIS updates schedule          | `SIU^S12`       |
| 4️⃣      | CT scan performed               | Modality stores image in PACS | – (DICOM)       |
| 5️⃣      | Radiologist reads image         | PACS viewer                   | –               |
| 6️⃣      | Report generated in RIS         | RIS                           | –               |
| 7️⃣      | Report sent to EMR              | RIS → EMR                     | `ORU^R01`       |
| 8️⃣      | Doctor sees image link & report | EMR                           | –               |

---

## 💉 SCENARIO 4: **Vaccination Update to Registry**

**Objective**: Clinic administers COVID-19 vaccine and sends update to state registry.

### 🔁 HL7 Messaging Workflow:

| **Step** | **Action**                            | **System**           | **HL7 Message** |
| -------- | ------------------------------------- | -------------------- | --------------- |
| 1️⃣      | Nurse records vaccination             | EMR                  | `VXU^V04`       |
| 2️⃣      | Message sent to immunization registry | EMR → State Registry | `VXU^V04`       |
| 3️⃣      | Registry returns ACK                  | Registry → EMR       | `ACK`           |
| 4️⃣      | Record shown as submitted             | EMR status updated   | –               |

---

## 💳 SCENARIO 5: **Billing After Surgery**

**Objective**: Patient undergoes knee surgery. Billing is triggered.

### 🔁 HL7 Messaging Workflow:

| **Step** | **Action**                | **System**             | **HL7 Message**         |
| -------- | ------------------------- | ---------------------- | ----------------------- |
| 1️⃣      | Surgery order initiated   | EMR → OR system        | `ORM^O01`               |
| 2️⃣      | Surgery performed         | OR marks completion    | –                       |
| 3️⃣      | Charges posted to billing | EMR → Billing          | `DFT^P03`               |
| 4️⃣      | Insurance billed          | Billing system → Payer | EDI 837 (non-HL7)       |
| 5️⃣      | Payment status updated    | Billing system → EMR   | `DFT^P03` or direct API |

---

## 📄 SCENARIO 6: **Uploading Scanned Document**

**Objective**: Scanned discharge summary PDF is stored in patient’s record.

### 🔁 HL7 Messaging Workflow:

| **Step** | **Action**                     | **System**              | **HL7 Message** |
| -------- | ------------------------------ | ----------------------- | --------------- |
| 1️⃣      | Staff uploads scanned document | EMR or Scanning App     | `MDM^T02`       |
| 2️⃣      | Document metadata recorded     | MDM stores doc ID, type | `MDM^T02`       |
| 3️⃣      | EMR links document to visit    | EMR document viewer     | –               |

---


---

 **expanded list of all major HL7 v2.x message types** 
---

## 🧾 **Complete HL7 v2.x Message Types with Real-World Use Cases**

| **HL7 Message Type** | **Full Form**                            | **When It Is Used**                               | **Example Scenario**                            |
| -------------------- | ---------------------------------------- | ------------------------------------------------- | ----------------------------------------------- |
| `ADT^A01`            | Admit/Visit Notification                 | Patient is admitted to hospital                   | Patient enters ER and is assigned a bed         |
| `ADT^A02`            | Transfer Patient                         | Patient moved from one ward to another            | Moved from ER to ICU                            |
| `ADT^A03`            | Discharge Patient                        | Patient is discharged from hospital               | Discharged after treatment                      |
| `ADT^A04`            | Register a Patient                       | Patient arrives for outpatient appointment        | Patient comes in for a check-up                 |
| `ADT^A08`            | Update Patient Info                      | Patient demographic or contact info updated       | New address or phone number entered             |
| `ADT^A11`            | Cancel Admit                             | Admission was canceled                            | Patient admitted by mistake                     |
| `ADT^A13`            | Cancel Discharge                         | Discharge was reversed                            | Patient not stable, re-admitted                 |
| `ORM^O01`            | Order Entry                              | Order for lab test, imaging, etc.                 | Doctor orders blood test or CT scan             |
| `ORU^R01`            | Observation Result                       | Sends results from lab or imaging                 | Lab sends hemoglobin result                     |
| `ORU^R30`            | Structured Report Result                 | Imaging result with structured fields             | Radiologist sends CT report                     |
| `OML^O21`            | Lab Order with Multiple Specimens        | One order contains multiple lab tests/specimens   | CBC + LFT in one order                          |
| `OBR` Segment        | Observation Request (within ORU/OML/ORM) | Indicates the specific test requested             | Blood glucose, X-ray                            |
| `OBX` Segment        | Observation Result Segment               | Carries the actual result                         | "Glucose = 92 mg/dL"                            |
| `DFT^P03`            | Detailed Financial Transaction           | Billing info for a procedure                      | Billing for X-ray                               |
| `BAR^P01`            | Add Patient Account Info                 | Billing account creation                          | Register new billing record                     |
| `SIU^S12`            | Schedule New Appointment                 | Create new patient appointment                    | Booking cardiology consult                      |
| `SIU^S13`            | Modify Appointment                       | Update appointment date or time                   | Reschedule dental visit                         |
| `SIU^S15`            | Cancel Appointment                       | Appointment canceled                              | Patient unavailable                             |
| `MDM^T02`            | Transmit Medical Document                | Sends discharge summary, operative notes          | Send summary to another hospital                |
| `VXU^V04`            | Unsolicited Vaccination Update           | Send vaccine info to government registry          | COVID-19 vaccine report                         |
| `QRY^A19`            | Patient Demographics Query               | Query to retrieve patient info                    | Insurance portal requests patient info          |
| `RDE^O11`            | Pharmacy/Treatment Encoded Order         | Medication order                                  | Doctor orders insulin for patient               |
| `RDS^O13`            | Pharmacy Dispense                        | Pharmacy sends dispense info                      | 10 tablets of Amoxicillin dispensed             |
| `RAS^O17`            | Pharmacy Administration Info             | Info about how medication was administered        | IV injection details                            |
| `RGR^R01`            | Pharmacy Give Report                     | Summary of medications given                      | Medication audit report                         |
| `ADT^A28`            | Add New Patient Record                   | New patient registered in system                  | First visit ever to hospital                    |
| `ADT^A31`            | Update Patient Record                    | Update any patient-related master record          | Add allergy information                         |
| `ACK`                | General Acknowledgment                   | Confirms that message was received successfully   | LIS replies ACK after receiving test order      |
| `NMD^N01`            | Application Management                   | Device or system status messages                  | Lab device sends status to LIS                  |
| `MFK^M01`            | Master File Acknowledgment               | Acknowledgment for master data updates            | Confirmation of new doctor added in master list |
| `MFN^M01`            | Master File Notification                 | Update master data such as providers, departments | Add new department to hospital directory        |

---

## 🧠 **Memory Aids**

| **Prefix** | **Represents**           | **Hint**                                      |
| ---------- | ------------------------ | --------------------------------------------- |
| `ADT`      | Admit/Discharge/Transfer | Movement or updates related to patient status |
| `ORM/OML`  | Orders                   | Doctor is ordering something                  |
| `ORU`      | Results                  | Lab or imaging is reporting results           |
| `SIU`      | Scheduling               | SIU = Schedule It Up!                         |
| `DFT/BAR`  | Billing/Accounts         | Related to financial transactions             |
| `VXU`      | Vaccine Update           | VX = Vaccination                              |
| `MDM`      | Documents                | Transmitting discharge summaries, notes       |
| `ACK`      | Acknowledgement          | Reply to confirm message                      |
| `QRY`      | Query                    | Requesting information                        |

---


---



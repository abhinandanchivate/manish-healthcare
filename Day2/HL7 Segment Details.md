 **detailed guide to HL7 v2.x message types with their generic syntax/structure (segment flow)**, grouped by category, so that you can **write, interpret, and build** 

---

## 🛏️ **1. ADT – Admit, Discharge, Transfer Messages**

| Message Type | Full Form                | Generic Syntax                |
| ------------ | ------------------------ | ----------------------------- |
| `ADT^A01`    | Admit/Visit Notification | `MSH` → `EVN` → `PID` → `PV1` |
| `ADT^A02`    | Transfer Patient         | `MSH` → `EVN` → `PID` → `PV1` |
| `ADT^A03`    | Discharge Patient        | `MSH` → `EVN` → `PID` → `PV1` |
| `ADT^A04`    | Register Outpatient      | `MSH` → `EVN` → `PID` → `PV1` |
| `ADT^A08`    | Update Patient Info      | `MSH` → `EVN` → `PID` → `PV1` |
| `ADT^A11`    | Cancel Admit             | `MSH` → `EVN` → `PID` → `PV1` |
| `ADT^A13`    | Cancel Discharge         | `MSH` → `EVN` → `PID` → `PV1` |
| `ADT^A28`    | Add New Patient          | `MSH` → `EVN` → `PID`         |
| `ADT^A31`    | Update Patient Record    | `MSH` → `EVN` → `PID`         |

---

## 🧪 **2. ORM / OML – Orders (Lab, Radiology, ECG, etc.)**

| Message Type | Full Form                | Generic Syntax                                     |
| ------------ | ------------------------ | -------------------------------------------------- |
| `ORM^O01`    | General Order Message    | `MSH` → `PID` → `PV1` → `ORC` → `OBR` (+ multiple) |
| `OML^O21`    | Lab Order with Specimens | `MSH` → `PID` → `PV1` → `ORC` → `OBR` → `SPM`      |

---

## 📊 **3. ORU – Observations / Results**

| Message Type | Full Form                 | Generic Syntax                                                                         |
| ------------ | ------------------------- | -------------------------------------------------------------------------------------- |
| `ORU^R01`    | Observation Result        | `MSH` → `PID` → `PV1` → `ORC` → `OBR` → `OBX` (+ repeatable)                           |
| `ORU^R30`    | Structured Imaging Report | `MSH` → `PID` → `PV1` → `ORC` → `OBR` → `OBX` (with structured text or PDF references) |

---

## 💉 **4. RDE / RDS / RAS – Pharmacy Orders, Dispense, Administration**

| Message Type | Full Form              | Generic Syntax                                                  |
| ------------ | ---------------------- | --------------------------------------------------------------- |
| `RDE^O11`    | Encoded Drug Order     | `MSH` → `PID` → `PV1` → `ORC` → `RXE` (+ optional `RXR`, `RXC`) |
| `RDS^O13`    | Dispense Message       | `MSH` → `PID` → `PV1` → `ORC` → `RXD`                           |
| `RAS^O17`    | Administration Message | `MSH` → `PID` → `PV1` → `ORC` → `RXA`                           |

---

## 💵 **5. DFT / BAR – Financial Transactions and Billing**

| Message Type | Full Form                   | Generic Syntax                                       |
| ------------ | --------------------------- | ---------------------------------------------------- |
| `DFT^P03`    | Financial Transaction       | `MSH` → `EVN` → `PID` → `PV1` → `FT1` (+ repeatable) |
| `BAR^P01`    | Add Patient Billing Account | `MSH` → `EVN` → `PID` → `PV1` → `IN1`, `IN2`         |

---

## 📅 **6. SIU – Scheduling Messages**

| Message Type | Full Form                | Generic Syntax                |
| ------------ | ------------------------ | ----------------------------- |
| `SIU^S12`    | Schedule New Appointment | `MSH` → `SCH` → `PID` → `PV1` |
| `SIU^S13`    | Modify Appointment       | `MSH` → `SCH` → `PID` → `PV1` |
| `SIU^S15`    | Cancel Appointment       | `MSH` → `SCH` → `PID` → `PV1` |

---

## 📑 **7. MDM – Medical Document Management**

| Message Type | Full Form                          | Generic Syntax                                          |
| ------------ | ---------------------------------- | ------------------------------------------------------- |
| `MDM^T02`    | Transmit Discharge/Operative Notes | `MSH` → `PID` → `PV1` → `TXA` → `OBX` (for attachments) |

---

## 💉 **8. VXU – Vaccination Updates**

| Message Type | Full Form                  | Generic Syntax                                           |
| ------------ | -------------------------- | -------------------------------------------------------- |
| `VXU^V04`    | Immunization Record Upload | `MSH` → `PID` → `ORC` → `RXA` → `OBX` (for observations) |

---

## 🔍 **9. QRY – Queries (Request for Patient Info)**

| Message Type        | Full Form                      | Generic Syntax        |
| ------------------- | ------------------------------ | --------------------- |
| `QRY^A19`           | Query for Patient Demographics | `MSH` → `QRD` → `QRF` |
| Response: `ADR^A19` | Respond with Patient Info      | `MSH` → `PID` → `PV1` |

---

## 🛠️ **10. Master Files & System Messages**

| Message Type | Full Form                      | Generic Syntax                                              |
| ------------ | ------------------------------ | ----------------------------------------------------------- |
| `MFN^M01`    | Master File Notification       | `MSH` → `MFI` → `MFE` → entity segments (e.g. `PRD`, `STF`) |
| `MFK^M01`    | Acknowledgement to Master File | `MSH` → `MSA`                                               |
| `NMD^N01`    | Application/System Status      | `MSH` → `NDS` → `NST`, `NSC`                                |

---

## ✅ **11. ACK – Acknowledgement**

| Message Type | Full Form       | Generic Syntax |
| ------------ | --------------- | -------------- |
| `ACK`        | Acknowledgement | `MSH` → `MSA`  |

---

## 🧠 Helpful Tip: HL7 Segment Cheatsheet

| Segment   | Description             |
| --------- | ----------------------- |
| `MSH`     | Message Header          |
| `EVN`     | Event Type              |
| `PID`     | Patient Identification  |
| `PV1`     | Patient Visit           |
| `ORC`     | Common Order            |
| `OBR`     | Observation Request     |
| `OBX`     | Observation Result      |
| `RXE`     | Pharmacy Encoded Order  |
| `RXA`     | Pharmacy Administration |
| `SCH`     | Schedule Segment        |
| `FT1`     | Financial Transaction   |
| `IN1/IN2` | Insurance Information   |
| `TXA`     | Document Metadata       |
| `QRD/QRF` | Query Definition/Filter |
| `MFI/MFE` | Master File Info/Event  |
| `MSA`     | Message Acknowledgement |

---

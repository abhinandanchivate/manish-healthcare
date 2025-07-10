To **build HL7 v2.x messages**,  **step-by-step guide**.  **how HL7 messages are constructed** from real-world healthcare events (like admission, lab orders, results, discharge, etc.).

---

## 🧱 Step-by-Step: How to Build HL7 v2.x Messages

---

### ✅ 1. **Understand the Healthcare Event**

Every HL7 message is tied to a **real-life action**.

| **Real Action**            | **HL7 Message Type** |
| -------------------------- | -------------------- |
| Patient Admitted           | `ADT^A01`            |
| Doctor Orders a Blood Test | `ORM^O01`            |
| Lab Sends Test Result      | `ORU^R01`            |
| Patient Discharged         | `ADT^A03`            |

👉 So the **first step** is to **identify what event** you want to model.

---

### ✅ 2. **Determine the Required HL7 Message Type**

Example: If a doctor orders a test → use `ORM^O01`
If lab sends result → use `ORU^R01`

---

### ✅ 3. **Use Segments Based on Message Type**

All HL7 v2.x messages are made of **segments**, each segment starts with a **3-letter code**.

| **Segment** | **Purpose**          |
| ----------- | -------------------- |
| `MSH`       | Message Header       |
| `PID`       | Patient Demographics |
| `PV1`       | Patient Visit Info   |
| `ORC`       | Common Order Info    |
| `OBR`       | Lab Test Requested   |
| `OBX`       | Lab Result           |

---

### ✅ 4. **Use Standard Delimiters**

| **Symbol** | **Purpose**             |                 |
| ---------- | ----------------------- | --------------- |
| \`         | \`                      | Field separator |
| `^`        | Component separator     |                 |
| `~`        | Repetition separator    |                 |
| `\`        | Escape character        |                 |
| `&`        | Sub-component separator |                 |

Default: `MSH|^~\&`

---

### ✅ 5. **Build the Message Line by Line**

Let’s say we want to **send a test result** (i.e., `ORU^R01`):

#### 🔶 MSH – Message Header

```hl7
MSH|^~\&|LIS|LAB|HIS|HOSPITAL|202507091000||ORU^R01|12345|P|2.3
```

| Field # | Meaning                  |
| ------- | ------------------------ |
| 3       | Sending system (`LIS`)   |
| 5       | Receiving system (`HIS`) |
| 7       | Message timestamp        |
| 9       | Message type (`ORU^R01`) |
| 10      | Message control ID       |
| 12      | HL7 version (e.g., 2.3)  |

---

#### 🔶 PID – Patient Info

```hl7
PID|1||P123456^^^HOSP^MR||PATEL^ANITA||19820512|F|||123 Main St^^Mumbai
```

---

#### 🔶 PV1 – Visit Info

```hl7
PV1|1|I|WARD1^BED5^01|||1234^Dr^SINGH
```

---

#### 🔶 OBR – Lab Order Details

```hl7
OBR|1||LAB1234|GLUCOSE^GLUCOSE TEST^L|||202507090900
```

---

#### 🔶 OBX – Lab Result Value

```hl7
OBX|1|NM|GLUCOSE^Glucose Level^L||92|mg/dL|70-110|N|||F
```

| Field | Meaning                         |
| ----- | ------------------------------- |
| 2     | Value Type (NM = Numeric)       |
| 3     | Observation Identifier          |
| 5     | Result Value                    |
| 6     | Units (mg/dL)                   |
| 7     | Reference Range                 |
| 8     | Abnormal Flag                   |
| 11    | Observation Result Status (`F`) |

---

## ✅ Final Combined HL7 ORU^R01 Message

```hl7
MSH|^~\&|LIS|LAB|HIS|HOSPITAL|202507091000||ORU^R01|12345|P|2.3
PID|1||P123456^^^HOSP^MR||PATEL^ANITA||19820512|F|||123 Main St^^Mumbai
PV1|1|I|WARD1^BED5^01|||1234^Dr^SINGH
OBR|1||LAB1234|GLUCOSE^GLUCOSE TEST^L|||202507090900
OBX|1|NM|GLUCOSE^Glucose Level^L||92|mg/dL|70-110|N|||F
```

---


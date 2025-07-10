**generic syntax guide for HL7 v2.x messages**, structured **segment by segment** with placeholder fields (`|`-separated), and annotated with what each field represents. This format helps **anyone write, understand, or simulate** HL7 messages in a human-readable way.

---

## 🟦 MSH – Message Header (Required for every HL7 message)

```
MSH|^~\&|<SendingApp>|<SendingFacility>|<ReceivingApp>|<ReceivingFacility>|<DateTime>|<Security>|<MessageType>|<ControlID>|<ProcessingID>|<Version>
```

| Pos | Field Name            | Description                             |    |
| --- | --------------------- | --------------------------------------- | -- |
| 1   | Field Separator       | Always \`                               | \` |
| 2   | Encoding Characters   | Typically `^~\&`                        |    |
| 3   | Sending Application   | System sending the message              |    |
| 4   | Sending Facility      | Physical/logical location of sender     |    |
| 5   | Receiving Application | System receiving the message            |    |
| 6   | Receiving Facility    | Location of receiver                    |    |
| 7   | Date/Time of Message  | Format: `YYYYMMDDHHMMSS`                |    |
| 8   | Security              | Optional – used for authentication      |    |
| 9   | Message Type          | e.g. `ADT^A01`, `ORM^O01`, `ORU^R01`    |    |
| 10  | Message Control ID    | Unique identifier for the message       |    |
| 11  | Processing ID         | P = Production, T = Training, D = Debug |    |
| 12  | Version ID            | HL7 version, e.g. `2.5`, `2.3.1`        |    |

---

## 🟩 PID – Patient Identification

```
PID|<SetID>|<ExternalID>|<PatientIDList>|<AltID>|<PatientName>|<MotherMaidenName>|<DOB>|<Sex>|<Alias>|<Address>|<County>|...
```

| Pos | Field Name              | Description                         |
| --- | ----------------------- | ----------------------------------- |
| 1   | Set ID – PID            | Sequence number of this PID segment |
| 3   | Patient Identifier List | MRN or unique patient ID            |
| 5   | Patient Name            | Format: `LastName^FirstName`        |
| 7   | Date of Birth           | `YYYYMMDD`                          |
| 8   | Sex                     | M/F/U                               |
| 11  | Patient Address         | `Street^Other^City^State^Zip`       |

---

## 🟨 PV1 – Patient Visit Information

```
PV1|<SetID>|<PatientClass>|<AssignedLocation>|...|<AttendingDoctor>|...
```

| Pos | Field Name        | Description                   |
| --- | ----------------- | ----------------------------- |
| 1   | Set ID – PV1      | Sequential number             |
| 2   | Patient Class     | I = Inpatient, O = Outpatient |
| 3   | Assigned Location | `Ward^Room^Bed`               |
| 7   | Attending Doctor  | `ID^Title^LastName`           |

---

## 🟧 ORC – Common Order Segment

```
ORC|<OrderControl>|<PlacerOrderNumber>|<FillerOrderNumber>|...|<OrderStatus>|...
```

| Pos | Field Name          | Description                                     |
| --- | ------------------- | ----------------------------------------------- |
| 1   | Order Control       | NW = New, CA = Cancel, OC = Order Cancelled     |
| 2   | Placer Order Number | Order ID from placing system                    |
| 3   | Filler Order Number | Order ID from fulfilling system (lab, pharmacy) |
| 5   | Order Status        | CM = Complete, DC = Discontinue                 |

---

## 🟪 OBR – Observation Request (used in ORU, ORM, OML)

```
OBR|<SetID>|<PlacerOrderNumber>|<FillerOrderNumber>|<ServiceID>|...|<ObservationDateTime>|...|<ResultStatus>
```

| Pos | Field Name            | Description                                       |
| --- | --------------------- | ------------------------------------------------- |
| 1   | Set ID – OBR          | Sequential ID of the OBR segment                  |
| 2   | Placer Order Number   | Optional order ID from ordering system            |
| 3   | Filler Order Number   | ID from lab or imaging system                     |
| 4   | Universal Service ID  | `Code^Name^CodingSystem` (e.g., `GLUCOSE^Test^L`) |
| 7   | Observation Date/Time | Time the test was performed                       |

---

## 🟥 OBX – Observation Result (used in ORU^R01)

```
OBX|<SetID>|<ValueType>|<ObservationID>|<ObsSubID>|<Value>|<Units>|<ReferenceRange>|<AbnormalFlag>|...|<Status>
```

| Pos | Field Name             | Description                                       |
| --- | ---------------------- | ------------------------------------------------- |
| 1   | Set ID – OBX           | Sequential ID                                     |
| 2   | Value Type             | `NM` (numeric), `ST` (string), `CE` (coded entry) |
| 3   | Observation Identifier | `Code^Desc^System`                                |
| 5   | Observation Value      | Actual result                                     |
| 6   | Units                  | `mg/dL`, `mmHg`, etc.                             |
| 7   | Reference Range        | `low-high` format                                 |
| 8   | Abnormal Flag          | N = Normal, H = High, L = Low                     |
| 11  | Result Status          | F = Final, C = Corrected, P = Preliminary         |

---

## 🟫 RXA – Pharmacy Administration (used in `VXU^V04` for vaccination)

```
RXA|<GiveSubID>|<AdminSubID>|<StartDate>|<EndDate>|<VaccineCode>|<Amount>|<Units>|...|<AdminNotes>
```

| Pos | Field Name            | Description                            |
| --- | --------------------- | -------------------------------------- |
| 1   | Give Sub-ID           | Sequence within RXA group              |
| 2   | Administration Sub-ID | Sequence of admin for same order       |
| 3   | Start Date/Time       | When dose was given                    |
| 4   | End Date/Time         | Same as Start if single administration |
| 5   | Vaccine Code          | `CVX Code^Name^CVX`                    |
| 6   | Amount Given          | Dose quantity                          |
| 7   | Units                 | `mL`, `mg`, etc.                       |
| 9   | Administration Notes  | Notes or reason codes                  |

---

## 🟨 FT1 – Financial Transaction (used in DFT^P03)

```
FT1|<SetID>|...|<TransactionDate>|...|<Code>|<Description>|<Qty>|<Amount>|<Currency>
```

| Pos | Field Name       | Description                    |
| --- | ---------------- | ------------------------------ |
| 1   | Set ID – FT1     | Sequence ID                    |
| 4   | Transaction Date | Date service was performed     |
| 6   | Transaction Code | Code for service (e.g., X-ray) |
| 7   | Description      | `XRAY^Chest X-ray`             |
| 8   | Quantity         | How many services performed    |
| 9   | Amount           | Cost of the service            |
| 10  | Currency         | INR, USD, etc.                 |

---

## 🟧 TXA – Document Metadata (used in MDM^T02)

```
TXA|<SetID>|<DocType>|<DocContentType>|<ActivityDateTime>|...|<OriginationDateTime>|<UniqueDocID>
```

| Pos | Field Name            | Description                      |
| --- | --------------------- | -------------------------------- |
| 1   | Set ID – TXA          | Sequence number                  |
| 2   | Document Type         | e.g., `DS` for discharge summary |
| 3   | Document Content Type | MIME type or HL7 type            |
| 4   | Activity Date/Time    | When document was generated      |
| 9   | Origination Date      | Original date of report          |
| 12  | Unique Document ID    | UUID or other unique reference   |

---


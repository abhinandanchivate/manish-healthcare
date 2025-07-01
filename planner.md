**12-Week HLS Training Planner — Weeks 1 to 4 with Detailed Sessions, Case Studies & Labs**

---

### **Week 1: Healthcare Data & Interoperability (Phase 1)**

#### **Case Study 1**: FHIR-Powered Patient Portal with HL7 Message Parsing

*Objective*: Demonstrate how HL7 v2.x messages can be parsed and visualized in a patient portal using FHIR.

#### **Case Study 2**: CDA-FHIR Hybrid Viewer

*Objective*: Display CDA documents side-by-side with their equivalent FHIR Bundles in a single UI.

| **Day**   | **Session 1**                                                | **Session 2**                                           | **Session 3**                                      | **Session 4: Assessment + Assignment**                                                                     |
| --------- | ------------------------------------------------------------ | ------------------------------------------------------- | -------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| **8th July** | Intro to Healthcare IT, EMRs, and Interoperability Evolution | HL7 v2.x Standard, Message Types (ADT, ORM, ORU)        | HL7 Message Structure: Segments, Delimiters, ACKs  | **Quiz (20 Qs)** + *Assignment*: Parse, validate & simulate routing of ADT message using 7Edit & Mirth     |
| **9th July** | FHIR Introduction, RESTful Design Principles                 | Core FHIR Resources: Patient, Observation, Encounter    | Working with Public FHIR Servers via Postman       | **Quiz (20 Qs)** + *Assignment*: Perform CRUD operations on Patient & Observation resources                |
| **10th July** | FHIR Profiling with StructureDefinition                      | Bundles, Composition, DocumentReference, ImagingReports | Terminologies: LOINC, SNOMED, ValueSet, CodeSystem | **Quiz (20 Qs)** + *Assignment*: Create FHIR profile with terminology bindings using Forge/Simplifier      |
| **11th July** | DICOM Overview, Metadata, PACS/VNA                           | CDA Structure, CCD Example, USCDI Mandates              | Interop Levels, Consent & Provenance Resources     | **Quiz (20 Qs)** + *Assignment*: Map sample DICOM to ImagingStudy + create DocumentReference Bundle        |
| **14th July** | Mirth Connect Setup, HL7 to FHIR Conversion                  | OAuth2, RBAC, FHIR API Authentication                   | Simulate EHR-to-HIE to FHIR Workflow               | **Quiz (20 Qs)** + *Assignment*: Ingest HL7 → Convert to FHIR → Store in FHIR Server → Access via REST API |

---

### **Week 2: Software Development Fundamentals (Phase 2)**

#### **Case Study 1**: BMI Calculator for Geriatric Patients

*Objective*: Use logic and validations to build a personalized BMI calculator in Python.

#### **Case Study 2**: ER Triage Queue Manager

*Objective*: Simulate a priority-based ER queue using data structures.

| **Day**   | **Session 1**                                        | **Session 2**                                        | **Session 3**                                     | **Session 4: Assessment + Assignment**                                                         |
| --------- | ---------------------------------------------------- | ---------------------------------------------------- | ------------------------------------------------- | ---------------------------------------------------------------------------------------------- |
| **15th July** | Intro to SDLC, Variables and Constants (Python/Java) | Data Types, Type Casting, I/O, Arithmetic Operations | Control Flow: if, elif, else, loops               | **Quiz (20 Qs)** + *Assignment*: Build a CLI BMI Calculator with validations                   |
| **16th July** | Data Structures: Lists, Stacks, Queues               | Hashmaps, Linked Lists, Tree Basics                  | Searching & Sorting Techniques, Big O             | **Quiz (20 Qs)** + *Assignment*: ER Queue simulation using priority + basic DS                 |
| **17th July** | OOP Principles in Healthcare Systems                 | Inheritance, Overriding, Encapsulation               | OOP Case Study: Doctor-Patient-Appointments       | **Quiz (20 Qs)** + *Assignment*: Implement mini HMS with OOP model in Python/Java              |
| **18th July** | Git Basics: init, add, commit, log                   | GitHub repo setup, branching, merging                | Pull Requests, Conflict Resolution, Collaboration | **Quiz (20 Qs)** + *Assignment*: Hospital app feature push + PR merge flow                     |
| **21st July** | Agile Manifesto, Scrum Roles & Ceremonies            | Product & Sprint Backlogs, Jira/Trello               | Sprint Simulation, Burndown Charts                | **Quiz (20 Qs)** + *Assignment*: Create sprint board with sample healthcare features in Trello |

---

### **Week 3: Front-End Development (Phase 3)**

#### **Case Study 1**: Accessible Patient Registration System

*Objective*: Build an HTML/CSS/JS form with WCAG-compliant validations for elderly users.

#### **Case Study 2**: Responsive Healthcare Provider Directory

*Objective*: Create a responsive provider listing using Grid/Flexbox with filter and display.

| **Day**   | **Session 1**                            | **Session 2**                             | **Session 3**                        | **Session 4: Assessment + Assignment**                                                               |
| --------- | ---------------------------------------- | ----------------------------------------- | ------------------------------------ | ---------------------------------------------------------------------------------------------------- |
| **22nd July** | HTML5 Structure, DOCTYPE, Meta Tags      | Forms: input, select, radio, tables       | Semantic HTML for Medical Forms      | **Quiz (20 Qs)** + *Assignment*: Multi-page clinic site with patient registration form               |
| **23rd July** | CSS Fundamentals, Box Model, Colors      | Flexbox for Layout, Typography            | Responsive Design with Media Queries | **Quiz (20 Qs)** + *Assignment*: Responsive styling for Day 1 site with Flexbox and CSS Grid         |
| **24th July** | JavaScript: Variables, Functions, Events | DOM Manipulation: Forms, Tables           | JS Form Validation with Feedback     | **Quiz (20 Qs)** + *Assignment*: Interactive appointment form with input validation and confirmation |
| **25th July** | WCAG, ADA, Accessibility Tools           | ARIA, Screen Reader Support, Keyboard Nav | Empathy in UI for Healthcare         | **Quiz (20 Qs)** + *Assignment*: Refactor Day 1 form to WCAG 2.1 using AXE, Lighthouse               |
| **28th July** | Dashboard Wireframe: Layout Plan         | Display Data (Cards, Tables), Navigation  | Form Handling + Accessibility        | **Quiz (20 Qs)** + *Assignment*: Build patient dashboard UI with listing + registration form         |

---

### **Week 4: Mobile App Development (Phase 4)**

#### **Case Study 1**: FHIR Appointment Booking App

*Objective*: Build a mobile app to fetch and book appointments using FHIR APIs.

#### **Case Study 2**: Medication Reminder App

*Objective*: Create an offline-first cross-platform app with notifications.

| **Day**   | **Session 1**                          | **Session 2**                          | **Session 3**                          | **Session 4: Assessment + Assignment**                                                            |
| --------- | -------------------------------------- | -------------------------------------- | -------------------------------------- | ------------------------------------------------------------------------------------------------- |
| **29th July** | Native vs Hybrid vs Cross-Platform     | Setup React Native & Flutter Envs      | Build Hello World + Navigation         | **Quiz (20 Qs)** + *Assignment*: Build basic Hello World + nav in RN & Flutter                    |
| **30th July** | Form Inputs, DatePickers, Dropdowns    | State Management, Validation Logic     | UI Feedback: Toast, Alerts, Focus Mgmt | **Quiz (20 Qs)** + *Assignment*: Build validated patient registration form in both RN and Flutter |
| **31st July** | REST API, JSON, HTTP/Fetch             | Connect to FHIR API (GET, POST)        | Offline Storage, Caching, Pagination   | **Quiz (20 Qs)** + *Assignment*: Integrate mock FHIR API to fetch/display appointments            |
| **1st Aug** | HTTPS, SSL Pinning, OAuth2, RBAC       | Secure Token Storage (AsyncStorage/SP) | HIPAA Mobile Checklist, OWASP          | **Quiz (20 Qs)** + *Assignment*: Secure login screen with encrypted token storage                 |
| **4th Aug** | Feature Finalization, Wireframe Design | CRUD for Meds, Schedule, Notify Logic  | Testing, Packaging, Review             | **Quiz (20 Qs)** + *Assignment*: Final medication reminder app with local storage & accessibility |

---


---

### **Week 5: Front-End Development with React (Phase 5 - Part 1)**

#### **Case Study 1**: Patient Record Viewer

*Objective*: Build a React-based application to view, search, and update patient records using a FHIR-compliant API.

#### **Case Study 2**: FHIR Appointment Dashboard

*Objective*: Develop a multi-page React app with stateful forms and routing to manage patient appointments.

| **Day**   | **Session 1**                                    | **Session 2**                                    | **Session 3**                                        | **Session 4: Assessment + Assignment**                                                                       |
| --------- | ------------------------------------------------ | ------------------------------------------------ | ---------------------------------------------------- | ------------------------------------------------------------------------------------------------------------ |
| **5th Aug** | Intro to React, Component-based Architecture     | Setting up Create React App, JSX Basics          | useState, Event Handling, Reusable UI (Card, Button) | **Quiz (20 Qs)** + *Assignment*: Build a patient dashboard UI with reusable components + form state          |
| **6th Aug** | React Router Setup and Route Navigation          | useParams, useNavigate, Multi-page Structure     | Controlled Forms, Custom Validation                  | **Quiz (20 Qs)** + *Assignment*: Build a patient intake multi-view app with validation and routing           |
| **7th Aug** | useEffect for API Calls, Fetch/axios Integration | Display FHIR API PatientList, Tables & Filters   | Pagination, Error Handling, Secure Token Storage     | **Quiz (20 Qs)** + *Assignment*: Connect to mock FHIR API and implement filtered PatientList with pagination |
| **8th Aug** | useContext and Global State Management           | Create Notification Context, Avoid Prop Drilling | useReducer/useCallback Preview, Performance          | **Quiz (20 Qs)** + *Assignment*: Create a shared patient session context and notification logic              |
| **11th Aug** | Project Planning, UI Component Structuring       | Hooking API Calls, Secure Form Editing           | Final Review, User Roles, Testing                    | **Quiz (20 Qs)** + *Assignment*: Build and deploy a mini React patient record app using mock FHIR API        |

---

### **Week 6: Front-End Development with Angular (Phase 5 - Part 2)**

#### **Case Study 1**: Angular Clinic Dashboard

*Objective*: Develop a full Angular-based UI for managing patient and appointment data with modular architecture.

#### **Case Study 2**: Appointment Manager with Angular Material

*Objective*: Implement appointment scheduling features using Angular services, routing, and RxJS.

| **Day**   | **Session 1**                                    | **Session 2**                                 | **Session 3**                               | **Session 4: Assessment + Assignment**                                                               |
| --------- | ------------------------------------------------ | --------------------------------------------- | ------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **12th Aug** | Angular Intro, CLI Setup, Component Architecture | Template Syntax, Data Binding, Directives     | Component Communication with @Input/@Output | **Quiz (20 Qs)** + *Assignment*: Build PatientList and PatientDetail component using Angular CLI     |
| **13th Aug** | Angular Routing and Navigation                   | Reactive Forms: Structure and Validation      | UI Enhancement using Angular Material       | **Quiz (20 Qs)** + *Assignment*: Build and route validated patient registration form to summary view |
| **14th Aug** | Angular Services and DI, HTTPClientModule        | API Connection to FHIR or Mock Backend        | Centralized Data Store using Services       | **Quiz (20 Qs)** + *Assignment*: Create PatientService and connect with list/detail views            |
| **18th Aug** | RxJS Subjects & BehaviorSubjects                 | State Sharing, Debouncing, Stream Composition | Live Search and NgRx Preview                | **Quiz (20 Qs)** + *Assignment*: Implement live search using RxJS and central state store            |
| **19th Aug** | Define UI: Patient List, Appointment Form        | Appointment Model, Submission, Auth Guards    | Role-Based Access and App Review            | **Quiz (20 Qs)** + *Assignment*: Build & deploy Angular appointment app connected to mock FHIR API   |

---

### **Week 7: Backend Development with Java (Spring Boot)**

#### **Case Study 1**: Secure Patient API with Spring Boot

*Objective*: Build a Spring Boot API for CRUD operations on patient and appointment data with JWT-based security.

#### **Case Study 2**: API Documentation & Deployment

*Objective*: Add Swagger/OpenAPI documentation and deploy a healthcare API to cloud.

| **Day**   | **Session 1**                      | **Session 2**                                  | **Session 3**                           | **Session 4: Assessment + Assignment**                                                              |
| --------- | ---------------------------------- | ---------------------------------------------- | --------------------------------------- | --------------------------------------------------------------------------------------------------- |
| **20th Aug** | Spring Boot Setup using Initializr | REST Controllers, Annotations, Embedded Tomcat | Setup H2 + Postman Testing              | **Quiz (20 Qs)** + *Assignment*: Spring Boot app with patient GET/POST endpoints                    |
| **21st Aug** | JPA + MySQL/PostgreSQL Integration | Entity Classes, CRUD Repos, DTOs, Services     | Exception Handling, Validation, Logging | **Quiz (20 Qs)** + *Assignment*: Implement patient + appointment CRUD with error management         |
| **22nd Aug** | REST Design, Endpoint Versioning   | Swagger UI + OpenAPI Integration               | API Testing, Deployment to Heroku       | **Quiz (20 Qs)** + *Assignment*: Document and deploy secure healthcare API with Swagger             |
| **25th Aug** | Spring Security Overview           | JWT Auth Setup, Role-based Access              | Token Validation & Secure Filters       | **Quiz (20 Qs)** + *Assignment*: Secure API with JWT login and Admin/Doctor roles                   |
| **26th Aug** | Model Design: Doctor, Appointment  | CRUD with Validation and Audit Logs            | Test API using Postman Suite            | **Quiz (20 Qs)** + *Assignment*: Build full Spring Boot REST API with JWT, deploy and test securely |

---

### **Week 8: Backend Development with Python (Django)**

#### **Case Study 1**: Django-based Clinic Backend

*Objective*: Develop backend APIs using Django and Django REST Framework to manage patient and appointment data.

#### **Case Study 2**: Online Consultation System

*Objective*: Implement secure login, role-based API access, and deploy Django backend for healthcare data.

| **Day**   | **Session 1**                          | **Session 2**                                    | **Session 3**                                | **Session 4: Assessment + Assignment**                                                        |
| --------- | -------------------------------------- | ------------------------------------------------ | -------------------------------------------- | --------------------------------------------------------------------------------------------- |
| **28th Aug** | Django Setup, Project/App Creation     | Models: Patient, Appointment, Admin Registration | URLConf, Views, Django Shell                 | **Quiz (20 Qs)** + *Assignment*: Create Patient model and register in Django Admin            |
| **29th Aug** | Function vs Class-Based Views          | Django Forms, Validation, Error Handling         | Bootstrap Integration + Template Inheritance | **Quiz (20 Qs)** + *Assignment*: Intake & appointment forms using Django templates            |
| **1st Sept** | DRF Setup: Serializers & ViewSets      | API URLs, JSON Response, Filtering               | Pagination, Permissions, Versioning          | **Quiz (20 Qs)** + *Assignment*: Build API for patient and appointment with DRF               |
| **2nd Sept** | Token-Based Auth with DRF SimpleJWT    | Role-Based Permissions, Swagger Docs             | Secure Views + Monitoring                    | **Quiz (20 Qs)** + *Assignment*: Add JWT auth + generate Swagger docs using drf-yasg          |
| **3rd Sept** | Models: Doctor, Prescription, Consults | Full CRUD API with JWT & Swagger                 | Deployment on Render or Heroku               | **Quiz (20 Qs)** + *Assignment*: Complete a Django REST project for managing medical consults |

---



---

### **Week 9: Backend Development with C# (.NET Core)**

#### **Case Study 1**: .NET Healthcare API for Patient & Appointment

*Objective*: Build a secure, RESTful .NET Core API managing patient and appointment data using EF Core and JWT authentication.

#### **Case Study 2**: Swagger-Based Appointment System for Clinics

*Objective*: Add OpenAPI docs, versioning, and deploy secure appointment APIs with cloud readiness.

| **Day**   | **Session 1**                    | **Session 2**                          | **Session 3**                            | **Session 4: Assessment + Assignment**                                                             |
| --------- | -------------------------------- | -------------------------------------- | ---------------------------------------- | -------------------------------------------------------------------------------------------------- |
| **4th Sept** | .NET Core Overview & SDK Setup   | Create Web API Project & Controller    | DI + Model Design (Patient, Appointment) | **Quiz (20 Qs)** + *Assignment*: Build GET/POST endpoints for patient in .NET Core API             |
| **5th Sept** | EF Core Config + SQL/PostgreSQL  | Entity Classes + Migrations            | Async CRUD + Repo Pattern, Logging       | **Quiz (20 Qs)** + *Assignment*: Full EF Core CRUD with error handling + validations               |
| **8th Sept** | REST Design & Routing            | Swagger/OpenAPI Docs                   | Versioning, Paging, FHIR Integration     | **Quiz (20 Qs)** + *Assignment*: Add Swagger docs + implement paging/filtering                     |
| **9th Sept** | ASP.NET Identity + JWT Auth      | Role-Based Policies + Secure Endpoints | CORS, HTTPS, OWASP Practices             | **Quiz (20 Qs)** + *Assignment*: Add JWT-based auth and RBAC on patient API                        |
| **10th Sept** | Domain Models + Security Wrap-up | Deploy to Azure App Service            | Integration & Review                     | **Quiz (20 Qs)** + *Assignment*: Capstone - Build & deploy full .NET Core Appointment API securely |

---

### **Week 10: Database Management & Cloud**

#### **Case Study 1**: Structured vs Unstructured Healthcare Records

*Objective*: Design normalized schemas for structured data (PACS, FHIR) and document-oriented NoSQL for EMR, RIS, IDM.

#### **Case Study 2**: Serverless Healthcare App on Cloud

*Objective*: Deploy scalable healthcare backend using serverless APIs, cloud DBs, and CI/CD automation.

| **Day**   | **Session 1**                         | **Session 2**                         | **Session 3**                       | **Session 4: Assessment + Assignment**                                                               |
| --------- | ------------------------------------- | ------------------------------------- | ----------------------------------- | ---------------------------------------------------------------------------------------------------- |
| **11th Sept** | Relational DBs + Postgres/MySQL Setup | SQL Queries & Schema Design           | JOINs, Indexing, Backup Strategies  | **Quiz (20 Qs)** + *Assignment*: Design patient-visit schema and write SQL queries                   |
| **12th Sept** | Intro to NoSQL (MongoDB Focus)        | Document Modeling + CRUD              | Aggregations, Indexing, Comparison  | **Quiz (20 Qs)** + *Assignment*: Model lab logs in MongoDB + Aggregation queries                     |
| **15th Sept** | Cloud Concepts: IaaS/PaaS/SaaS        | Setup EC2, Azure App Service          | Deploy Sample App, Serverless Intro | **Quiz (20 Qs)** + *Assignment*: Deploy app on EC2/Azure and explore Lambda/Functions                |
| **16th sept** | Deep Dive into Serverless + CI/CD     | Lambda + API Gateway + DB Integration | Logging, Auto-scaling, Monitoring   | **Quiz (20 Qs)** + *Assignment*: Build serverless REST API with DynamoDB                             |
| **17th Sept** | High Availability & Security          | HIPAA on Cloud, IAM Policies          | Final Scalable Cloud Architecture   | **Quiz (20 Qs)** + *Assignment*: Deploy healthcare records API with autoscaling, failover monitoring |

---

### **Week 11: Healthcare Security & Emerging Technologies**

#### **Case Study 1**: PHI Compliance with GitHub Copilot

*Objective*: Automate secure coding and auditing logic for HIPAA/GDPR.

#### **Case Study 2**: AI-Driven Symptom Classification + Remote Monitoring

*Objective*: Use AI/ML, secure remote monitoring, and real-time telemedicine tools for modern patient care.

| **Day**   | **Session 1**                         | **Session 2**                           | **Session 3**                         | **Session 4: Assessment + Assignment**                                                          |
| --------- | ------------------------------------- | --------------------------------------- | ------------------------------------- | ----------------------------------------------------------------------------------------------- |
| **18th Sept** | HIPAA & GDPR Overview                 | PHI, PII, Audit Logging, GitHub Copilot | Design Compliance-Ready Software      | **Quiz (20 Qs)** + *Assignment*: Use Copilot to log access and simulate audit for PHI data      |
| **19th Sept** | Encryption Techniques (AES, RSA, SHA) | OAuth2, OpenID, RBAC Models             | Secure API Design with JWT            | **Quiz (20 Qs)** + *Assignment*: Build secure login with RBAC + encrypted storage               |
| **22nd Sept** | Telemedicine Concepts, IoT Overview   | Device Integration + UI Design          | Simulate Remote Monitoring, APIs      | **Quiz (20 Qs)** + *Assignment*: Build telemedicine UI with mocked vital data stream            |
| **23rd Sept** | AI/ML in Diagnostics, XAI Concepts    | scikit-learn Workflow + Model Training  | GitHub Copilot for ML Pipelines       | **Quiz (20 Qs)** + *Assignment*: Train a symptom classifier using sklearn + deploy with Copilot |
| **24th Sept** | Big Data Tools (Hadoop, Spark)        | Wearable Ingestion + Realtime Pipeline  | Capstone Pipeline with Visualizations | **Quiz (20 Qs)** + *Assignment*: Hadoop/Spark demo + visualizations with security enforced      |

---

### **Week 12: Capstone Project & Final Evaluation**

#### **Capstone Theme**: Secure, Interoperable Healthcare Management System

| **Day**   | **Session 1**                                  | **Session 2**                        | **Session 3**                           | **Session 4: Capstone Deliverables**                             |
| --------- | ---------------------------------------------- | ------------------------------------ | --------------------------------------- | ---------------------------------------------------------------- |
| **25th Sept** | Project Kickoff, Team Setup, Git Repo          | Define Architecture: React/.NET/FHIR | Define Compliance Scope (HIPAA/GDPR)    | Initialize GitHub repo, Wiki, Agile board with tech stack        |
| **26th Sept** | Database + Backend Design (Relational & NoSQL) | REST APIs + OAuth2/JWT               | Swagger, CI/CD + Security Layers        | Deliver Secure API module with Swagger and Unit Tests            |
| **29th Sept** | Frontend Build: Dashboard + Forms              | Integrate APIs, Telemedicine UI      | State Mgmt, Deployment, Responsive UI   | Build + Deploy Frontend with test coverage (WCAG + HTTPS)        |
| **30th Sept** | AI/ML Feature: Classifier API                  | Big Data Stream Ingestion + Charts   | Analytics Dashboard + Final Integration | Deploy AI pipeline + integrate with frontend dashboards securely |
| **1st Oct** | Team Demo & Presentation                       | Evaluation (UI, Security, Interop)   | Written + Oral Assessment               | Final Capstone App Presentation + Certificate + Career Roadmap   |

---



# Software Requirements Specification (SRS) — HomeSafe Smart Security

ឯកសារនេះប្រែ User Requirements (សូមមើល `URD/URD.md`) ទៅជា Software Requirements ជាក់លាក់ ដោយប្រើ Structure តាម Wiegers SRS Template ដែលបានលើកឡើងក្នុង *Software Engineering: A Practitioner's Approach* (Pressman, 7th Ed., Chapter 5)។

---

## 1. Introduction

### 1.1 Purpose
ឯកសារនេះកំណត់ Software Requirements ទាំងអស់សម្រាប់ HomeSafe Smart Security System — Version 1.0 (Increment 1–5)។

### 1.2 Document Conventions
`FR-XX` = Functional Requirement, `NFR-XX` = Non-Functional Requirement។ Priority Level: Essential / Moderate / Optional។

### 1.3 Intended Audience and Reading Suggestions
Developer Team, QA/Tester, Project Supervisor, និង Stakeholder ដែលត្រូវការ Technical Detail។ URD សម្រាប់ Non-Technical Reader, SRS សម្រាប់ Technical Reader។

### 1.4 Project Scope
HomeSafe គ្របដណ្តប់ Authentication, Security Modes, Sensor Monitoring, Alarm, Notification, Video Surveillance, Remote Access, និង Device Management — ដាក់ឱ្យប្រើតាម Incremental Model (5 Increments)។ Out of Scope: Third-Party Home Automation Integration (ឧ. Smart Light, Thermostat) សម្រាប់ Version 1.0។

### 1.5 References
- Pressman, R. S. *Software Engineering: A Practitioner's Approach*, 7th Edition
- `Process_Model/` — Incremental Model, Agile Scrum, V-Model
- `Diagram/class_diagram.md`, `Diagram/use_case_diagram.md`

---

## 2. Overall Description

### 2.1 Product Perspective
HomeSafe គឺជា New, Self-Contained Product Line — មិនមែនជា Modification នៃ Existing System ទេ។ វារួមមាន Local Control Hub (Hardware), Mobile Application (iOS/Android), និង Backend Server (Cloud)។

### 2.2 Product Features (High-Level)
Authentication, Arm/Disarm, Security Modes, Sensor Monitoring, Alarm, Notification, Camera Streaming/Recording, Event History, Device Management — សូមមើលព័ត៌មានលម្អិតក្នុង Section 3 (System Features)។

### 2.3 User Classes and Characteristics
សូមមើល `URD/URD.md` Section 3 (Homeowner, Family Member, Guest, Administrator, IoT Devices)។

### 2.4 Operating Environment
សូមមើល `URD/URD.md` Section 4 (Mobile OS versions, Hub connectivity, Sensor/Camera protocol)។

### 2.5 Design and Implementation Constraints
សូមមើល `URD/URD.md` Section 5 (Protocol Interoperability, Third-Party Notification Service, Encryption Standard, Backup Power, Scalability Limit)។

### 2.6 User Documentation
Mobile App ត្រូវមាន In-App Onboarding Guide។ Hub ត្រូវភ្ជាប់ជាមួយ Quick-Start Installation Guide (Printed/PDF)។

### 2.7 Assumptions and Dependencies
សូមមើល `URD/URD.md` Section 6។

---

## 3. System Features (Functional Requirements)

| ID | Feature | Description | Priority |
|---|---|---|---|
| **FR-01** | User Authentication | System ត្រូវ Authenticate User (PIN/Fingerprint/Mobile Credential) មុនពេលអនុញ្ញាតឱ្យប្រើ Protected Functions | Essential |
| **FR-02** | Arm/Disarm | System ត្រូវអនុញ្ញាតឱ្យ User ដែលមានសិទ្ធិ ប្តូរ Home, Away និង Disarm Mode | Essential |
| **FR-03** | Security Modes | System ត្រូវគាំទ្រ Home, Away, Disarm និង Scheduled Mode | Essential |
| **FR-04** | Sensor Monitoring | System ត្រូវត្រួតពិនិត្យ Sensors ដែលបានកំណត់ជាបន្តបន្ទាប់ (Motion, Door/Window, Glass-Break) | Essential |
| **FR-05** | Intrusion Detection | System ត្រូវរកឃើញ Intrusion តាម Sensor Input និង Active Security Mode | Essential |
| **FR-06** | Alarm | System ត្រូវ Activate Siren នៅពេលមាន Configured Intrusion Event | Essential |
| **FR-07** | Notification | System ត្រូវផ្ញើ Push Notification ឬ SMS នៅពេលមាន Security Event | Moderate |
| **FR-08** | Camera Streaming | System ត្រូវផ្តល់ Live Video សម្រាប់ Authorized Users | Moderate |
| **FR-09** | Automatic Recording | System ត្រូវចាប់ផ្តើម Recording ស្វ័យប្រវត្តិនៅពេលមាន Motion/Security Event | Moderate |
| **FR-10** | Event History | System ត្រូវរក្សាទុក Security Events (Type, Device, Timestamp, Status, Recording Link) សម្រាប់ពិនិត្យពេលក្រោយ | Moderate |
| **FR-11** | Device Management | Admin ត្រូវអាច Add, Remove និង Configure IoT Devices | Optional (Increment 1 foundation, refined later) |

---

## 4. External Interface Requirements

### 4.1 User Interfaces
- **Mobile Application** — Dashboard (System Status), Arm/Disarm Control, Camera Viewer, Notification Center, Event History List, Device Management Screen (Admin only)
- **Local Control Panel (Hub Display/Keypad)** — LCD Display + LED Indicators + Keypad សម្រាប់ PIN Entry, Arm/Disarm, Panic Button

### 4.2 Hardware Interfaces
- **Motion / Door-Window / Glass-Break Sensors** — ភ្ជាប់ទៅ Hub តាម Wireless Protocol (ឧ. Zigbee/Z-Wave) ឬ Wired Contact
- **Camera** — ភ្ជាប់ទៅ Hub/Network តាម WiFi ឬ PoE, គាំទ្រ Pan/Zoom (ប្រសិនបើមាន)
- **Siren/Alarm Actuator** — Digital Output ពី Hub, Activate/Deactivate តាម Alarm Event
- **Local Control Hub** — Central Processing Unit ដែលភ្ជាប់ Sensors, Camera, និង Internet Gateway

### 4.3 Software Interfaces
- **Backend Database** — រក្សាទុក User Credential, Device Config, Event History (Cloud-hosted, ឧ. Managed SQL/NoSQL Service)
- **Push Notification Service** — Third-Party API (ឧ. Firebase Cloud Messaging) សម្រាប់ FR-07
- **SMS Gateway** — Third-Party API (ឧ. Twilio ឬ Local Telecom Provider) សម្រាប់ FR-07
- **Mobile App ↔ Backend API** — RESTful API តាម HTTPS, JSON Payload

### 4.4 Communications Interfaces
- **Hub ↔ Sensors/Camera** — Local Wireless Protocol (Zigbee/Z-Wave) ឬ Wired, Low-Latency
- **Hub ↔ Backend Server** — Internet Connection (WiFi/4G Backup), HTTPS/MQTT សម្រាប់ Real-Time Event Push
- **Mobile App ↔ Backend Server** — HTTPS REST API, WebSocket/MQTT សម្រាប់ Live Camera Streaming និង Real-Time Alert

---

## 5. Other Nonfunctional Requirements

### 5.1 Reliability
- Target Availability = 99.9% ក្នុងលក្ខខណ្ឌដែលបានកំណត់
- Critical Components (Hub, Alarm) គួរគាំទ្រ Backup Power

### 5.2 Security
- Authentication និង Authorization សម្រាប់រាល់ Protected Function
- ការពារ Data និង Communication ដោយ Encryption (AES-256 ជា Target)

### 5.3 Performance
- Target Alert Delivery ≤ 2 វិនាទី បន្ទាប់ពី Sensor Trigger

### 5.4 Scalability
- គាំទ្រ IoT Devices រហូតដល់ 50 Devices ក្នុង Household Hub

### 5.5 Usability
- Mobile App Interface ងាយយល់, ត្រូវការការកំណត់តិចសម្រាប់ Non-Technical User

### 5.6 Maintainability
- System ត្រូវបែងជា Modules ដើម្បីងាយ Fix Bug, Update Security, បន្ថែម Device ប្រភេទថ្មី

---

## 6. Other Requirements

Testing & Verification Requirements — សូមមើល `Process_Model/` និង Section 12 (Testing and Verification) ក្នុងឯកសារដើម សម្រាប់ Test Case Table ដែលភ្ជាប់ជាមួយ FR-01 ដល់ FR-11 ។

---

## Appendix A: Glossary

| Term | និយមន័យ |
|---|---|
| **Arm** | ដំណើរការ Activate Security Monitoring |
| **Disarm** | បិទ Security Monitoring |
| **Zone** | តំបន់ដែល Sensor ជាក់លាក់គ្របដណ្តប់ (ឧ. Perimeter, Interior) |
| **Intrusion** | Event ដែល System កំណត់ថាមាន Unauthorized Entry |
| **Hub** | Local Control Device ដែលភ្ជាប់ Sensors, Camera, និង Internet |
| **Increment** | ដំណាក់កាលអភិវឌ្ឍតាម Incremental Model (សូមមើល `Process_Model/`) |
| **FR / NFR** | Functional Requirement / Non-Functional Requirement |
| **Push Notification** | សារជូនដំណឹងផ្ញើទៅ Mobile App ដោយផ្ទាល់ (មិនមែន SMS) |

## Appendix B: Analysis Models

- `Diagram/class_diagram.md` — Class Diagram (System, Sensor, ControlPanel, Camera, User, ជាដើម)
- `Diagram/use_case_diagram.md` — Use Case Diagram (Homeowner, Sensors, Cameras, Administrator)

## Appendix C: Issues List (Open Issues)

1. តើ Push Notification Service ណាមួយ (Firebase, OneSignal, ...) ត្រូវជ្រើសរើសសម្រាប់ Production?
2. តើ Bandwidth ត្រូវការប៉ុន្មានសម្រាប់ Live Camera Streaming ជាមួយ User ច្រើននាក់ក្នុងពេលតែមួយ?
3. តើ Hub ត្រូវការ Battery Backup យូរប៉ុន្មាននាទី/ម៉ោង នៅពេលអគ្គិសនីដាច់?
4. តើ Guest Access ត្រូវផុតកំណត់ស្វ័យប្រវត្តិដោយរបៀបណា (Time-based, Manual Revoke)?
5. តើ Data Retention Policy សម្រាប់ Recording/Event History គួរជាប៉ុន្មានថ្ងៃ/ខែ?

---

## Reference

Wiegers, K. — SRS Template (cited in Pressman, R. S. *Software Engineering: A Practitioner's Approach*, 7th Edition, Chapter 5, "Software Requirements Specification Template").

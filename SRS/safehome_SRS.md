# Software Requirements Specification (SRS)
## HomeSafe Smart Security

**Project Type:** Software Engineering Case Study
**Document:** Software Requirements Specification
**Related Document:** [`URD.md`](./URD.md) — User Requirements Document
**ភាសា:** Khmer / English (Bilingual)

---

## 1. Purpose

> SRS ប្រែ User Requirements ទៅជា Software Requirements ជាក់លាក់។ វាឆ្លើយសំណួរ៖ **«System ត្រូវធ្វើអ្វី?»**
> *(SRS translates user requirements into concrete software requirements. It answers: "What must the system do?")*

This document specifies the functional and non-functional requirements, system design, process model, and testing strategy for HomeSafe Smart Security, based on the requirements captured in the URD.

---

## 2. System Overview

HomeSafe is an IoT-based Smart Home Security system connecting sensors, cameras, a local control hub, an alarm/notification layer, and a mobile application, enabling homeowners to monitor and secure their homes locally and remotely.

**Actors:** Homeowner, Family Member, Guest, Administrator, IoT Sensors, Security Camera.

---

## 3. Functional Requirements

| ID | Title | Requirement |
|---|---|---|
| **FR-01** | User Authentication | System ត្រូវ Authenticate User មុនពេលអនុញ្ញាតឱ្យប្រើ Protected Functions។ *The system must authenticate the user before granting access to protected functions.* |
| **FR-02** | Arm/Disarm | System ត្រូវអនុញ្ញាតឱ្យ User ដែលមានសិទ្ធិ ប្តូរ Home, Away និង Disarm Mode។ *The system must allow authorized users to switch between Home, Away, and Disarm modes.* |
| **FR-03** | Security Modes | System ត្រូវគាំទ្រ Home, Away, Disarm និង Scheduled Mode។ *The system must support Home, Away, Disarm, and Scheduled modes.* |
| **FR-04** | Sensor Monitoring | System ត្រូវត្រួតពិនិត្យ Sensors ដែលបានកំណត់ជាបន្តបន្ទាប់។ *The system must continuously monitor configured sensors.* |
| **FR-05** | Intrusion Detection | System ត្រូវរកឃើញ Intrusion តាម Sensor Input និង Active Security Mode។ *The system must detect intrusions based on sensor input and the active security mode.* |
| **FR-06** | Alarm | System ត្រូវ Activate Siren នៅពេលមាន Configured Intrusion Event។ *The system must activate the siren when a configured intrusion event occurs.* |
| **FR-07** | Notification | System ត្រូវផ្ញើ Push Notification ឬ SMS នៅពេលមាន Security Event។ *The system must send a push notification or SMS when a security event occurs.* |
| **FR-08** | Camera Streaming | System ត្រូវផ្តល់ Live Video សម្រាប់ Authorized Users។ *The system must provide live video to authorized users.* |
| **FR-09** | Automatic Recording | System ត្រូវចាប់ផ្តើម Recording ដោយស្វ័យប្រវត្តិនៅពេលមាន Motion/Security Event ដែលបានកំណត់។ *The system must automatically start recording on a configured motion/security event.* |
| **FR-10** | Event History | System ត្រូវរក្សាទុក Security Events សម្រាប់ពិនិត្យពេលក្រោយ។ *The system must store security events for later review.* |
| **FR-11** | Device Management | Admin ត្រូវអាច Add, Remove និង Configure IoT Devices។ *The Administrator must be able to add, remove, and configure IoT devices.* |

### 3.1 Event History Fields
Each logged event includes:
- ប្រភេទ Event (Event Type)
- Device
- ថ្ងៃ/ម៉ោង (Date/Time)
- Status
- Recording ដែលពាក់ព័ន្ធ (Related recording, if any)

---

## 4. Non-Functional Requirements

> Non-Functional Requirements ប្រាប់ថា System ត្រូវដំណើរការមានគុណភាពបែបណា។
> *(Non-functional requirements describe the quality attributes the system must have.)*

| Category | Requirement |
|---|---|
| **4.1 Reliability** | Target Availability = 99.9% ក្នុងលក្ខខណ្ឌដែលបានកំណត់ (under defined conditions). Critical components should support backup power. |
| **4.2 Security** | Authentication and authorization required; data and communication protected by encryption; **AES-256** may be set as the project's design-level security target. |
| **4.3 Performance** | Target alert delivery ≤ **2 seconds** after sensor trigger, under defined test conditions. |
| **4.4 Scalability** | Initial target: support up to **50 IoT devices** per household hub. |
| **4.5 Usability** | Mobile app should have an easy-to-understand interface requiring minimal configuration for non-technical users. |
| **4.6 Maintainability** | System should be divided into modules to ease bug fixes, security updates, and adding new device types. |

---

## 5. System Design

### 5.1 High-Level Architecture
```
User
  ↓
Mobile / Web App
  ↓
Backend / API
  ↓
Database  +  Local Control Hub
  ↓
Sensors / Cameras / Alarm
```

### 5.2 Components
- Mobile Application
- Backend / API
- Local Control Hub
- Database
- Sensor Layer
- Camera Layer
- Alarm / Notification Layer

### 5.3 Data Entities

| Entity | Fields |
|---|---|
| **Users** | UserID, Name, Contact, Role, Authentication Data |
| **Devices** | DeviceID, Name, Type, Status |
| **SecurityEvents** | EventID, DeviceID, EventType, DateTime, Status |
| **Cameras** | CameraID, Name, Status |
| **Recordings** | RecordingID, CameraID, EventID, File Reference |

---

## 6. Process Model

### 6.1 Primary Model — Incremental Development Model
យើងជ្រើស Incremental Model ជា Process Model សំខាន់ ព្រោះ HomeSafe មាន Features ជាច្រើនដែលអាចបែងចែកអភិវឌ្ឍ និង Test ជាដំណាក់កាល។
*(Chosen because HomeSafe has many features that can be developed and tested in stages: reduces risk, delivers usable versions early, eases adding IoT devices, and supports iterative feedback.)*

| Increment | Scope |
|---|---|
| **1 — Core Foundation** | Local Control Hub, Database, Authentication, Basic Device Control, Basic System Status |
| **2 — Remote Access** | Mobile Application, Wireless/Network Connectivity, Remote Access, Remote Arm/Disarm, Device Status |
| **3 — Security Monitoring** | Motion Sensor, Door/Window Sensors, Glass-Break Sensor, Intrusion Detection, Alarm/Siren |
| **4 — Surveillance** | Security Camera, Live Streaming, Motion-triggered Recording, Video Storage, Recording History |
| **5 — Alerts & Automation** | Push Notification, SMS Alert, Scheduled Arming/Disarming, Automation Rules, Event History, Device Management |

### 6.2 Supporting Practices
| Practice | Purpose |
|---|---|
| **Prototype Model** | Test hardware compatibility, UI concept, sensor communication, camera integration, and alarm before full build. |
| **Agile Scrum** | Short sprints (Sprint 1: Login, Sprint 2: Arm/Disarm, Sprint 3: Sensors, Sprint 4: Camera, Sprint 5: Notification) with planning, development, testing, review, and feedback. |
| **V-Model Principles** | Verification & validation for critical security features (Authentication, Intrusion Detection, Alarm, Notification): Requirement → Design → Implementation → Testing. |

### 6.3 Process Model Summary

| Model | Role | Status |
|---|---|---|
| Incremental Model | Develop HomeSafe in increments and test in stages | Primary |
| Prototype Model | Test hardware, UI, and IoT compatibility | Supporting |
| Agile Scrum | Short sprints, feedback, continuous improvement | Supporting |
| V-Model Principles | Verification/validation for critical security features | Supporting |

---

## 7. Testing and Verification

### 7.1 Test Levels
- **Unit Testing** — tests small functions, e.g. Login.
- **Integration Testing** — tests Sensor → Hub → Alarm.
- **System Testing** — tests the entire workflow end-to-end.
- **Acceptance Testing** — user verifies the system meets requirements.

### 7.2 Sample Test Cases

| Test | Condition/Input | Expected Result | Requirement |
|---|---|---|---|
| Login | Correct PIN | Login successful | FR-01 |
| Login | Wrong PIN | Access Denied | FR-01 |
| Arm | Authorized User | System Armed | FR-02 |
| Disarm | Authorized User | System Disarmed | FR-02 |
| Motion | Motion in Away Mode | Security Event Created | FR-04 / FR-05 |
| Intrusion | Configured Intrusion | Alarm Activated | FR-05 / FR-06 |
| Alert | Security Event | Notification Sent | FR-07 |
| Camera | Authorized User | Live Stream | FR-08 |
| Recording | Motion/Security Event | Video Recorded | FR-09 |

---

## 8. Security and Risk Management

| Risk | Problem | Mitigation |
|---|---|---|
| **Internet Failure** | Remote access may not work | Local Control Hub should continue basic security functions by design |
| **Power Failure** | Devices may stop working | Backup battery for critical components |
| **False Alarm** | Sensor may trigger incorrectly | Configurable sensitivity/detection rules, event verification by design |
| **Unauthorized Access** | Unauthorized users may attempt system access | Authentication, role-based authorization, encryption, logging, security updates |

---

## 9. Deployment

1. Install and configure the Local Control Hub.
2. Install and connect Sensors/Cameras.
3. Create Users and Roles.
4. Configure Security Modes and Automation Rules.
5. Perform Integration and Acceptance Testing.
6. Deploy the system for use.

---

## 10. Maintenance

- Fix bugs
- Security updates
- IoT device updates
- Database backup/recovery
- Performance monitoring
- Log review
- Support for new devices
- Feature improvements

---

## 11. Traceability

This SRS implements the requirements captured in [`URD.md`](./URD.md). Each functional requirement (FR-01–FR-11) traces back to one or more URS items (Section 5 of the URD) and forward to the test cases in Section 7 of this document.

---

## 12. Conclusion

HomeSafe Smart Security is a Smart Home Security system using IoT to provide secure access, continuous sensor monitoring, real-time alerts, remote control, and video surveillance. It supports Home/Away/Disarm modes, user roles, automated responses, and security event management. The Incremental Development Model was chosen as the primary process model because HomeSafe's features can be developed and tested in stages; the Prototype Model helps validate hardware/UI early, Agile Scrum keeps development flexible and feedback-driven, and V-Model principles support verification and validation of critical security features. The overall goal is a secure, reliable, scalable, maintainable, and easy-to-use system for residential use.

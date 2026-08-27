### 6.4 Relationship សំខាន់ៗ

Homeowner មាន Interaction ជាមួយ Login, Arm/Disarm, Camera, Alerts និង Recordings។ Admin គ្រប់គ្រង Users និង Devices។ Sensors ជា Source នៃ Security Events ហើយ System ឆ្លើយតបតាម Mode និង Rules ដែលបានកំណត់។

---

## 7. Software Requirements Specification (SRS)

SRS ប្រែ User Requirements ទៅជា Software Requirements ជាក់លាក់។ វាឆ្លើយសំណួរ៖ «System ត្រូវធ្វើអ្វី?»

### 7.1 Functional Requirements

- **FR-01 – User Authentication:** System ត្រូវ Authenticate User មុនពេលអនុញ្ញាតឱ្យប្រើ Protected Functions។
- **FR-02 – Arm/Disarm:** System ត្រូវអនុញ្ញាតឱ្យ User ដែលមានសិទ្ធិ ប្តូរ Home, Away និង Disarm Mode។
- **FR-03 – Security Modes:** System ត្រូវគាំទ្រ Home, Away, Disarm និង Scheduled Mode។
- **FR-04 – Sensor Monitoring:** System ត្រូវត្រួតពិនិត្យ Sensors ដែលបានកំណត់ជាបន្តបន្ទាប់។
- **FR-05 – Intrusion Detection:** System ត្រូវរកឃើញ Intrusion តាម Sensor Input និង Active Security Mode។
- **FR-06 – Alarm:** System ត្រូវ Activate Siren នៅពេលមាន Configured Intrusion Event។
- **FR-07 – Notification:** System ត្រូវផ្ញើ Push Notification ឬ SMS នៅពេលមាន Security Event។
- **FR-08 – Camera Streaming:** System ត្រូវផ្តល់ Live Video សម្រាប់ Authorized Users។
- **FR-09 – Automatic Recording:** System ត្រូវចាប់ផ្តើម Recording ដោយស្វ័យប្រវត្តិនៅពេលមាន Motion/Security Event ដែលបានកំណត់។
- **FR-10 – Event History:** System ត្រូវរក្សាទុក Security Events សម្រាប់ពិនិត្យពេលក្រោយ។
- **FR-11 – Device Management:** Admin ត្រូវអាច Add, Remove និង Configure IoT Devices។

### 7.2 Event History Details

- ប្រភេទ Event
- Device
- ថ្ងៃ/ម៉ោង
- Status
- Recording ដែលពាក់ព័ន្ធ

---

## 8. Non-Functional Requirements

### 8.1 Reliability

- Target Availability = 99.9% ក្នុងលក្ខខណ្ឌដែលបានកំណត់
- Critical Components គួរគាំទ្រ Backup Power

### 8.2 Security

- Authentication និង Authorization
- ការពារ Data និង Communication ដោយ Encryption
- អាចកំណត់ AES-256 ជា Project Security Target តាមការរចនា

### 8.3 Performance

- Target Alert Delivery ≤ 2 វិនាទី បន្ទាប់ពី Sensor Trigger ក្រោមលក្ខខណ្ឌ Test ដែលបានកំណត់។

### 8.4 Scalability

- គោលដៅដំបូងគឺគាំទ្រ IoT Devices រហូតដល់ 50 Devices ក្នុង Household Hub។

### 8.5 Usability

- Mobile App គួរមាន Interface ងាយយល់ និងត្រូវការការកំណត់តិចសម្រាប់អ្នកប្រើដែលមិនមែនជាអ្នកបច្ចេកទេស។

### 8.6 Maintainability

- System គួរត្រូវបានបែងជា Modules ដើម្បីងាយ Fix Bug, Update Security និងបន្ថែម Device ប្រភេទថ្មី។

---

## 9. System Design

### 9.1 High-Level Architecture

### 9.2 Components

- Mobile Application
- Backend / API
- Local Control Hub
- Database
- Sensor Layer
- Camera Layer
- Alarm / Notification Layer

### 9.3 Data Entities

- **Users:** UserID, Name, Contact, Role, Authentication Data
- **Devices:** DeviceID, Name, Type, Status
- **SecurityEvents:** EventID, DeviceID, EventType, DateTime, Status
- **Cameras:** CameraID, Name, Status
- **Recordings:** RecordingID, CameraID, EventID, File Reference

---

## 10. Process Model

### 10.1 Primary Model – Incremental Development Model

យើងជ្រើស Incremental Model ជា Process Model សំខាន់ ព្រោះ HomeSafe មាន Features ជាច្រើនដែលអាចបែងចែកអភិវឌ្ឍ និង Test ជាដំណាក់កាល។

- អភិវឌ្ឍជាផ្នែកៗ
- Test មួយ Increment ម្តង
- កាត់បន្ថយ Risk
- អាចផ្តល់ Version ដែលប្រើបានមុន
- ងាយបន្ថែម IoT Devices
- ងាយទទួល Feedback និងកែលម្អ

### 10.2 Increments Overview

| Increment       | Module / Features                                                      | Focus / Target      |
| :-------------- | :--------------------------------------------------------------------- | :------------------ |
| **Increment 1** | Local Control Hub, Database, Authentication, Basic Device Control      | Core Foundation     |
| **Increment 2** | Mobile App, Wireless Connectivity, Remote Arm/Disarm, Device Status    | Remote Access       |
| **Increment 3** | Motion, Door/Window, Glass-Break Sensors, Intrusion Engine, Siren      | Security Monitoring |
| **Increment 4** | Security Camera, Live Streaming, Motion Recording, Video Storage       | Surveillance        |
| **Increment 5** | Push Notification, SMS, Scheduled Arming, Automation Rules, Management | Alerts & Automation |

---

## 11. Supporting Process Models / Practices

- **11.1 Prototype Model:** ប្រើសម្រាប់សាកល្បង Hardware Compatibility, UI Concept, Sensor Communication, Camera Integration និង Alarm មុនពេល Build ប្រព័ន្ធពេញលេញ។
- **11.2 Agile Scrum:** ប្រើ Short Sprints, Planning, Development, Testing, Review និង Feedback ដើម្បីកែលម្អ System ជាបន្តបន្ទាប់ (ឧទាហរណ៍៖ Sprint 1 – Login; Sprint 2 – Arm/Disarm; Sprint 3 – Sensors; Sprint 4 – Camera; Sprint 5 – Notification)។
- **11.3 V-Model Principles:** ប្រើ Verification និង Validation សម្រាប់ Security Features ដែលសំខាន់ ដូចជា Authentication, Intrusion Detection, Alarm និង Notification (Requirement ➔ Design ➔ Implementation ➔ Testing)។

---

## 12. Testing and Verification

### 12.1 ប្រភេទ Testing

- **Unit Testing:** Test Function តូចៗ ដូចជា Login។
- **Integration Testing:** Test Sensor ➔ Hub ➔ Alarm។
- **System Testing:** Test Workflow ទាំងមូល។
- **Acceptance Testing:** User ពិនិត្យថា System បំពេញ Requirements ឬអត់។

### 12.2 Test Cases Matrix

| Test Case     | Condition / Input      | Expected Result        | Requirement |
| :------------ | :--------------------- | :--------------------- | :---------- |
| **Login**     | PIN ត្រឹមត្រូវ         | Login បានជោគជ័យ        | FR-01       |
| **Login**     | PIN ខុស                | Access Denied          | FR-01       |
| **Arm**       | Authorized User        | System Armed           | FR-02       |
| **Disarm**    | Authorized User        | System Disarmed        | FR-02       |
| **Motion**    | Motion ក្នុង Away Mode | Security Event Created | FR-04/05    |
| **Intrusion** | Configured Intrusion   | Alarm Activated        | FR-05/06    |
| **Alert**     | Security Event         | Notification Sent      | FR-07       |
| **Camera**    | Authorized User        | Live Stream            | FR-08       |
| **Recording** | Motion/Security Event  | Video Recorded         | FR-09       |

---

## 13. Security និង Risk Management

- **13.1 Internet Failure:** Remote Access អាចមិនដំណើរការ ➔ Local Control Hub គួរបន្តមុខងារ Security មូលដ្ឋានបានតាមការរចនា។
- **13.2 Power Failure:** Devices អាចឈប់ដំណើរការ ➔ Backup Battery សម្រាប់ Critical Components។
- **13.3 False Alarm:** Sensor អាច Trigger ខុស ➔ កំណត់ Sensitivity និង Detection Rules និងប្រើ Event Verification តាមការរចនា។
- **13.4 Unauthorized Access:** អ្នកគ្មានសិទ្ធិអាចព្យាយាមចូល System ➔ Authentication, Role-based Authorization, Encryption, Logging និង Security Updates។

---

## 14. Deployment

1. ដំឡើង និង Configure Local Control Hub។
2. ដំឡើង និងភ្ជាប់ Sensors/Cameras។
3. បង្កើត Users និង Roles។
4. កំណត់ Security Modes និង Automation Rules។
5. ធ្វើ Integration និង Acceptance Testing។
6. ដាក់ System ឱ្យប្រើប្រាស់។

---

## 15. Maintenance

- Fix Bugs & Security Updates
- IoT Device Updates
- Database Backup/Recovery
- Performance Monitoring & Log Review
- Support New Devices & Feature Improvements

---

## 16. Project Flow សរុប

### 16.1 អត្ថន័យរបស់ជំហាននីមួយៗ

- **Problem:** កំណត់បញ្ហាដែលត្រូវដោះស្រាយ។
- **Objectives:** កំណត់អ្វីដែល Project ចង់សម្រេច។
- **Scope:** កំណត់អ្វីមាន និងមិនមានក្នុង Project។
- **URS:** កំណត់អ្វីដែល User ត្រូវការ។
- **Use Case:** បង្ហាញ User/Actor Interaction ជាមួយ System។
- **SRS:** កំណត់អ្វីដែល Software ត្រូវធ្វើ។
- **Design:** កំណត់របៀបដែល System នឹងត្រូវសាងសង់។
- **Process Model:** កំណត់របៀបរៀបចំ និងដំណើរការ Development។
- **Development:** សរសេរ និងបង្កើត System។
- **Testing:** ពិនិត្យថា System ដំណើរការត្រឹមត្រូវ។
- **Deployment:** ដាក់ System ឱ្យប្រើប្រាស់។
- **Maintenance:** កែ Bug, Update និងបន្ថែមមុខងារ។

---

## 17. សេចក្តីសន្និដ្ឋាន (Conclusion)

HomeSafe Smart Security គឺជាប្រព័ន្ធ Smart Home Security ដែលប្រើ IoT ដើម្បីផ្តល់ Secure Access, Continuous Sensor Monitoring, Real-Time Alerts, Remote Control និង Video Surveillance។ ប្រព័ន្ធគាំទ្រ Home/Away/Disarm Modes, User Roles, Automated Responses និង Security Event Management។

Incremental Development Model ត្រូវបានជ្រើសជាម៉ូដែលសំខាន់ ព្រោះ Features របស់ HomeSafe អាចអភិវឌ្ឍ និង Test ជាផ្នែកៗ។ Prototype អាចជួយសាកល្បង Hardware/UI មុន, Agile Scrum ជួយឱ្យ Development មានភាពបត់បែន និងទទួល Feedback, ខណៈ V-Model Principles ជួយ Verification និង Validation នៃ Security Features សំខាន់ៗ។

គោលដៅចុងក្រោយគឺបង្កើតប្រព័ន្ធដែលមានសុវត្ថិភាព ជឿជាក់ អាចពង្រីកបាន ងាយថែទាំ និងងាយប្រើប្រាស់សម្រាប់លំនៅដ្ឋាន។

---

## 18. សង្ខេប Process Models

| Model                  | តួនាទី                                                     | ស្ថានភាព   |
| :--------------------- | :--------------------------------------------------------- | :--------- |
| **Incremental Model**  | អភិវឌ្ឍ HomeSafe ជា Increments និង Test ជាដំណាក់កាល        | Primary    |
| **Prototype Model**    | សាកល្បង Hardware, UI និង IoT Compatibility                 | Supporting |
| **Agile Scrum**        | Short Sprints, Feedback និង Continuous Improvement         | Supporting |
| **V-Model Principles** | Verification/Validation សម្រាប់ Critical Security Features | Supporting |

"""

filename = "HomeSafe_Smart_Security_Case_Study.md"
with open(filename, "w", encoding="utf-8") as f:
f.write(content)

print(f"File created: {filename}")

### 6.4 Relationship សំខាន់ៗ

Homeowner មាន Interaction ជាមួយ Login, Arm/Disarm, Camera, Alerts និង Recordings។ Admin គ្រប់គ្រង Users និង Devices។ Sensors ជា Source នៃ Security Events ហើយ System ឆ្លើយតបតាម Mode និង Rules ដែលបានកំណត់។

---

## 7. Software Requirements Specification (SRS)

SRS ប្រែ User Requirements ទៅជា Software Requirements ជាក់លាក់។ វាឆ្លើយសំណួរ៖ «System ត្រូវធ្វើអ្វី?»

### 7.1 Functional Requirements

- **FR-01 – User Authentication:** System ត្រូវ Authenticate User មុនពេលអនុញ្ញាតឱ្យប្រើ Protected Functions។
- **FR-02 – Arm/Disarm:** System ត្រូវអនុញ្ញាតឱ្យ User ដែលមានសិទ្ធិ ប្តូរ Home, Away និង Disarm Mode។
- **FR-03 – Security Modes:** System ត្រូវគាំទ្រ Home, Away, Disarm និង Scheduled Mode។
- **FR-04 – Sensor Monitoring:** System ត្រូវត្រួតពិនិត្យ Sensors ដែលបានកំណត់ជាបន្តបន្ទាប់។
- **FR-05 – Intrusion Detection:** System ត្រូវរកឃើញ Intrusion តាម Sensor Input និង Active Security Mode។
- **FR-06 – Alarm:** System ត្រូវ Activate Siren នៅពេលមាន Configured Intrusion Event។
- **FR-07 – Notification:** System ត្រូវផ្ញើ Push Notification ឬ SMS នៅពេលមាន Security Event។
- **FR-08 – Camera Streaming:** System ត្រូវផ្តល់ Live Video សម្រាប់ Authorized Users។
- **FR-09 – Automatic Recording:** System ត្រូវចាប់ផ្តើម Recording ដោយស្វ័យប្រវត្តិនៅពេលមាន Motion/Security Event ដែលបានកំណត់។
- **FR-10 – Event History:** System ត្រូវរក្សាទុក Security Events សម្រាប់ពិនិត្យពេលក្រោយ។
- **FR-11 – Device Management:** Admin ត្រូវអាច Add, Remove និង Configure IoT Devices។

### 7.2 Event History Details

- ប្រភេទ Event
- Device
- ថ្ងៃ/ម៉ោង
- Status
- Recording ដែលពាក់ព័ន្ធ

---

## 8. Non-Functional Requirements

### 8.1 Reliability

- Target Availability = 99.9% ក្នុងលក្ខខណ្ឌដែលបានកំណត់
- Critical Components គួរគាំទ្រ Backup Power

### 8.2 Security

- Authentication និង Authorization
- ការពារ Data និង Communication ដោយ Encryption
- អាចកំណត់ AES-256 ជា Project Security Target តាមការរចនា

### 8.3 Performance

- Target Alert Delivery ≤ 2 វិនាទី បន្ទាប់ពី Sensor Trigger ក្រោមលក្ខខណ្ឌ Test ដែលបានកំណត់។

### 8.4 Scalability

- គោលដៅដំបូងគឺគាំទ្រ IoT Devices រហូតដល់ 50 Devices ក្នុង Household Hub។

### 8.5 Usability

- Mobile App គួរមាន Interface ងាយយល់ និងត្រូវការការកំណត់តិចសម្រាប់អ្នកប្រើដែលមិនមែនជាអ្នកបច្ចេកទេស។

### 8.6 Maintainability

- System គួរត្រូវបានបែងជា Modules ដើម្បីងាយ Fix Bug, Update Security និងបន្ថែម Device ប្រភេទថ្មី។

---

## 9. System Design

### 9.1 High-Level Architecture

### 9.2 Components

- Mobile Application
- Backend / API
- Local Control Hub
- Database
- Sensor Layer
- Camera Layer
- Alarm / Notification Layer

### 9.3 Data Entities

- **Users:** UserID, Name, Contact, Role, Authentication Data
- **Devices:** DeviceID, Name, Type, Status
- **SecurityEvents:** EventID, DeviceID, EventType, DateTime, Status
- **Cameras:** CameraID, Name, Status
- **Recordings:** RecordingID, CameraID, EventID, File Reference

---

## 10. Process Model

### 10.1 Primary Model – Incremental Development Model

យើងជ្រើស Incremental Model ជា Process Model សំខាន់ ព្រោះ HomeSafe មាន Features ជាច្រើនដែលអាចបែងចែកអភិវឌ្ឍ និង Test ជាដំណាក់កាល។

- អភិវឌ្ឍជាផ្នែកៗ
- Test មួយ Increment ម្តង
- កាត់បន្ថយ Risk
- អាចផ្តល់ Version ដែលប្រើបានមុន
- ងាយបន្ថែម IoT Devices
- ងាយទទួល Feedback និងកែលម្អ

### 10.2 Increments Overview

| Increment       | Module / Features                                                      | Focus / Target      |
| :-------------- | :--------------------------------------------------------------------- | :------------------ |
| **Increment 1** | Local Control Hub, Database, Authentication, Basic Device Control      | Core Foundation     |
| **Increment 2** | Mobile App, Wireless Connectivity, Remote Arm/Disarm, Device Status    | Remote Access       |
| **Increment 3** | Motion, Door/Window, Glass-Break Sensors, Intrusion Engine, Siren      | Security Monitoring |
| **Increment 4** | Security Camera, Live Streaming, Motion Recording, Video Storage       | Surveillance        |
| **Increment 5** | Push Notification, SMS, Scheduled Arming, Automation Rules, Management | Alerts & Automation |

---

## 11. Supporting Process Models / Practices

- **11.1 Prototype Model:** ប្រើសម្រាប់សាកល្បង Hardware Compatibility, UI Concept, Sensor Communication, Camera Integration និង Alarm មុនពេល Build ប្រព័ន្ធពេញលេញ។
- **11.2 Agile Scrum:** ប្រើ Short Sprints, Planning, Development, Testing, Review និង Feedback ដើម្បីកែលម្អ System ជាបន្តបន្ទាប់ (ឧទាហរណ៍៖ Sprint 1 – Login; Sprint 2 – Arm/Disarm; Sprint 3 – Sensors; Sprint 4 – Camera; Sprint 5 – Notification)។
- **11.3 V-Model Principles:** ប្រើ Verification និង Validation សម្រាប់ Security Features ដែលសំខាន់ ដូចជា Authentication, Intrusion Detection, Alarm និង Notification (Requirement ➔ Design ➔ Implementation ➔ Testing)។

---

## 12. Testing and Verification

### 12.1 ប្រភេទ Testing

- **Unit Testing:** Test Function តូចៗ ដូចជា Login។
- **Integration Testing:** Test Sensor ➔ Hub ➔ Alarm។
- **System Testing:** Test Workflow ទាំងមូល។
- **Acceptance Testing:** User ពិនិត្យថា System បំពេញ Requirements ឬអត់។

### 12.2 Test Cases Matrix

| Test Case     | Condition / Input      | Expected Result        | Requirement |
| :------------ | :--------------------- | :--------------------- | :---------- |
| **Login**     | PIN ត្រឹមត្រូវ         | Login បានជោគជ័យ        | FR-01       |
| **Login**     | PIN ខុស                | Access Denied          | FR-01       |
| **Arm**       | Authorized User        | System Armed           | FR-02       |
| **Disarm**    | Authorized User        | System Disarmed        | FR-02       |
| **Motion**    | Motion ក្នុង Away Mode | Security Event Created | FR-04/05    |
| **Intrusion** | Configured Intrusion   | Alarm Activated        | FR-05/06    |
| **Alert**     | Security Event         | Notification Sent      | FR-07       |
| **Camera**    | Authorized User        | Live Stream            | FR-08       |
| **Recording** | Motion/Security Event  | Video Recorded         | FR-09       |

---

## 13. Security និង Risk Management

- **13.1 Internet Failure:** Remote Access អាចមិនដំណើរការ ➔ Local Control Hub គួរបន្តមុខងារ Security មូលដ្ឋានបានតាមការរចនា។
- **13.2 Power Failure:** Devices អាចឈប់ដំណើរការ ➔ Backup Battery សម្រាប់ Critical Components។
- **13.3 False Alarm:** Sensor អាច Trigger ខុស ➔ កំណត់ Sensitivity និង Detection Rules និងប្រើ Event Verification តាមការរចនា។
- **13.4 Unauthorized Access:** អ្នកគ្មានសិទ្ធិអាចព្យាយាមចូល System ➔ Authentication, Role-based Authorization, Encryption, Logging និង Security Updates។

---

## 14. Deployment

1. ដំឡើង និង Configure Local Control Hub។
2. ដំឡើង និងភ្ជាប់ Sensors/Cameras។
3. បង្កើត Users និង Roles។
4. កំណត់ Security Modes និង Automation Rules។
5. ធ្វើ Integration និង Acceptance Testing។
6. ដាក់ System ឱ្យប្រើប្រាស់។

---

## 15. Maintenance

- Fix Bugs & Security Updates
- IoT Device Updates
- Database Backup/Recovery
- Performance Monitoring & Log Review
- Support New Devices & Feature Improvements

---

## 16. Project Flow សរុប

### 16.1 អត្ថន័យរបស់ជំហាននីមួយៗ

- **Problem:** កំណត់បញ្ហាដែលត្រូវដោះស្រាយ។
- **Objectives:** កំណត់អ្វីដែល Project ចង់សម្រេច។
- **Scope:** កំណត់អ្វីមាន និងមិនមានក្នុង Project។
- **URS:** កំណត់អ្វីដែល User ត្រូវការ។
- **Use Case:** បង្ហាញ User/Actor Interaction ជាមួយ System។
- **SRS:** កំណត់អ្វីដែល Software ត្រូវធ្វើ។
- **Design:** កំណត់របៀបដែល System នឹងត្រូវសាងសង់។
- **Process Model:** កំណត់របៀបរៀបចំ និងដំណើរការ Development។
- **Development:** សរសេរ និងបង្កើត System។
- **Testing:** ពិនិត្យថា System ដំណើរការត្រឹមត្រូវ។
- **Deployment:** ដាក់ System ឱ្យប្រើប្រាស់។
- **Maintenance:** កែ Bug, Update និងបន្ថែមមុខងារ។

---

## 17. សេចក្តីសន្និដ្ឋាន (Conclusion)

HomeSafe Smart Security គឺជាប្រព័ន្ធ Smart Home Security ដែលប្រើ IoT ដើម្បីផ្តល់ Secure Access, Continuous Sensor Monitoring, Real-Time Alerts, Remote Control និង Video Surveillance។ ប្រព័ន្ធគាំទ្រ Home/Away/Disarm Modes, User Roles, Automated Responses និង Security Event Management។

Incremental Development Model ត្រូវបានជ្រើសជាម៉ូដែលសំខាន់ ព្រោះ Features របស់ HomeSafe អាចអភិវឌ្ឍ និង Test ជាផ្នែកៗ។ Prototype អាចជួយសាកល្បង Hardware/UI មុន, Agile Scrum ជួយឱ្យ Development មានភាពបត់បែន និងទទួល Feedback, ខណៈ V-Model Principles ជួយ Verification និង Validation នៃ Security Features សំខាន់ៗ។

គោលដៅចុងក្រោយគឺបង្កើតប្រព័ន្ធដែលមានសុវត្ថិភាព ជឿជាក់ អាចពង្រីកបាន ងាយថែទាំ និងងាយប្រើប្រាស់សម្រាប់លំនៅដ្ឋាន។

---

## 18. សង្ខេប Process Models

| Model                  | តួនាទី                                                     | ស្ថានភាព   |
| :--------------------- | :--------------------------------------------------------- | :--------- |
| **Incremental Model**  | អភិវឌ្ឍ HomeSafe ជា Increments និង Test ជាដំណាក់កាល        | Primary    |
| **Prototype Model**    | សាកល្បង Hardware, UI និង IoT Compatibility                 | Supporting |
| **Agile Scrum**        | Short Sprints, Feedback និង Continuous Improvement         | Supporting |
| **V-Model Principles** | Verification/Validation សម្រាប់ Critical Security Features | Supporting |

"""

with open("HomeSafe_Smart_Security_Case_Study.md", "w", encoding="utf-8") as f:
f.write(content) ### 6.4 Relationship សំខាន់ៗ
Homeowner មាន Interaction ជាមួយ Login, Arm/Disarm, Camera, Alerts និង Recordings។ Admin គ្រប់គ្រង Users និង Devices។ Sensors ជា Source នៃ Security Events ហើយ System ឆ្លើយតបតាម Mode និង Rules ដែលបានកំណត់។

---

## 7. Software Requirements Specification (SRS)

SRS ប្រែ User Requirements ទៅជា Software Requirements ជាក់លាក់។ វាឆ្លើយសំណួរ៖ «System ត្រូវធ្វើអ្វី?»

### 7.1 Functional Requirements

- **FR-01 – User Authentication:** System ត្រូវ Authenticate User មុនពេលអនុញ្ញាតឱ្យប្រើ Protected Functions។
- **FR-02 – Arm/Disarm:** System ត្រូវអនុញ្ញាតឱ្យ User ដែលមានសិទ្ធិ ប្តូរ Home, Away និង Disarm Mode។
- **FR-03 – Security Modes:** System ត្រូវគាំទ្រ Home, Away, Disarm និង Scheduled Mode។
- **FR-04 – Sensor Monitoring:** System ត្រូវត្រួតពិនិត្យ Sensors ដែលបានកំណត់ជាបន្តបន្ទាប់។
- **FR-05 – Intrusion Detection:** System ត្រូវរកឃើញ Intrusion តាម Sensor Input និង Active Security Mode។
- **FR-06 – Alarm:** System ត្រូវ Activate Siren នៅពេលមាន Configured Intrusion Event។
- **FR-07 – Notification:** System ត្រូវផ្ញើ Push Notification ឬ SMS នៅពេលមាន Security Event។
- **FR-08 – Camera Streaming:** System ត្រូវផ្តល់ Live Video សម្រាប់ Authorized Users។
- **FR-09 – Automatic Recording:** System ត្រូវចាប់ផ្តើម Recording ដោយស្វ័យប្រវត្តិនៅពេលមាន Motion/Security Event ដែលបានកំណត់។
- **FR-10 – Event History:** System ត្រូវរក្សាទុក Security Events សម្រាប់ពិនិត្យពេលក្រោយ។
- **FR-11 – Device Management:** Admin ត្រូវអាច Add, Remove និង Configure IoT Devices។

### 7.2 Event History Details

- ប្រភេទ Event
- Device
- ថ្ងៃ/ម៉ោង
- Status
- Recording ដែលពាក់ព័ន្ធ

---

## 8. Non-Functional Requirements

### 8.1 Reliability

- Target Availability = 99.9% ក្នុងលក្ខខណ្ឌដែលបានកំណត់
- Critical Components គួរគាំទ្រ Backup Power

### 8.2 Security

- Authentication និង Authorization
- ការពារ Data និង Communication ដោយ Encryption
- អាចកំណត់ AES-256 ជា Project Security Target តាមការរចនា

### 8.3 Performance

- Target Alert Delivery ≤ 2 វិនាទី បន្ទាប់ពី Sensor Trigger ក្រោមលក្ខខណ្ឌ Test ដែលបានកំណត់។

### 8.4 Scalability

- គោលដៅដំបូងគឺគាំទ្រ IoT Devices រហូតដល់ 50 Devices ក្នុង Household Hub។

### 8.5 Usability

- Mobile App គួរមាន Interface ងាយយល់ និងត្រូវការការកំណត់តិចសម្រាប់អ្នកប្រើដែលមិនមែនជាអ្នកបច្ចេកទេស។

### 8.6 Maintainability

- System គួរត្រូវបានបែងជា Modules ដើម្បីងាយ Fix Bug, Update Security និងបន្ថែម Device ប្រភេទថ្មី។

---

## 9. System Design

### 9.1 High-Level Architecture

### 9.2 Components

- Mobile Application
- Backend / API
- Local Control Hub
- Database
- Sensor Layer
- Camera Layer
- Alarm / Notification Layer

### 9.3 Data Entities

- **Users:** UserID, Name, Contact, Role, Authentication Data
- **Devices:** DeviceID, Name, Type, Status
- **SecurityEvents:** EventID, DeviceID, EventType, DateTime, Status
- **Cameras:** CameraID, Name, Status
- **Recordings:** RecordingID, CameraID, EventID, File Reference

---

## 10. Process Model

### 10.1 Primary Model – Incremental Development Model

យើងជ្រើស Incremental Model ជា Process Model សំខាន់ ព្រោះ HomeSafe មាន Features ជាច្រើនដែលអាចបែងចែកអភិវឌ្ឍ និង Test ជាដំណាក់កាល។

- អភិវឌ្ឍជាផ្នែកៗ
- Test មួយ Increment ម្តង
- កាត់បន្ថយ Risk
- អាចផ្តល់ Version ដែលប្រើបានមុន
- ងាយបន្ថែម IoT Devices
- ងាយទទួល Feedback និងកែលម្អ

### 10.2 Increments Overview

| Increment       | Module / Features                                                      | Focus / Target      |
| :-------------- | :--------------------------------------------------------------------- | :------------------ |
| **Increment 1** | Local Control Hub, Database, Authentication, Basic Device Control      | Core Foundation     |
| **Increment 2** | Mobile App, Wireless Connectivity, Remote Arm/Disarm, Device Status    | Remote Access       |
| **Increment 3** | Motion, Door/Window, Glass-Break Sensors, Intrusion Engine, Siren      | Security Monitoring |
| **Increment 4** | Security Camera, Live Streaming, Motion Recording, Video Storage       | Surveillance        |
| **Increment 5** | Push Notification, SMS, Scheduled Arming, Automation Rules, Management | Alerts & Automation |

---

## 11. Supporting Process Models / Practices

- **11.1 Prototype Model:** ប្រើសម្រាប់សាកល្បង Hardware Compatibility, UI Concept, Sensor Communication, Camera Integration និង Alarm មុនពេល Build ប្រព័ន្ធពេញលេញ។
- **11.2 Agile Scrum:** ប្រើ Short Sprints, Planning, Development, Testing, Review និង Feedback ដើម្បីកែលម្អ System ជាបន្តបន្ទាប់ (ឧទាហរណ៍៖ Sprint 1 – Login; Sprint 2 – Arm/Disarm; Sprint 3 – Sensors; Sprint 4 – Camera; Sprint 5 – Notification)។
- **11.3 V-Model Principles:** ប្រើ Verification និង Validation សម្រាប់ Security Features ដែលសំខាន់ ដូចជា Authentication, Intrusion Detection, Alarm និង Notification (Requirement ➔ Design ➔ Implementation ➔ Testing)។

---

## 12. Testing and Verification

### 12.1 ប្រភេទ Testing

- **Unit Testing:** Test Function តូចៗ ដូចជា Login។
- **Integration Testing:** Test Sensor ➔ Hub ➔ Alarm។
- **System Testing:** Test Workflow ទាំងមូល។
- **Acceptance Testing:** User ពិនិត្យថា System បំពេញ Requirements ឬអត់។

### 12.2 Test Cases Matrix

| Test Case     | Condition / Input      | Expected Result        | Requirement |
| :------------ | :--------------------- | :--------------------- | :---------- |
| **Login**     | PIN ត្រឹមត្រូវ         | Login បានជោគជ័យ        | FR-01       |
| **Login**     | PIN ខុស                | Access Denied          | FR-01       |
| **Arm**       | Authorized User        | System Armed           | FR-02       |
| **Disarm**    | Authorized User        | System Disarmed        | FR-02       |
| **Motion**    | Motion ក្នុង Away Mode | Security Event Created | FR-04/05    |
| **Intrusion** | Configured Intrusion   | Alarm Activated        | FR-05/06    |
| **Alert**     | Security Event         | Notification Sent      | FR-07       |
| **Camera**    | Authorized User        | Live Stream            | FR-08       |
| **Recording** | Motion/Security Event  | Video Recorded         | FR-09       |

---

## 13. Security និង Risk Management

- **13.1 Internet Failure:** Remote Access អាចមិនដំណើរការ ➔ Local Control Hub គួរបន្តមុខងារ Security មូលដ្ឋានបានតាមការរចនា។
- **13.2 Power Failure:** Devices អាចឈប់ដំណើរការ ➔ Backup Battery សម្រាប់ Critical Components។
- **13.3 False Alarm:** Sensor អាច Trigger ខុស ➔ កំណត់ Sensitivity និង Detection Rules និងប្រើ Event Verification តាមការរចនា។
- **13.4 Unauthorized Access:** អ្នកគ្មានសិទ្ធិអាចព្យាយាមចូល System ➔ Authentication, Role-based Authorization, Encryption, Logging និង Security Updates។

---

## 14. Deployment

1. ដំឡើង និង Configure Local Control Hub។
2. ដំឡើង និងភ្ជាប់ Sensors/Cameras។
3. បង្កើត Users និង Roles។
4. កំណត់ Security Modes និង Automation Rules។
5. ធ្វើ Integration និង Acceptance Testing។
6. ដាក់ System ឱ្យប្រើប្រាស់។

---

## 15. Maintenance

- Fix Bugs & Security Updates
- IoT Device Updates
- Database Backup/Recovery
- Performance Monitoring & Log Review
- Support New Devices & Feature Improvements

---

## 16. Project Flow សរុប

### 16.1 អត្ថន័យរបស់ជំហាននីមួយៗ

- **Problem:** កំណត់បញ្ហាដែលត្រូវដោះស្រាយ។
- **Objectives:** កំណត់អ្វីដែល Project ចង់សម្រេច។
- **Scope:** កំណត់អ្វីមាន និងមិនមានក្នុង Project។
- **URS:** កំណត់អ្វីដែល User ត្រូវការ។
- **Use Case:** បង្ហាញ User/Actor Interaction ជាមួយ System។
- **SRS:** កំណត់អ្វីដែល Software ត្រូវធ្វើ។
- **Design:** កំណត់របៀបដែល System នឹងត្រូវសាងសង់។
- **Process Model:** កំណត់របៀបរៀបចំ និងដំណើរការ Development។
- **Development:** សរសេរ និងបង្កើត System។
- **Testing:** ពិនិត្យថា System ដំណើរការត្រឹមត្រូវ។
- **Deployment:** ដាក់ System ឱ្យប្រើប្រាស់។
- **Maintenance:** កែ Bug, Update និងបន្ថែមមុខងារ។

---

## 17. សេចក្តីសន្និដ្ឋាន (Conclusion)

HomeSafe Smart Security គឺជាប្រព័ន្ធ Smart Home Security ដែលប្រើ IoT ដើម្បីផ្តល់ Secure Access, Continuous Sensor Monitoring, Real-Time Alerts, Remote Control និង Video Surveillance។ ប្រព័ន្ធគាំទ្រ Home/Away/Disarm Modes, User Roles, Automated Responses និង Security Event Management។

Incremental Development Model ត្រូវបានជ្រើសជាម៉ូដែលសំខាន់ ព្រោះ Features របស់ HomeSafe អាចអភិវឌ្ឍ និង Test ជាផ្នែកៗ។ Prototype អាចជួយសាកល្បង Hardware/UI មុន, Agile Scrum ជួយឱ្យ Development មានភាពបត់បែន និងទទួល Feedback, ខណៈ V-Model Principles ជួយ Verification និង Validation នៃ Security Features សំខាន់ៗ។

គោលដៅចុងក្រោយគឺបង្កើតប្រព័ន្ធដែលមានសុវត្ថិភាព ជឿជាក់ អាចពង្រីកបាន ងាយថែទាំ និងងាយប្រើប្រាស់សម្រាប់លំនៅដ្ឋាន។

---

## 18. សង្ខេប Process Models

| Model                  | តួនាទី                                                     | ស្ថានភាព   |
| :--------------------- | :--------------------------------------------------------- | :--------- |
| **Incremental Model**  | អភិវឌ្ឍ HomeSafe ជា Increments និង Test ជាដំណាក់កាល        | Primary    |
| **Prototype Model**    | សាកល្បង Hardware, UI និង IoT Compatibility                 | Supporting |
| **Agile Scrum**        | Short Sprints, Feedback និង Continuous Improvement         | Supporting |
| **V-Model Principles** | Verification/Validation សម្រាប់ Critical Security Features | Supporting |

"""

with open("HomeSafe_Smart_Security_Case_Study.md", "w", encoding="utf-8") as f:
f.write(content)

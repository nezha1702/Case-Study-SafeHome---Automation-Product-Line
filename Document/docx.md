# HOME SAFE SMART SECURITY

## ប្រព័ន្ធសុវត្ថិភាព និង Automation សម្រាប់ Smart Home

**Software Engineering Case Study**

---

# 1. សេចក្តីផ្តើម (Introduction)

## 1.1 ឈ្មោះគម្រោង

**HomeSafe Smart Security**

## 1.2 ប្រភេទគម្រោង

**Software Engineering Case Study**

## 1.3 អត្ថន័យរបស់ប្រព័ន្ធ

HomeSafe គឺជាប្រព័ន្ធ **Smart Home Security** ដែលប្រើប្រាស់ **IoT Devices** ដើម្បីត្រួតពិនិត្យ និងការពារផ្ទះ។

ប្រព័ន្ធនេះភ្ជាប់៖

- Sensors
- Cameras
- Alarm
- Local Control Hub
- Mobile Application

ដើម្បីឱ្យម្ចាស់ផ្ទះអាចត្រួតពិនិត្យ និងគ្រប់គ្រងផ្ទះបានទាំងនៅក្នុងផ្ទះ និងពីចម្ងាយ។

## 1.4 មុខងារសំខាន់ៗ

- Smart Security
- Camera Surveillance
- Intrusion Detection
- Alarm / Siren
- Remote Monitoring
- Smart Automation
- Mobile Access

---

# 2. Background និង Problem Statement

## 2.1 Background

HomeSafe ប្រើប្រាស់បច្ចេកវិទ្យា **IoT** ដើម្បីឱ្យឧបករណ៍សុវត្ថិភាពនៅក្នុងផ្ទះអាចទំនាក់ទំនងគ្នា និងត្រូវបានគ្រប់គ្រងតាមរយៈប្រព័ន្ធកណ្ដាល។

ឧបករណ៍សំខាន់ៗមាន៖

- **Motion Sensor** – រកចលនា
- **Door / Window Sensor** – ពិនិត្យទ្វារ និងបង្អួច
- **Glass Break Sensor** – រកការបែកកញ្ចក់
- **Security Camera** – មើល និងថតវីដេអូ
- **Siren / Alarm** – បន្លឺសំឡេងពេលមានហេតុការណ៍
- **Mobile App** – គ្រប់គ្រងពីទូរស័ព្ទ
- **Local Control Hub** – គ្រប់គ្រងឧបករណ៍ក្នុងផ្ទះ

## 2.2 បញ្ហាដែលគម្រោងចង់ដោះស្រាយ

1. ម្ចាស់ផ្ទះមិនអាចតាមដានផ្ទះបានគ្រប់ពេល។
2. ពិបាកដឹងភ្លាមៗនៅពេលមានការចូលដោយគ្មានការអនុញ្ញាត។
3. ប្រព័ន្ធសុវត្ថិភាពធម្មតាអាចមាន Remote Access កំណត់។
4. អ្នកប្រើត្រូវការទទួល Alert ភ្លាមៗ។
5. ត្រូវការគ្រប់គ្រង Sensors, Cameras និង Alarm ពីកន្លែងតែមួយ។
6. ប្រព័ន្ធគួរអាចពង្រីកទៅ IoT Devices បន្ថែមបាន។

---

# 3. Objectives និង Scope

## 3.1 គោលបំណងសំខាន់

បង្កើតប្រព័ន្ធ **Smart Home Security** ដែលមានសុវត្ថិភាព ជឿជាក់ ងាយប្រើ និងអាចឱ្យម្ចាស់ផ្ទះត្រួតពិនិត្យ គ្រប់គ្រង និងការពារផ្ទះបានពីចម្ងាយ។

## 3.2 គោលបំណងរង

- ការពារទ្រព្យសម្បត្តិ និងលំនៅដ្ឋាន
- ផ្តល់ User Authentication ដែលមានសុវត្ថិភាព
- ត្រួតពិនិត្យ Sensors ជាបន្តបន្ទាប់
- រកឃើញ Intrusion Events
- ផ្ញើ Security Alerts
- មើល Live Camera និងថតវីដេអូ
- គ្រប់គ្រងប្រព័ន្ធពី Mobile App
- គាំទ្រ User Roles និង Permissions
- ធានា Reliability និង Security

## 3.3 Scope – អ្វីដែលគម្រោងមាន

- Login / Authentication
- PIN និង Fingerprint
- Family / Guest Roles
- Home / Away / Disarm
- Scheduled Arming / Disarming
- Motion / Door / Window / Glass Break Detection
- Live Camera
- Video Recording
- Siren
- Push Notification
- SMS Alert
- Device Configuration
- Security Event Logs

## 3.4 Out of Scope – អ្វីដែលមិនទាន់រួមបញ្ចូល

- ភ្ជាប់ដោយផ្ទាល់ទៅប៉ូលិស ឬ Emergency Service
- Professional Security Monitoring Center
- Advanced AI Facial Recognition
- Full Smart Energy Management
- Full Smart Water Management

---

# 4. Stakeholders និង User Roles

## 4.1 Homeowner

ម្ចាស់ផ្ទះមានសិទ្ធិគ្រប់គ្រងមុខងារសំខាន់ៗ ដូចជា៖

- Arm / Disarm
- មើល Camera
- មើល Alerts
- មើល Recordings
- គ្រប់គ្រង Family Members

## 4.2 Family Member

សមាជិកគ្រួសារអាចប្រើមុខងារដែលម្ចាស់ផ្ទះបានអនុញ្ញាត។

## 4.3 Guest

ភ្ញៀវអាចទទួលបាន៖

- Temporary Access
- Limited Access

តាម Permission ដែលបានកំណត់។

## 4.4 Administrator

Admin គ្រប់គ្រង៖

- Users
- Devices
- Sensors
- Cameras
- Alarm
- Notification Settings

## 4.5 IoT Devices

Sensors និង Cameras ផ្ញើ៖

- Events
- Status

ទៅកាន់ HomeSafe System។

---

# 5. User Requirements Specification (URS)

URS មានន័យថា **តម្រូវការរបស់អ្នកប្រើប្រាស់**។

វាឆ្លើយសំណួរ៖

> **User ចង់ឱ្យ System មានអ្វីខ្លះ?**

## 5.1 Secure Access

- Login ដោយ PIN
- Fingerprint Authentication
- Mobile Credentials
- Family Access
- Guest Access
- Role-Based Permissions

## 5.2 Security Modes

### Home Mode

ប្រើនៅពេលអ្នករស់នៅក្នុងផ្ទះ។

User អាចកំណត់ Sensors ខ្លះឱ្យ Active និងខ្លះឱ្យ Inactive។

### Away Mode

ប្រើនៅពេលអ្នកចេញពីផ្ទះ។

Sensors ដែលបានកំណត់សម្រាប់ Security ត្រូវបាន Activate។

### Disarm Mode

បិទ Security Monitoring សម្រាប់ User ដែលមានសិទ្ធិ។

### Scheduled Mode

អាចកំណត់ម៉ោងឱ្យ System Arm ឬ Disarm ដោយស្វ័យប្រវត្តិ។

## 5.3 Sensor Monitoring

- Motion Detection
- Door Monitoring
- Window Monitoring
- Glass Break Detection

## 5.4 Real-Time Alerts

- Push Notification
- SMS Alert
- Local Siren / Alarm

## 5.5 Remote Access

- ពិនិត្យ System Status
- Arm / Disarm ពីចម្ងាយ
- មើល Camera
- មើល Alerts
- មើល Event History

## 5.6 Video Surveillance

- Live Camera Streaming
- Manual Recording
- Motion-Triggered Recording
- មើល Recordings ចាស់

## 5.7 Device Management

- Add Device
- Remove Device
- Configure Device
- Check Device Status

---

# 6. Use Case Analysis

Use Case គឺជាវិធីបង្ហាញថា **Actor មាន Interaction អ្វីជាមួយ System**។

## 6.1 Actors

- Homeowner
- Family Member
- Guest
- Administrator
- IoT Sensors
- Security Camera

## 6.2 Main Use Cases

- Login
- Arm System
- Disarm System
- Select Security Mode
- View Camera
- Record Video
- Detect Intruder
- Trigger Alarm
- Send Notification
- View Event History
- Configure System
- Manage Users
- Manage Devices

## 6.3 Core Intrusion Workflow

```text
Sensor រកឃើញហេតុការណ៍
        ↓
HomeSafe ទទួល Event
        ↓
ពិនិត្យ Security Mode
        ↓
សម្រេចថាជា Intrusion ឬអត់
        ↓
Activate Alarm
        ↓
ចាប់ផ្តើម Recording
        ↓
ផ្ញើ Notification ទៅ Homeowner
        ↓
ពិនិត្យ Event
```

## 6.4 Relationship សំខាន់ៗ

- Homeowner មាន Interaction ជាមួយ Login, Arm/Disarm, Camera, Alerts និង Recordings។
- Admin គ្រប់គ្រង Users និង Devices។
- Sensors ជា Source នៃ Security Events។
- System ឆ្លើយតបតាម Mode និង Rules ដែលបានកំណត់។

---

# 7. Software Requirements Specification (SRS)

SRS បម្លែង **User Requirements** ទៅជា **Software Requirements ជាក់លាក់**។

វាឆ្លើយសំណួរ៖

> **System ត្រូវធ្វើអ្វី?**

## 7.1 Functional Requirements

### FR-01 – User Authentication

System ត្រូវ Authenticate User មុនពេលអនុញ្ញាតឱ្យប្រើ Protected Functions។

### FR-02 – Arm / Disarm

System ត្រូវអនុញ្ញាតឱ្យ User ដែលមានសិទ្ធិប្តូរ Home, Away និង Disarm Mode។

### FR-03 – Security Modes

System ត្រូវគាំទ្រ៖

- Home Mode
- Away Mode
- Disarm Mode
- Scheduled Mode

### FR-04 – Sensor Monitoring

System ត្រូវត្រួតពិនិត្យ Sensors ដែលបានកំណត់ជាបន្តបន្ទាប់។

### FR-05 – Intrusion Detection

System ត្រូវរកឃើញ Intrusion តាម Sensor Input និង Active Security Mode។

### FR-06 – Alarm

System ត្រូវ Activate Siren នៅពេលមាន Configured Intrusion Event។

### FR-07 – Notification

System ត្រូវផ្ញើ៖

- Push Notification
- SMS

នៅពេលមាន Security Event។

### FR-08 – Camera Streaming

System ត្រូវផ្តល់ Live Video សម្រាប់ Authorized Users។

### FR-09 – Automatic Recording

System ត្រូវចាប់ផ្តើម Recording ដោយស្វ័យប្រវត្តិនៅពេលមាន៖

- Motion
- Security Event

ដែលបានកំណត់។

### FR-10 – Event History

System ត្រូវរក្សាទុក Security Events សម្រាប់ពិនិត្យពេលក្រោយ។

### FR-11 – Device Management

Admin ត្រូវអាច៖

- Add
- Remove
- Configure

IoT Devices។

## 7.2 Event History

ត្រូវរក្សាទុក៖

- ប្រភេទ Event
- Device
- ថ្ងៃ / ម៉ោង
- Status
- Recording ដែលពាក់ព័ន្ធ

---

# 8. Non-Functional Requirements

Non-Functional Requirements ប្រាប់ថា៖

> **System ត្រូវដំណើរការមានគុណភាពបែបណា?**

## 8.1 Reliability

- Target Availability = **99.9%** ក្នុងលក្ខខណ្ឌដែលបានកំណត់
- Critical Components គួរគាំទ្រ Backup Power

## 8.2 Security

- Authentication និង Authorization
- ការពារ Data និង Communication ដោយ Encryption
- អាចកំណត់ AES-256 ជា Project Security Target តាមការរចនា

## 8.3 Performance

Target Alert Delivery ប្រហែល **2 វិនាទី** បន្ទាប់ពី Sensor Trigger ក្នុងលក្ខខណ្ឌ Test ដែលបានកំណត់។

## 8.4 Scalability

គោលដៅដំបូងគឺគាំទ្រ IoT Devices រហូតដល់ **50 Devices ក្នុង Household Hub**។

## 8.5 Usability

Mobile App គួរមាន Interface ងាយយល់ និងត្រូវការការកំណត់តិចសម្រាប់អ្នកប្រើដែលមិនមែនជាអ្នកបច្ចេកទេស។

## 8.6 Maintainability

System គួរត្រូវបានបែងជា Modules ដើម្បីងាយ៖

- Fix Bug
- Update Security
- បន្ថែម Device ប្រភេទថ្មី

---

# 9. System Design

## 9.1 High-Level Architecture

```text
User
  ↓
Mobile App / Web App
  ↓
Backend / API
  ↓
Database
  ↓
Local Control Hub
  ↓
Sensors / Cameras / Alarm
```

## 9.2 Components

- Mobile Application
- Backend / API
- Local Control Hub
- Database
- Sensor Layer
- Camera Layer
- Alarm / Notification Layer

## 9.3 Data Entities

### Users

```text
UserID
Name
Contact
Role
Authentication Data
```

### Devices

```text
DeviceID
Name
Type
Status
```

### SecurityEvents

```text
EventID
DeviceID
EventType
DateTime
Status
```

### Cameras

```text
CameraID
Name
Status
```

### Recordings

```text
RecordingID
CameraID
EventID
File Reference
```

---

# 10. Process Model

## 10.1 Primary Model – Incremental Development Model

HomeSafe ប្រើ **Incremental Development Model** ជា Process Model សំខាន់។

មូលហេតុគឺ HomeSafe មាន Features ជាច្រើនដែលអាចបែងចែកអភិវឌ្ឍ និង Test ជាដំណាក់កាល។

អត្ថប្រយោជន៍៖

- អភិវឌ្ឍជាផ្នែកៗ
- Test មួយ Increment ម្តង
- កាត់បន្ថយ Risk
- អាចផ្តល់ Version ដែលប្រើបានមុន
- ងាយបន្ថែម IoT Devices
- ងាយទទួល Feedback និងកែលម្អ

## 10.2 Increment 1 – Core Foundation

- Local Control Hub
- Database
- Authentication
- Basic Device Control
- Basic System Status

## 10.3 Increment 2 – Remote Access

- Mobile Application
- Wireless / Network Connectivity
- Remote Access
- Remote Arm / Disarm
- Device Status

## 10.4 Increment 3 – Security Monitoring

- Motion Sensor
- Door / Window Sensors
- Glass Break Sensor
- Intrusion Detection
- Alarm / Siren

## 10.5 Increment 4 – Surveillance

- Security Camera
- Live Streaming
- Motion-Triggered Recording
- Video Storage
- Recording History

## 10.6 Increment 5 – Alerts and Automation

- Push Notification
- SMS Alert
- Scheduled Arming / Disarming
- Automation Rules
- Event History
- Device Management

---

# 11. Supporting Process Models / Practices

## 11.1 Prototype Model

ប្រើសម្រាប់សាកល្បង៖

- Hardware Compatibility
- UI Concept
- Sensor Communication
- Camera Integration
- Alarm

មុនពេល Build ប្រព័ន្ធពេញលេញ។

## 11.2 Agile Scrum

ប្រើ៖

- Short Sprints
- Planning
- Development
- Testing
- Review
- Feedback

ឧទាហរណ៍៖

```text
Sprint 1 → Login
Sprint 2 → Arm / Disarm
Sprint 3 → Sensors
Sprint 4 → Camera
Sprint 5 → Notification
```

## 11.3 V-Model Principles

ប្រើសម្រាប់៖

- Verification
- Validation

នៃ Security Features សំខាន់ៗ ដូចជា៖

- Authentication
- Intrusion Detection
- Alarm
- Notification

```text
Requirement
    ↓
Design
    ↓
Implementation
    ↓
Testing
```

---

# 12. Testing and Verification

## 12.1 ប្រភេទ Testing

- **Unit Testing** – Test Function តូចៗ ដូចជា Login
- **Integration Testing** – Test Sensor → Hub → Alarm
- **System Testing** – Test Workflow ទាំងមូល
- **Acceptance Testing** – User ពិនិត្យថា System បំពេញ Requirements ឬអត់

## 12.2 ឧទាហរណ៍ Test Cases

| Test      | Condition / Input       | Expected Result        | Requirement   |
| --------- | ----------------------- | ---------------------- | ------------- |
| Login     | PIN ត្រឹមត្រូវ          | Login បានជោគជ័យ        | FR-01         |
| Login     | PIN ខុស                 | Access Denied          | FR-01         |
| Arm       | Authorized User         | System Armed           | FR-02         |
| Disarm    | Authorized User         | System Disarmed        | FR-02         |
| Motion    | Motion ក្នុង Away Mode  | Security Event Created | FR-04 / FR-05 |
| Intrusion | Configured Intrusion    | Alarm Activated        | FR-05 / FR-06 |
| Alert     | Security Event          | Notification Sent      | FR-07         |
| Camera    | Authorized User         | Live Stream            | FR-08         |
| Recording | Motion / Security Event | Video Recorded         | FR-09         |

---

# 13. Security និង Risk Management

## 13.1 Internet Failure

**បញ្ហា៖**

Remote Access អាចមិនដំណើរការ។

**ដំណោះស្រាយ៖**

Local Control Hub គួរបន្តមុខងារ Security មូលដ្ឋានបានតាមការរចនា។

## 13.2 Power Failure

**បញ្ហា៖**

Devices អាចឈប់ដំណើរការ។

**ដំណោះស្រាយ៖**

ប្រើ Backup Battery សម្រាប់ Critical Components។

## 13.3 False Alarm

**បញ្ហា៖**

Sensor អាច Trigger ខុស។

**ដំណោះស្រាយ៖**

- កំណត់ Sensitivity
- Detection Rules
- Event Verification

តាមការរចនា។

## 13.4 Unauthorized Access

**បញ្ហា៖**

អ្នកគ្មានសិទ្ធិអាចព្យាយាមចូល System។

**ដំណោះស្រាយ៖**

- Authentication
- Role-Based Authorization
- Encryption
- Logging
- Security Updates

---

# 14. Deployment

1. ដំឡើង និង Configure Local Control Hub។
2. ដំឡើង និងភ្ជាប់ Sensors / Cameras។
3. បង្កើត Users និង Roles។
4. កំណត់ Security Modes និង Automation Rules។
5. ធ្វើ Integration និង Acceptance Testing។
6. ដាក់ System ឱ្យប្រើប្រាស់។

---

# 15. Maintenance

- Fix Bugs
- Security Updates
- IoT Device Updates
- Database Backup / Recovery
- Performance Monitoring
- Log Review
- Support New Devices
- Feature Improvements

---

# 16. Project Flow សរុប

```text
Problem
   ↓
Objectives
   ↓
Scope
   ↓
Stakeholders / User Roles
   ↓
URS
   ↓
Use Case
   ↓
SRS
   ↓
System Design
   ↓
Process Model
   ↓
Incremental Development
   ↓
Testing
   ↓
Deployment
   ↓
Maintenance
```

## 16.1 អត្ថន័យរបស់ជំហាននីមួយៗ

- **Problem** – កំណត់បញ្ហាដែលត្រូវដោះស្រាយ។
- **Objectives** – កំណត់អ្វីដែល Project ចង់សម្រេច។
- **Scope** – កំណត់អ្វីមាន និងមិនមានក្នុង Project។
- **URS** – កំណត់អ្វីដែល User ត្រូវការ។
- **Use Case** – បង្ហាញ User / Actor Interaction ជាមួយ System។
- **SRS** – កំណត់អ្វីដែល Software ត្រូវធ្វើ។
- **Design** – កំណត់របៀបដែល System នឹងត្រូវសាងសង់។
- **Process Model** – កំណត់របៀបរៀបចំ និងដំណើរការ Development។
- **Development** – សរសេរ និងបង្កើត System។
- **Testing** – ពិនិត្យថា System ដំណើរការត្រឹមត្រូវ។
- **Deployment** – ដាក់ System ឱ្យប្រើប្រាស់។
- **Maintenance** – កែ Bug, Update និងបន្ថែមមុខងារ។

---

# 17. សេចក្តីសន្និដ្ឋាន (Conclusion)

HomeSafe Smart Security គឺជាប្រព័ន្ធ Smart Home Security ដែលប្រើប្រាស់ IoT ដើម្បីផ្តល់៖

- Secure Access
- Continuous Sensor Monitoring
- Real-Time Alerts
- Remote Control
- Video Surveillance
- Home / Away / Disarm Modes
- User Roles
- Automated Responses
- Security Event Management

**Incremental Development Model** ត្រូវបានជ្រើសរើសជាម៉ូដែលសំខាន់ ព្រោះ Features របស់ HomeSafe អាចអភិវឌ្ឍ និង Test ជាផ្នែកៗ។

បន្ថែមពីនេះ៖

- **Prototype Model** ជួយសាកល្បង Hardware និង UI មុន
- **Agile Scrum** ជួយឱ្យ Development មានភាពបត់បែន និងទទួល Feedback
- **V-Model Principles** ជួយ Verification និង Validation នៃ Security Features សំខាន់ៗ

គោលដៅចុងក្រោយគឺបង្កើតប្រព័ន្ធដែលមាន៖

> **សុវត្ថិភាព, ជឿជាក់, អាចពង្រីកបាន, ងាយថែទាំ និងងាយប្រើសម្រាប់លំនៅដ្ឋាន។**

---

# 18. សង្ខេប Process Models

| Model              | តួនាទី                                                       | ស្ថានភាព    |
| ------------------ | ------------------------------------------------------------ | ----------- |
| Incremental Model  | អភិវឌ្ឍ HomeSafe ជា Increments និង Test ជាដំណាក់កាល          | **Primary** |
| Prototype Model    | សាកល្បង Hardware, UI និង IoT Compatibility                   | Supporting  |
| Agile Scrum        | Short Sprints, Feedback និង Continuous Improvement           | Supporting  |
| V-Model Principles | Verification / Validation សម្រាប់ Critical Security Features | Supporting  |

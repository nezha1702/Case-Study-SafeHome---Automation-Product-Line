# User Requirements Document (URD)
## HomeSafe Smart Security

**Project Type:** Software Engineering Case Study
**Document:** User Requirements Document (URD / URS)
**ភាសា:** Khmer / English (Bilingual)

---

## 1. Introduction (សេចក្តីផ្តើម)

### 1.1 Project Name (ឈ្មោះគម្រោង)
HomeSafe Smart Security

### 1.2 Project Type (ប្រភេទគម្រោង)
Software Engineering Case Study

### 1.3 System Overview (អត្ថន័យរបស់ប្រព័ន្ធ)
HomeSafe គឺជាប្រព័ន្ធ Smart Home Security ដែលប្រើ IoT Devices ដើម្បីត្រួតពិនិត្យនិងការពារផ្ទះ។ វាភ្ជាប់ Sensors, Cameras, Alarm, Local Control Hub និង Mobile Application ដើម្បីឱ្យម្ចាស់ផ្ទះអាចត្រួតពិនិត្យ និងគ្រប់គ្រងផ្ទះបានទាំងនៅក្នុង និងពីចម្ងាយ។

> HomeSafe is a Smart Home Security system that uses IoT devices to monitor and protect a home. It connects sensors, cameras, an alarm, a local control hub, and a mobile app so the homeowner can monitor and control the home both locally and remotely.

### 1.4 Key Features (មុខងារសំខាន់ៗ)
- សុវត្ថិភាពផ្ទះ (Smart Security)
- តាមដាន Camera (Surveillance)
- រកឃើញការចូលដោយគ្មានការអនុញ្ញាត (Intrusion Detection)
- Alarm / Siren
- Remote Monitoring
- Smart Automation
- Mobile Access

---

## 2. Background and Problem Statement

### 2.1 Background (ផ្ទៃខាងក្រោយ)
HomeSafe ប្រើបច្ចេកវិទ្យា IoT ដើម្បីឱ្យឧបករណ៍សុវត្ថិភាពនៅក្នុងផ្ទះអាចទំនាក់ទំនងគ្នា និងត្រូវបានគ្រប់គ្រងតាមរយៈប្រព័ន្ធកណ្ដាល។

Core devices in the ecosystem:

| Device | Role (មុខងារ) |
|---|---|
| Motion Sensor | រកចលនា / Detects motion |
| Door/Window Sensor | ពិនិត្យទ្វារ/បង្អួច / Monitors doors & windows |
| Glass-Break Sensor | រកការបែកកញ្ចក់ / Detects glass breaking |
| Security Camera | មើល និងថតវីដេអូ / Live view & recording |
| Siren/Alarm | បន្លឺសំឡេងពេលមានហេតុការណ៍ / Sounds on event |
| Mobile App | គ្រប់គ្រងពីទូរស័ព្ទ / Remote control |
| Local Control Hub | គ្រប់គ្រងឧបករណ៍ក្នុងផ្ទះ / Local device management |

### 2.2 Problem Statement (បញ្ហាដែលគម្រោងចង់ដោះស្រាយ)
1. ម្ចាស់ផ្ទះមិនអាចតាមដានផ្ទះបានគ្រប់ពេល — Homeowners cannot monitor their homes at all times.
2. ពិបាកដឹងភ្លាមៗនៅពេលមានការចូលដោយគ្មានការអនុញ្ញាត — Hard to know immediately about unauthorized entry.
3. ប្រព័ន្ធសុវត្ថិភាពធម្មតាអាចមាន Remote Access កំណត់ — Conventional systems often have limited remote access.
4. អ្នកប្រើត្រូវការទទួល Alert ភ្លាមៗ — Users need immediate alerts.
5. ត្រូវការគ្រប់គ្រង Sensors, Cameras និង Alarm ពីកន្លែងតែមួយ — Need to manage sensors, cameras, and alarm from one place.
6. ប្រព័ន្ធគួរអាចពង្រីកទៅ IoT Devices បន្ថែមបាន — The system should be extensible to more IoT devices.

---

## 3. Objectives and Scope

### 3.1 Main Objective (គោលបំណងសំខាន់)
បង្កើតប្រព័ន្ធ Smart Home Security ដែលមានសុវត្ថិភាព ជឿជាក់ ងាយប្រើ និងអាចឱ្យម្ចាស់ផ្ទះត្រួតពិនិត្យ គ្រប់គ្រង និងការពារផ្ទះបានពីចម្ងាយ។

> Build a secure, reliable, easy-to-use Smart Home Security system that lets the homeowner monitor, control, and protect the home remotely.

### 3.2 Sub-Objectives (គោលបំណងរង)
- ការពារទ្រព្យសម្បត្តិ និងលំនៅដ្ឋាន
- ផ្តល់ User Authentication ដែលមានសុវត្ថិភាព
- ត្រួតពិនិត្យ Sensors ជាបន្តបន្ទាប់
- រកឃើញ Intrusion Events
- ផ្ញើ Security Alerts
- មើល Live Camera និងថតវីដេអូ
- គ្រប់គ្រងប្រព័ន្ធពី Mobile App
- គាំទ្រ User Roles និង Permissions
- ធានា Reliability និង Security

### 3.3 In Scope (Scope — អ្វីដែលគម្រោងមាន)
- Login / Authentication
- PIN និង Fingerprint
- Family/Guest Roles
- Home/Away/Disarm Modes
- Scheduled Arming/Disarming
- Motion / Door / Window / Glass-Break Detection
- Live Camera
- Video Recording
- Siren
- Push Notification
- SMS Alert
- Device Configuration
- Security Event Logs

### 3.4 Out of Scope (អ្វីដែលមិនទាន់រួមបញ្ចូល)
- ភ្ជាប់ដោយផ្ទាល់ទៅប៉ូលិស ឬ Emergency Service (Direct police/emergency service integration)
- Professional Security Monitoring Center
- Advanced AI Facial Recognition
- Full Smart Energy Management
- Full Smart Water Management

---

## 4. Stakeholders and User Roles

### 4.1 Homeowner
ម្ចាស់ផ្ទះមានសិទ្ធិគ្រប់គ្រងសំខាន់ៗ ដូចជា Arm/Disarm, មើល Camera, មើល Alerts/Recordings និងគ្រប់គ្រង Family Members។
*(Full control: Arm/Disarm, view cameras, view alerts/recordings, manage family members.)*

### 4.2 Family Member
សមាជិកគ្រួសារអាចប្រើមុខងារដែលម្ចាស់ផ្ទះបានអនុញ្ញាត។
*(Can use features permitted by the homeowner.)*

### 4.3 Guest
ភ្ញៀវអាចទទួលបាន Temporary Access ឬ Limited Access តាម Permission។
*(Temporary or limited access, per permission.)*

### 4.4 Administrator
Admin គ្រប់គ្រង Users, Devices, Sensors, Cameras, Alarm និង Notification Settings។
*(Manages users, devices, sensors, cameras, alarm, and notification settings.)*

### 4.5 IoT Devices
Sensors និង Cameras ផ្ញើ Events/Status ទៅ HomeSafe System។
*(Sensors and cameras send events/status to the HomeSafe system — non-human actor.)*

---

## 5. User Requirements Specification (URS)

> URS មានន័យថា តម្រូវការរបស់អ្នកប្រើ។ វាឆ្លើយសំណួរ៖ **«User ចង់ឱ្យ System មានអ្វីខ្លះ?»**
> *(URS = User Requirements. It answers: "What does the user want the system to have?")*

### 5.1 Secure Access
- Login ដោយ PIN (PIN login)
- Fingerprint Authentication
- Mobile Credentials
- Family Access
- Guest Access
- Role-based Permissions

### 5.2 Security Modes
| Mode | Description |
|---|---|
| **Home Mode** | ប្រើពេលអ្នករស់នៅក្នុងផ្ទះ។ User អាចកំណត់ Sensors ខ្លះឱ្យ Active និងខ្លះឱ្យ Inactive — used while occupants are home; some sensors active, some inactive. |
| **Away Mode** | ប្រើពេលអ្នកចេញពីផ្ទះ។ Sensors ដែលបានកំណត់សម្រាប់ Security ត្រូវបាន Activate — used when away; all configured security sensors are activated. |
| **Disarm Mode** | បិទ Security Monitoring សម្រាប់ User ដែលមានសិទ្ធិ — turns off monitoring for authorized users. |
| **Scheduled Mode** | អាចកំណត់ម៉ោងឱ្យ System Arm ឬ Disarm ដោយស្វ័យប្រវត្តិ — automatic arm/disarm on a schedule. |

### 5.3 Sensor Monitoring
- Motion Detection
- Door Monitoring
- Window Monitoring
- Glass-Break Detection

### 5.4 Real-Time Alerts
- Push Notification
- SMS Alert
- Local Siren/Alarm

### 5.5 Remote Access
- ពិនិត្យ System Status (Check system status)
- Arm/Disarm ពីចម្ងាយ (Remote arm/disarm)
- មើល Camera (View camera)
- មើល Alerts (View alerts)
- មើល Event History (View event history)

### 5.6 Video Surveillance
- Live Camera Streaming
- Manual Recording
- Motion-triggered Recording
- មើល Recordings ចាស់ (View past recordings)

### 5.7 Device Management
- Add Device
- Remove Device
- Configure Device
- Check Device Status

---

## 6. Use Case Analysis

> Use Case គឺជាវិធីបង្ហាញថា Actor មាន Interaction អ្វីជាមួយ System។
> *(A use case shows how an actor interacts with the system.)*

### 6.1 Actors
- Homeowner
- Family Member
- Guest
- Administrator
- IoT Sensors
- Security Camera

### 6.2 Main Use Cases
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

### 6.3 Core Intrusion Workflow
```
Sensor detects event
      ↓
HomeSafe receives event
      ↓
Check active Security Mode
      ↓
Determine: Intrusion or not?
      ↓
Activate Alarm
      ↓
Start Recording
      ↓
Send Notification
      ↓
Homeowner reviews the event
```
*(Khmer: Sensor រកឃើញហេតុការណ៍ → HomeSafe ទទួល Event → ពិនិត្យ Security Mode → សម្រេចថាជា Intrusion ឬអត់ → Activate Alarm → ចាប់ផ្តើម Recording → ផ្ញើ Notification → Homeowner ពិនិត្យ Event។)*

### 6.4 Key Relationships
- **Homeowner** interacts with Login, Arm/Disarm, Camera, Alerts, and Recordings.
- **Administrator** manages Users and Devices.
- **Sensors** are the source of security events; the system responds according to configured mode and rules.

---

## 7. Traceability to SRS

This URD defines *what the user needs*. Each item here is translated into concrete functional requirements (FR-01 … FR-11) and non-functional requirements in the accompanying [`SRS.md`](./SRS.md).

---

## 8. Conclusion

HomeSafe Smart Security responds to the need for a home security system that offers secure access, continuous sensor monitoring, real-time alerts, remote control, and video surveillance — supporting Home/Away/Disarm modes, user roles, automated responses, and security event management, while explicitly excluding direct emergency-service integration, professional monitoring centers, facial recognition, and full energy/water management for this phase.

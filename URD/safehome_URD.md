# User Requirements Document (URD) — HomeSafe Smart Security

ឯកសារនេះពិពណ៌នាអំពី **អ្វីដែល User ចង់ឱ្យ System មាន** — សរសេរជា Language ដែល Non-Technical Stakeholder អាចយល់បាន។ វាខុសពី SRS ត្រង់ SRS ប្រែ Requirements ទាំងនេះទៅជា Technical Specification សម្រាប់ Developer។

---

## 1. Purpose (គោលបំណង)

ឯកសារនេះកំណត់នូវ User-Level Requirements សម្រាប់ HomeSafe Smart Security — Product Line សម្រាប់ Home Automation & Security ។ វាសម្រាប់ Homeowner, Family Member, Guest, Administrator, និង Developer Team ប្រើប្រាស់ជាមូលដ្ឋានសម្រាប់ SRS, Design, និង Testing។

## 2. Product Perspective (ទស្សនវិស័យផលិតផល)

HomeSafe គឺជា Smart Home Security Product ថ្មី ដែលភ្ជាប់ IoT Sensors, Camera, និង Mobile Application ចូលគ្នាតាមរយៈ Local Control Hub ។ Hub ត្រូវបានតភ្ជាប់ទៅ Cloud/Server ដើម្បីផ្តល់ Remote Access, Push Notification, និង Event History ។ វាមិនមែនជា Standalone Device ទេ — វាជា **Product Line** ដែលមាន Hardware (Hub, Sensors, Camera) + Software (Mobile App, Backend) ។

## 3. User Classes and Characteristics (ថ្នាក់ User)

| User Class | លក្ខណៈពិសេស |
|---|---|
| **Homeowner** | Primary User, មានសិទ្ធិពេញលេញ (Full Control) លើ System — Arm/Disarm, Configure, មើល Camera, គ្រប់គ្រង User ដទៃ |
| **Family Member** | មានសិទ្ធិមួយចំនួន (ឧ. Arm/Disarm, មើល Camera) ប៉ុន្តែមិនអាច Manage Devices ឬ Users បានទេ |
| **Guest** | Temporary Access, សិទ្ធិមានកម្រិត (ឧ. Disarm ក្នុងរយៈពេលកំណត់) |
| **Administrator** | Technical Role — Manage Devices, Reconfigure Sensors, Troubleshoot System |
| **IoT Devices** (Sensors/Camera) | មិនមែន Human User ទេ ប៉ុន្តែជា Actor ដែល Interact ជាមួយ System ដោយស្វ័យប្រវត្តិ |

Family Member និង Guest ភាគច្រើនមិនមែនជា Technical User ទេ — Interface ត្រូវសាមញ្ញ។ Administrator ត្រូវការ Interface លម្អិតជាង សម្រាប់ Device Configuration។

## 4. Operating Environment (បរិយាកាសប្រតិបត្តិការ)

| Component | Environment |
|---|---|
| Mobile Application | iOS 14+ និង Android 10+ |
| Local Control Hub | Embedded Device ភ្ជាប់ជាមួយ Home WiFi Network (2.4GHz/5GHz) |
| Sensors (Motion, Door/Window, Glass-Break) | ភ្ជាប់ទៅ Hub តាម Wireless Protocol (ឧ. Zigbee/Z-Wave) ឬ Wired |
| Camera | ភ្ជាប់តាម WiFi ឬ PoE (Power over Ethernet), គាំទ្រ Live Streaming |
| Backend/Server | Cloud-hosted, គាំទ្រ Multiple Household ក្នុងពេលតែមួយ |
| Internet Connectivity | ត្រូវការសម្រាប់ Remote Access, Push Notification, Video Streaming — System នៅតែដំណើរការ Local Functions (Arm/Disarm តាម Control Panel) ទោះបីគ្មាន Internet |

## 5. Design and Implementation Constraints (ដែនកំណត់)

- Sensors និង Camera ត្រូវប្រើ Protocol ស្តង់ដារ ដើម្បីអាចផ្លាស់ប្តូរ/បន្ថែម Device ថ្មីពី Manufacturer ផ្សេងគ្នាបាន (Interoperability)
- Push Notification ត្រូវពឹងផ្អែកលើ Third-Party Service (ឧ. Firebase Cloud Messaging សម្រាប់ Push, SMS Gateway សម្រាប់ SMS)
- Data ទាំងអស់ (Video, Event Log, Credential) ត្រូវបាន Encrypt តាម AES-256 ស្របតាម Non-Functional Security Requirement
- Local Control Hub ត្រូវមាន Backup Power (Battery) ដើម្បីបន្តដំណើរការនៅពេលអគ្គិសនីដាច់
- Household Hub មួយត្រូវគាំទ្រដល់ 50 Devices តាម Scalability Target ដែលបានកំណត់

## 6. Assumptions and Dependencies (សន្មតិកម្ម និង Dependency)

- Homeowner មាន Smartphone ដែលអាចដំឡើង Mobile App
- ផ្ទះមាន WiFi Network ដែលមានស្ថេរភាព
- Sensors និង Camera ត្រូវបានដំឡើងត្រឹមត្រូវដោយ Technician ឬ User ខ្លួនឯង
- Push Notification/SMS Service ពីភាគីទីបី (ឧ. Firebase, Twilio) មានស្ថេរភាព និងអាចប្រើប្រាស់បាន
- System សន្មតថា Time/Date របស់ Hub ត្រឹមត្រូវ សម្រាប់ Scheduled Mode

## 7. User Requirements (តម្រូវការ User — Feature Level)

### 7.1 Secure Access
- Login ដោយ PIN
- Fingerprint Authentication
- Mobile Credentials
- Family Access / Guest Access
- Role-based Permissions

### 7.2 Security Modes
- **Home Mode** — Active សម្រាប់ Sensor ខ្លះ, User នៅផ្ទះ
- **Away Mode** — Active គ្រប់ Sensors, User ចេញពីផ្ទះ
- **Disarm Mode** — បិទ Security Monitoring
- **Scheduled Mode** — Arm/Disarm ស្វ័យប្រវត្តិតាមម៉ោង

### 7.3 Sensor Monitoring
Motion Detection, Door Monitoring, Window Monitoring, Glass-Break Detection

### 7.4 Real-Time Alerts
Push Notification, SMS Alert, Local Siren/Alarm

### 7.5 Remote Access
ពិនិត្យ Status, Arm/Disarm ពីចម្ងាយ, មើល Camera, មើល Alerts, មើល Event History

### 7.6 Video Surveillance
Live Streaming, Manual Recording, Motion-triggered Recording, មើល Recording ចាស់

### 7.7 Device Management
Add/Remove/Configure Device, Check Device Status

## 8. Priority (អាទិភាព)

| Feature Group | Priority | Increment |
|---|---|---|
| Secure Access, Security Modes | Essential | Increment 1 |
| Remote Access | Essential | Increment 2 |
| Sensor Monitoring, Real-Time Alerts (Alarm) | Essential | Increment 3 |
| Video Surveillance | Moderate | Increment 4 |
| Real-Time Alerts (Notification), Scheduled Mode | Moderate | Increment 5 |

---

## Reference

សូមមើល `SRS/SRS.md` សម្រាប់ Technical Specification ពេញលេញ, និង `Diagram/use_case_diagram.md` សម្រាប់ Actor Interaction ។

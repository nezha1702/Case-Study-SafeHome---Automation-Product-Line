## Author : Chor Channe 
# 01-Homeowner Requirements: SafeHome Product Line Case Study(Testing)

## 1. System Context & Overview
* **System Purpose**: SafeHome is a home automation and security product line designed to affordably digitize, monitor, and control residential security and environmental automation features[cite: 1].
* **System Description**: The system integrates hardware sensors (e.g., motion, door/window sensors), video cameras, control panels, and software interfaces running on personal computers or dedicated devices, allowing homeowners to manage their security settings locally or remotely[cite: 1].
* **Environmental Assumptions & Constraints**:
  * Homeowners have standard electrical power and home communications infrastructure (e.g., landline telephone, internet connectivity)[cite: 1].
  * Security sensors and video cameras are properly installed at critical ingress/egress points and indoor rooms[cite: 1].
  * Hardware components (control panels, sensors) interact with software across dedicated hardware interfaces[cite: 1].

---

## 2. Requirements Gathered from Stakeholders (Elicitation Narrative)
> *"As a homeowner, I want an affordable system that keeps my home secure and allows me to control basic automation functions easily. I need to be able to arm and disarm the security system using a master control panel or my personal computer. If an intrusion or sensor trip occurs while the system is armed, it must sound an alarm, dial an emergency response firm, and display which sensor was triggered. I also want to observe my home remotely using video cameras to ensure everything is safe. The system must be extremely easy to use, highly reliable so false alarms are minimized, and protected by password access so unauthorized people cannot change my security settings or turn off the alarm."*

---

## 3. Homeowner Needs & Expectations

### 3.1 Stakeholders & Actors
* **Homeowner / User**: Primary operator who arms/disarms the system, configures preferences, views camera feeds, and responds to system status[cite: 1].
* **Sensors (Motion, Door, Window, Smoke, etc.)**: Hardware components that sense physical changes and report events to the software system[cite: 1].
* **Cameras**: Video acquisition devices used for home monitoring[cite: 1].
* **Monitoring Agency / Alarm Response Company**: External service notified automatically during emergency event activations[cite: 1].

---

## 4. Functional Homeowner Requirements

* **UF-01: System Arming and Disarming**
  * The homeowner shall be able to arm or disarm the security system via a dedicated control panel or remote system interface[cite: 1].
* **UF-02: Sensor Status Monitoring**
  * The system shall continuously monitor connected security sensors (e.g., door contacts, motion detectors) and display their operational status to the homeowner[cite: 1].
* **UF-03: Alarm Activation and Emergency Response**
  * Upon detection of an intrusion event when armed, the system shall trigger an audible alarm and automatically initiate a phone call/signal to an external monitoring agency[cite: 1].
* **UF-04: Video Camera Monitoring**
  * The homeowner shall be able to view live or recorded video streams from cameras installed throughout the residence[cite: 1].
* **UF-05: Event and Zone Identification**
  * The system shall identify and display the specific zone or sensor location where an event/alarm was triggered[cite: 1].
* **UF-06: System Configuration and User Management**
  * The homeowner shall be able to configure user access codes, system settings, and zone parameters[cite: 1].

---

## 5. Non-Functional Homeowner Requirements

* **Non-UF-01: Security & Authentication**
  * System functions (arming, disarming, configuration) must require valid user password/passcode authentication to prevent unauthorized tampering[cite: 1].
* **Non-UF-02: Usability**
  * The user interface must be intuitive, easy to navigate, and minimize memory load for non-technical homeowners[cite: 1].
* **Non-UF-03: Reliability & Dependability**
  * The system must operate reliably without system crashes, ensuring continuous protection of the home[cite: 1].
* **Non-UF-04: Performance & Timeliness**
  * The system must process sensor state changes and trigger alarm responses within critical real-time bounds upon intrusion detection[cite: 1].

---

## 6. Source References (Pressman 7th Edition)
* **Chapter 5**: Understanding Requirements (Case study setup & requirements elicitation techniques)[cite: 1].
* **Chapter 6**: Requirements Modeling: Scenarios, Information, and Analysis Classes (SafeHome use cases and domain analysis)[cite: 1].
* **Chapter 7**: Requirements Modeling: Flow, Behavior, Patterns, and WebApps (SafeHome control specifications and state behavior)[cite: 1].
* **Chapter 9**: Architectural Design (SafeHome architectural genres and instantiations)[cite: 1].
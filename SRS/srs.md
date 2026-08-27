# 02-System Requirements Specification (SRS): SafeHome System

## 1. Introduction & System Scope
The SafeHome system provides integrated security management and home automation capabilities[cite: 1]. This document specifies the functional and non-functional system requirements derived from stakeholder needs and formal architectural patterns detailed in the textbook[cite: 1].

---

## 2. System Requirements

### 2.1 Functional Requirements (FR)

| Requirement ID | System Requirement | Traces to URD | Source Classification |
| :--- | :--- | :--- | :--- |
| **SR-F01** | The system shall provide a user authentication mechanism requiring a valid passcode/password before granting access to control features[cite: 1]. | F-HO-01, NF-HO-01 | **Explicit** (Pressman Ch. 5, 6)[cite: 1] |
| **SR-F02** | The system shall accept commands to Arm (Away/Home) and Disarm the security system[cite: 1]. | F-HO-01 | **Explicit** (Pressman Ch. 6)[cite: 1] |
| **SR-F03** | The system shall continuously read digital signals from installed sensors (motion, contact, environmental)[cite: 1]. | F-HO-02 | **Explicit** (Pressman Ch. 7)[cite: 1] |
| **SR-F04** | Upon receiving an intrusion signal while armed, the system shall activate the local audible alarm/siren[cite: 1]. | F-HO-03 | **Explicit** (Pressman Ch. 7)[cite: 1] |
| **SR-F05** | The system shall place an automated call/data transmission to a designated monitoring agency upon alarm activation[cite: 1]. | F-HO-03 | **Explicit** (Pressman Ch. 6, 7)[cite: 1] |
| **SR-F06** | The system shall route video signals from home cameras to the user display interface[cite: 1]. | F-HO-04 | **Explicit** (Pressman Ch. 6, 9)[cite: 1] |
| **SR-F07** | The system shall display alarm zone status and specific sensor location during an alert state[cite: 1]. | F-HO-05 | **Explicit** (Pressman Ch. 6)[cite: 1] |
| **SR-F08** | The system shall allow the user to configure system parameters (e.g., delay times, passcodes, sensor zones)[cite: 1]. | F-HO-06 | **Derived/Interpreted** (Pressman Ch. 5, 6)[cite: 1] |

### 2.2 Non-Functional Requirements (NFR)

| Requirement ID | System Requirement | Traces to URD | Source Classification |
| :--- | :--- | :--- | :--- |
| **SR-NF01** | **Security**: Passcodes and control transmissions must be protected against unauthorized access and tampering[cite: 1]. | NF-HO-01 | **Explicit** (Pressman Ch. 5, 14)[cite: 1] |
| **SR-NF02** | **Performance/Real-Time Response**: Sensor input processing and state transitions must occur within strict deterministic time bounds[cite: 1]. | NF-HO-04 | **Explicit** (Pressman Ch. 7, 18)[cite: 1] |
| **SR-NF03** | **Usability**: Graphical user interfaces must conform to standard usability patterns to minimize user cognitive memory load[cite: 1]. | NF-HO-02 | **Explicit** (Pressman Ch. 11)[cite: 1] |
| **SR-NF04** | **Reliability**: The software system must operate continuously without unhandled exceptions or system failure during operation[cite: 1]. | NF-HO-03 | **Explicit** (Pressman Ch. 14, 16)[cite: 1] |

---

## 3. Relationship Between Functional and Non-Functional Requirements

Non-functional requirements act as direct operational constraints on functional execution:
* **Functional Base Requirement**: `SR-F02` ("The system shall accept commands to Arm/Disarm").
  * **Non-Functional Constraint**: `SR-NF01` & `SR-F01` constrain this action by requiring that arming/disarming operations cannot execute until security authentication successfully validates user credentials[cite: 1].
* **Functional Base Requirement**: `SR-F04` ("The system shall activate the local audible alarm upon intrusion").
  * **Non-Functional Constraint**: `SR-NF02` constrains execution by requiring the state change from sensor trip to alarm sound to occur within real-time latency limits[cite: 1].

---

## 4. Stakeholders Matrix

| Stakeholder | Role | Interest in System | Relevant Requirements |
| :--- | :--- | :--- | :--- |
| **Homeowner** | End User / Operator | Primary operation, ease of use, family safety, property protection[cite: 1]. | SR-F01 – SR-F08, SR-NF01 – SR-NF04[cite: 1] |
| **System Developer / Architect** | Software Engineer | System modularity, maintainability, architectural integrity[cite: 1]. | SR-NF02, SR-NF04[cite: 1] |
| **Monitoring Agency** | External Service Receiver | Timely and reliable receipt of distress/alarm signals[cite: 1]. | SR-F05, SR-NF02[cite: 1] |

---

## 5. Supporting UML / Design Information

### 5.1 Use Case Diagram Elements
* **Actors**: Homeowner, Sensors, Monitoring Agency[cite: 1].
* **Use Cases**: `Arm/Disarm System`, `Configure System Settings`, `Monitor Sensors`, `Trigger Alarm`, `View Video Stream`[cite: 1].

### 5.2 Class Diagram Elements (Actuator-Sensor Pattern)
* **Classes**: `ControlPanel`, `Sensor`, `Actuator`, `Alarm`, `Camera`, `User`[cite: 1].
* **Attributes**: 
  * `Sensor`: `sensorID`, `status` (active/inactive), `zoneLocation`[cite: 1].
  * `ControlPanel`: `systemStatus` (armed/disarmed), `masterPasscode`[cite: 1].
* **Operations**:
  * `Sensor`: `readStatus()`, `trip()`[cite: 1].
  * `ControlPanel`: `arm()`, `disarm()`, `validatePasscode()`[cite: 1].
  * `Alarm`: `soundAlarm()`, `notifyAgency()`[cite: 1].
* **Relationships**: `ControlPanel` manages multiple `Sensor` and `Actuator` objects (Aggregation/Composition)[cite: 1].

### 5.3 Behavioral & Flow Diagrams
* **State Diagram States**: `Disarmed`, `Armed`, `Alarming`, `System Configuration`[cite: 1].
* **Sequence Diagram Interactions**: Homeowner enters passcode $\rightarrow$ `ControlPanel` validates passcode $\rightarrow$ `ControlPanel` updates status to `Armed` $\rightarrow$ `Sensors` set to active monitoring mode[cite: 1].

---

## 6. Requirements Traceability Matrix

| Stakeholder Need | URD | SRS | UML / Design Element | Source |
| :--- | :--- | :--- | :--- | :--- |
| Secure access control | F-HO-01, NF-HO-01 | SR-F01, SR-NF01 | `ControlPanel::validatePasscode()` | Ch. 5, 6, 11[cite: 1] |
| System status control | F-HO-01 | SR-F02 | `Arm/Disarm System` Use Case | Ch. 6[cite: 1] |
| Intrusion Detection | F-HO-02, F-HO-03 | SR-F03, SR-F04 | `Sensor` class, `Monitor Sensors` Use Case | Ch. 6, 7[cite: 1] |
| Emergency notification | F-HO-03 | SR-F05 | `Alarm::notifyAgency()` | Ch. 6, 7[cite: 1] |
| Remote Visuals | F-HO-04 | SR-F06 | `Camera` class, `View Video Stream` Use Case | Ch. 6, 9[cite: 1] |

---

## 7. Source Verification

### A. Explicitly Stated in Book
* Functional requirements for arming/disarming, sensor monitoring, camera display, and remote agency notification[cite: 1].
* Actuator-Sensor analysis pattern application for home security domain[cite: 1].
* Architectural genre definitions and state-based modeling for SafeHome[cite: 1].

### B. Derived from Book
* Explicit mapping of URD numerical IDs to refined SRS requirement IDs (`SR-F01` to `SR-F08`).
* Formal separation of security constraints as non-functional wrappers on specific operational use cases.

### C. Not Supported by Book
* Specific numerical metrics such as "alarm must dial within 3.5 seconds" or "system availability must be 99.999%." (These are intentionally excluded to adhere strictly to Pressman's text)[cite: 1].
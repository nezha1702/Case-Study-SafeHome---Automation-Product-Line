# SafeHome Requirements — Summary and Software Requirements Specification

*Based on the SafeHome case study in Roger S. Pressman, "Software Engineering: A Practitioner's Approach," 7th Edition*

---

## Summary Paragraph

SafeHome is a home-management and security product line, developed for a market growing at roughly 40 percent a year, whose first release is the home security function: homeowners configure the wireless-sensor-based system through a wall-mounted control panel, a PC, or the Internet, arm it in "stay" or "away" mode, and have it recognize situations such as illegal entry, fire, flooding, or dangerous carbon monoxide levels and automatically notify a monitoring service by phone. Building on that foundation, the product line adds a home-surveillance function that lets the homeowner view, pan/zoom, record, and play back footage from house cameras — locally or remotely over the Internet — and a home-management function that lets the homeowner control lights, appliances, HVAC, and (optionally) audiovisual devices from a floor-plan interface, including preset "home," "away," "overnight travel," and "extended travel" modes. All three functions share a common look-and-feel interface accessed through the control panel, an installed PC, or a password/ID-protected website, and are bound by constraints such as recognizing sensor events within one second, redialing the monitoring service every 20 seconds until connected, and remaining simple enough that a homeowner never needs to consult a manual.

---

## 1. Introduction

### 1.1 Purpose
This document specifies the requirements for the SafeHome system, a wireless home security, surveillance, and home-management product, as elicited in the SafeHome case study.

### 1.2 Project Scope
SafeHome enables homeowners to configure and monitor a home security system, view and record surveillance camera output, and control home devices (lighting, appliances, HVAC, and optionally audiovisual equipment), all accessible through a control panel, a local PC, or a password-protected website over the Internet.

### 1.3 Intended Audience
Software engineers, marketing and product management staff, and other stakeholders participating in SafeHome's requirements engineering and design.

---

## 2. Overall Description

### 2.1 Product Perspective
SafeHome is a new, standalone consumer product line composed of wireless sensors, a control panel, cameras, device controllers, and companion PC/web software that communicates with a central monitoring service.

### 2.2 User Classes and Characteristics
- **Homeowner** — the primary actor; arms/disarms the system, responds to alerts, views cameras, and controls devices. No technical background assumed; the interface must be intuitive.
- **Setup manager** — typically the homeowner in a different role, responsible for initial installation and configuration.
- **Sensors** — devices (window/door, motion, smoke, flood, carbon monoxide) that report events to the system.
- **Monitoring and response subsystem** — the central station that receives alarm notifications and initiates a response.

### 2.3 Operating Environment
The system runs on a homeowner's PC and a dedicated SafeHome control panel installed in the home, communicates with wireless sensors and cameras, and is accessible remotely via a browser over the Internet.

### 2.4 Design and Implementation Constraints
- Must interface directly to a standard telephone line for dialing the monitoring service.
- Must recognize when a sensor is not operating correctly.
- Must use two-level password protection (each password at least eight characters) for Internet-based access.
- Interfaces for security, surveillance, and home management must share the same look and feel.

### 2.5 Assumptions and Dependencies
- Sensors and device controllers use a wireless interface.
- A monitoring agency is available to receive automated phone notifications.

---

## 3. System Features (Functional Requirements)

### 3.1 Home Security Function
- **FR-1** The system shall allow the homeowner to enter a password to enable all other interactions.
- **FR-2** The system shall allow the homeowner to inquire about the status of a security zone.
- **FR-3** The system shall allow the homeowner to inquire about the status of an individual sensor.
- **FR-4** The system shall provide a panic button for use in an emergency.
- **FR-5** The system shall allow the homeowner to activate ("stay" or "away") or deactivate the security system.
  - "Stay" shall activate perimeter sensors only (interior motion sensors deactivated).
  - "Away" shall activate all sensors.
- **FR-6** During installation, the system shall let the setup manager assign a number and type to each sensor, program a master arm/disarm password, and input telephone number(s) to be dialed on an event.
- **FR-7** The system shall detect undesirable situations — illegal entry, fire, flooding, dangerous carbon monoxide levels, and others — via wireless sensors.
- **FR-8** When a sensor event is recognized, the system shall sound an audible alarm after a homeowner-configurable delay.
- **FR-9** The system shall automatically telephone a monitoring agency, reporting the event and its location, when a sensor event is detected.
- **FR-10** The system shall display a not-ready message on the control panel when a sensor (e.g., an open door or window) prevents arming, and shall clear the message once the condition is resolved.
- **FR-11** The system shall display prompting messages and status information through the control panel, PC, or browser interface.

### 3.2 Home Surveillance Function
- **FR-12** The system shall let the homeowner select a camera to view from a house floor plan.
- **FR-13** The system shall let the homeowner request thumbnail views from all cameras simultaneously and select one to enlarge.
- **FR-14** The system shall display camera views in a PC window at (at least) one frame per second.
- **FR-15** The system shall let the homeowner control pan and zoom for a selected camera.
- **FR-16** The system shall let the homeowner selectively record and replay camera output.
- **FR-17** The system shall let the homeowner block access to one or more cameras with a specific password.
- **FR-18** The system shall let the homeowner access camera surveillance via the Internet, including logging in with a user ID and two passwords before displaying camera functions.

### 3.3 Home Management Function
- **FR-19** The system shall let the homeowner turn specific lights and appliances on and off via a wireless interface, selected from a floor-plan display.
- **FR-20** The system shall let the homeowner set heating and air-conditioning temperatures.
- **FR-21** The system shall optionally let the homeowner control audiovisual devices (audio, television, DVD, digital recorders).
- **FR-22** The system shall let the homeowner apply a single preset ("home," "away," "overnight travel," "extended travel") that configures settings across all devices at once.
- **FR-23** In "overnight travel" and "extended travel" modes, the system shall turn lights on and off at randomized intervals and manage heating/air conditioning automatically.
- **FR-24** The system shall let the homeowner override any preset setting remotely via the Internet, subject to password protection.

### 3.4 Common Access and Configuration
- **FR-25** The system shall let the homeowner log on to the SafeHome Products website with a user ID and two passwords to access all functions of their installed system.
- **FR-26** Upon login, the system shall display all major function buttons (security, surveillance, home management).
- **FR-27** The system shall provide a consistent interface — control panel, PC, or browser — across all functions.

---

## 4. External Interface Requirements

### 4.1 User Interfaces
- Wall-mounted control panel with keypad and LCD/status display (Figure 5.1 style: arm/disarm keys, zone indicators, panic button).
- PC-based graphical interface with floor-plan navigation for surveillance and device control.
- Browser-based interface providing the same functionality remotely.

### 4.2 Hardware Interfaces
- Wireless sensors (door/window, motion, smoke, flood, carbon monoxide).
- Wireless-interface device controllers for lights, appliances, HVAC, and audiovisual equipment.
- Surveillance cameras with pan/zoom capability.

### 4.3 Software Interfaces
- SafeHome Products website for remote/Internet-based access and account authentication.

### 4.4 Communications Interfaces
- Standard telephone line for automated dialing of the monitoring agency.
- Internet connection for remote access to security, surveillance, and home-management functions.

---

## 5. Other Nonfunctional Requirements

### 5.1 Performance Requirements
- **NFR-1** A sensor event shall be recognized within one second of occurrence.
- **NFR-2** Camera video shall display at a minimum of one frame per second.
- **NFR-3** If the monitoring agency's phone line is unavailable, the system shall redial every 20 seconds until a connection is obtained.

### 5.2 Safety Requirements
- **NFR-4** The system shall reliably detect and report fire, flooding, and carbon monoxide events in addition to intrusion, since these involve life-safety risk.
- **NFR-5** The system shall support an event-priority scheme so life-critical events are handled ahead of lower-priority ones.

### 5.3 Security Requirements
- **NFR-6** Internet-based access shall require a user ID and two passwords, each at least eight characters long.
- **NFR-7** The website used for remote access shall be secured (encrypted) to protect user credentials and system data.
- **NFR-8** The system shall support a separate password to restrict access to specific surveillance cameras.

### 5.4 Software Quality Attributes
- **NFR-9** Usability: the interface shall be intuitive enough that a homeowner does not need to consult a manual.
- **NFR-10** Consistency: security, surveillance, and home-management interfaces shall share a common look and feel.
- **NFR-11** Reliability: the system shall recognize and report when a sensor is not operating correctly.
- **NFR-12** Maintainability/extensibility: the architecture shall support adding new functions to the SafeHome product line (security was the first release, followed by surveillance and home management) without redesigning existing functions.

---

## 6. Other Requirements
- Appendix A (Glossary), Appendix B (Analysis Models, e.g., use cases and UML diagrams), and Appendix C (Issues List — e.g., handling of a forgotten password) would typically follow in a complete SRS, per the Wiegers SRS template referenced in the source text.
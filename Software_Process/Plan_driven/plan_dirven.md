# Plan-Driven Development — HomeSafe Smart Security

## What is Plan-Driven? (តើ Plan-Driven គឺជាអ្វី?)

Plan-Driven គឺជា Software Development Approach ដែល Activities ភាគច្រើន (Requirements, Design, Schedule, Deliverables) ត្រូវបាន **គ្រោងទុកជាមុន** មុនពេល Implementation ចាប់ផ្តើម។ Progress ត្រូវបានវាស់ស្ទង់ធៀបនឹង Plan ដែលបានកំណត់។ លក្ខណៈសំខាន់ៗ:

- Requirements ត្រូវបានកំណត់ និង Freeze ជាប់ពីដើម
- ត្រូវការ Documentation ច្រើន និងលម្អិត សម្រាប់ Traceability
- ការផ្លាស់ប្តូរនៅពេលក្រោយមានតម្លៃថ្លៃ
- សមស្របសម្រាប់ System ដែលមាន Requirements ច្បាស់លាស់ ឬត្រូវការ Verification/Validation យ៉ាងម៉ត់ចត់ (Safety-Critical Systems)
- ឧទាហរណ៍ Model: **Waterfall**, **V-Model**

## តើ Plan-Driven ត្រូវបានប្រើនៅឯណានៅក្នុង HomeSafe?

HomeSafe ប្រើ **V-Model Principles** ជា Model គាំទ្រ (Supporting Model) សម្រាប់ Verification និង Validation នៃ **Security Features ដែលសំខាន់បំផុត** ព្រោះ Feature ទាំងនេះមិនអាចមាន Error បានទេ:

- User Authentication
- Intrusion Detection
- Alarm
- Notification

### V-Model Flow

```
Requirement          →  Acceptance Testing
    ↓                          ↑
  Design            →  System Testing
    ↓                          ↑
Implementation      →  Unit / Integration Testing
    ↓                          ↑
              Build
```

រាល់ដំណាក់កាល Development (Requirement, Design, Implementation) មាន Testing Phase ដែលត្រូវនឹងវាដោយផ្ទាល់ — Requirement ត្រូវផ្គូផ្គងជាមួយ Acceptance Testing, Design ត្រូវផ្គូផ្គងជាមួយ System Testing, Implementation ត្រូវផ្គូផ្គងជាមួយ Unit/Integration Testing។

## Why Plan-Driven fits these parts of HomeSafe

- Authentication, Intrusion Detection, Alarm និង Notification គឺជា Security-Critical Functions — កំហុសនៅផ្នែកទាំងនេះអាចធ្វើឱ្យផ្ទះគ្មានសុវត្ថិភាព
- ត្រូវការ Verification/Validation ជាផ្លូវការ និង Documentation ច្បាស់លាស់ មុនពេលដាក់ឱ្យប្រើ
- Requirements សម្រាប់ Security Features ជាទូទៅមានស្ថិរភាព មិនផ្លាស់ប្តូរញឹកញាប់ដូច UI/UX

## Agile vs Plan-Driven — Quick Comparison

| | Plan-Driven | Agile |
|---|---|---|
| Requirements | កំណត់ជាប់ពីដើម | អាចផ្លាស់ប្តូរបាន |
| Documentation | ច្រើន, លម្អិត | តិចតួច, គ្រាន់តែគ្រប់គ្រាន់ |
| ការផ្លាស់ប្តូរ (Change) | មានតម្លៃថ្លៃពេលយឺត | ទទួលយកបានគ្រប់ពេល |
| សមស្របសម្រាប់ | Safety-critical, Scope ស្ថិរភាព | Scope មិនច្បាស់ / User-facing features |
| ប្រើនៅក្នុង HomeSafe | V-Model (Authentication, Intrusion Detection, Alarm, Notification) | Agile Scrum — សូមមើល `agile.md` |

## Reference

ចម្លងចេញពី Section 11.3 (V-Model Principles) នៃឯកសារ *HomeSafe Smart Security — Software Engineering Case Study*។

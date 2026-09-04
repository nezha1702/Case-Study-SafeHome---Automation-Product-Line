# Agile Development — HomeSafe Smart Security

## What is Agile? (តើ Agile គឺជាអ្វី?)

Agile គឺជា Software Development Approach ដែល Planning, Design, និង Implementation ត្រូវបានធ្វើ **ជាបន្តបន្ទាប់ និងចលនា (iterative)** ជំនួសឱ្យការគ្រោងទុកទាំងអស់ពីដើម។ Requirements អាចផ្លាស់ប្តូរបាន ហើយ Team ផ្តល់តម្លៃលើ:

- ការចែកចាយ Software ដែលដំណើរការបានលឿន (Working software over documentation)
- ការសហការជាមួយ Client/User ជាបន្តបន្ទាប់ (Customer collaboration)
- ការឆ្លើយតបនឹងការផ្លាស់ប្តូរ (Responding to change over following a plan)
- ការទំនាក់ទំនងផ្ទាល់ក្នុង Team

## តើ Agile ត្រូវបានប្រើនៅឯណានៅក្នុង HomeSafe?

HomeSafe ប្រើ **Agile Scrum** ជា Model គាំទ្រ (Supporting Model) — មិនមែនជា Model សំខាន់ទេ (Primary គឺ Incremental Model)។ Scrum ត្រូវបានប្រើដើម្បីធ្វើឱ្យ Development មានភាពបត់បែន និងទទួល Feedback ជាបន្តបន្ទាប់ក្នុងអំឡុងពេលអភិវឌ្ឍ Feature នីមួយៗ។

### Sprint Breakdown

| Sprint   | Feature                                    |
| -------- | ------------------------------------------ |
| Sprint 1 | Login (Authentication)                     |
| Sprint 2 | Arm / Disarm                               |
| Sprint 3 | Sensors (Motion, Door/Window, Glass-Break) |
| Sprint 4 | Camera (Live Streaming, Recording)         |
| Sprint 5 | Notification (Push, SMS)                   |

Rhythm របស់ Sprint នីមួយៗ: **Planning → Development → Testing → Review → Feedback**។

## Why Agile fits these parts of HomeSafe

- Features ទាំងនេះទាក់ទងផ្ទាល់នឹង User Experience (Login, Camera, Notification) ដែល Requirements អាចផ្លាស់ប្តូរបន្ទាប់ពី User Feedback
- Short Sprints អនុញ្ញាតឱ្យ Team សាកល្បង UI/UX Concept និងកែលម្អលឿន
- ជួយបញ្ចុះ Risk សម្រាប់ Feature ដែលមិនទាន់ច្បាស់ 100% តាំងពីដើម

## Agile vs Plan-Driven — Quick Comparison

|                         | Agile                                                                  | Plan-Driven                                                                                               |
| ----------------------- | ---------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------- |
| Requirements            | អាចផ្លាស់ប្តូរបាន                                                      | កំណត់ជាប់ពីដើម                                                                                            |
| Documentation           | តិចតួច, គ្រាន់តែគ្រប់គ្រាន់                                            | ច្រើន, លម្អិត                                                                                             |
| ការផ្លាស់ប្តូរ (Change) | ទទួលយកបានគ្រប់ពេល                                                      | មានតម្លៃថ្លៃពេលយឺត                                                                                        |
| សមស្របសម្រាប់           | Scope មិនច្បាស់ / User-facing features                                 | Safety-critical, Scope ស្ថិរភាព                                                                           |
| ប្រើនៅក្នុង HomeSafe    | Agile Scrum (Login, Arm/Disarm, Sensors, Camera, Notification sprints) | V-Model (Authentication, Intrusion Detection, Alarm, Notification verification) — សូមមើល `plan_dirven.md` |

## Reference

ចម្លងចេញពី Section 11.2 (Agile Scrum) នៃឯកសារ _HomeSafe Smart Security — Software Engineering Case Study_।

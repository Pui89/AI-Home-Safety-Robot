# PUI89 AI HOME — Product Requirements Specification v1.0

**Document status:** Proposed engineering baseline — review required  
**Version:** 1.0  
**Prepared:** 26 November 2026  
**Product:** PUI89 AI HOME — Indoor Four-Wheel Home Assistant  
**Authority:** Requirements and concept baseline only. This is not a released design, CAD package, production drawing, verified BOM, safety case, prototype record, or certification.

## 1. Purpose and product definition

PUI89 AI HOME is a compact, low-profile, four-wheel indoor assistant intended to improve residents' awareness of selected home conditions. It may observe owner-authorised spaces, detect specifically defined events using available sensors, and deliver clear, timestamped prompts for a person to review.

It is an additional awareness and assistance layer. It is not a certified life-safety device, a replacement for smoke/fire/carbon-monoxide/gas alarms, a medical device, a security guarantee, or an autonomous caregiver.

**Design principle:** calm, premium, approachable and serviceable. The product should look like a carefully engineered home appliance, not a toy, surveillance prop or miniature industrial rover.

## 2. Intended users and operating context

Primary user groups:
- Residents and families who want additional awareness of selected home conditions.
- Older adults and people who may benefit from reminders or human-reviewed alerts, without claiming medical monitoring.
- Family members or designated caregivers who receive authorised notifications.
- Building or property operators, where deployment is explicitly authorised.

Initial operating environment:
- Indoor, dry, ordinary residential floors.
- Supervised deployment in a mapped or explicitly bounded area.
- Smooth hard floors and low-pile floor coverings only after traction and obstacle tests.
- Human access to charging, cleaning, inspection and emergency power isolation.

Out of initial scope:
- Outdoor use, stairs, lifts, public roads, wet rooms, swimming pools and unqualified thresholds.
- Carrying people, pets, children, hot liquids, hazardous materials or heavy payloads.
- Physical intervention, restraint, lifting, medical diagnosis or emergency-response guarantees.
- Autonomous opening of doors, operating appliances, manipulating mains electricity or controlling certified safety systems.
- Unattended operation until a defined risk assessment and validation programme support it.

## 3. Product-level design targets

These values are inherited design targets, not measurements from a physical prototype.

| Attribute | Target / status |
|---|---|
| Mobility | Four-wheel, low-speed indoor mobile base |
| Width | 25–28 cm target |
| Depth | 30–33 cm target |
| Height | 30–35 cm target |
| Complete mass | 8 kg target |
| Maximum design mass | 10 kg ceiling, including battery and installed hardware |
| Payload | TBD; do not assume remaining mass is usable payload |
| Runtime | TBD after power budget and duty-cycle definition |
| Speed / stopping distance | TBD after hazard analysis and braking tests |
| Slope / threshold capability | TBD; no capability claim before tests |
| Operating temperature / humidity | TBD from component ratings and intended environment |
| Ingress protection | TBD; no IP rating claim |
| Acoustic level | TBD; measure in a defined room and operating mode |
| Connectivity | Local-first design preferred; network dependency and fallback must be specified |
| Service life / repair interval | TBD from component selection and reliability evidence |

Any change to envelope or mass requires a documented trade-off review. The 10 kg ceiling is a system-level limit, not a target for the chassis alone.

## 4. User needs and measurable outcomes

| ID | User need | Proposed acceptance evidence |
|---|---|---|
| UN-01 | Understand what the robot is doing | Usability review of clear status, mode and alert explanations |
| UN-02 | Know when an event was observed | Event record includes timestamp, source, confidence/quality and data age |
| UN-03 | Control where sensing is permitted | Permission and privacy settings can be inspected and tested |
| UN-04 | Avoid unexpected movement | Visible operating state, user stop control and measured stop behaviour |
| UN-05 | Recover from faults safely | Defined fault states, safe hold/stop behaviour and recovery instructions |
| UN-06 | Maintain the product | Accessible service points, replaceable wear parts and documented inspection |
| UN-07 | Avoid false assurance | Alerts state uncertainty and remind the user to verify critical conditions |

Numerical performance thresholds must be set after the use cases, sensor choices and risk analysis are reviewed. Do not invent detection accuracy, notification latency, battery life or reliability figures.

## 5. Physical architecture proposal

### 5.1 Form and packaging

- Low-profile, rounded-rectangle main body with a stable, compact footprint.
- Four-wheel arrangement with protected wheel openings and replaceable tyres.
- Upper sensor mast or sensor window only if required by field of view; keep it short, robust and serviceable.
- Distinct front/rear orientation with restrained status lighting and clear physical controls.
- Separate structural chassis, electronics carrier, battery enclosure and cosmetic covers.
- Removable service cover with captive or standard fasteners; no hidden destructive clips as the only access method.
- Cable routing protected from wheels, moving joints, sharp edges, heat and user-accessible pinch points.
- Centre of mass, wheelbase, track width, ground clearance and tipping margin remain TBD pending CAD and stability analysis.

### 5.2 Candidate subsystem blocks

| Subsystem | Candidate approach | Status |
|---|---|---|
| Chassis | Serviceable metal or engineered-polymer frame; material TBD | Proposed |
| Drive | Four-wheel drive or two driven wheels plus passive support; compare torque, complexity and control | Open design decision |
| Motors | Low-voltage geared DC/BLDC candidates only after load and thermal calculations | Not selected |
| Motor control | Current-limited driver with independent hardware disable | Required concept; not selected |
| Battery | Protected, replaceable battery pack with qualified BMS and fuse | Required; chemistry/capacity TBD |
| Compute | Low-power edge computer for perception and event logic | Candidate; not selected |
| Safety controller | Independent MCU or hardware path for stop, watchdog and fault handling | Required concept; architecture TBD |
| Sensors | RGB/depth camera and selected environmental sensors only where use case justifies them | Optional; not selected |
| IMU / vibration | Chassis-mounted accelerometer/IMU for motion and vibration context, if validated use case exists | Proposed; not installed |
| Connectivity | Wi-Fi/Bluetooth only as required; local status and safe fallback must remain defined | TBD |
| Charging | Protected charging interface or dock; electrical and thermal safety review required | TBD |

No component model, vendor, country of origin, price or availability is approved by this specification.

## 6. Hardware, embedded software and AI responsibilities

### Hardware
Physical sensors, camera, wheels, motors, motor drivers, battery/BMS, fuses, switches, enclosure, mechanical brakes or passive stopping provisions, charging connector and wiring.

### Embedded and deterministic software
Sensor acquisition, timestamps, unit conversion, motor control limits, watchdog, battery monitoring, communications health, fault handling, emergency stop path, safe-state transitions and data-quality checks.

### AI / analytics
Only where supported by an approved use case and suitable data:
- Object or motion detection within authorised areas.
- Event classification and context-aware anomaly suggestions.
- Sensor fusion with provenance and uncertainty.
- Human-readable alert summaries.

AI must not directly bypass motor limits, emergency stop, watchdogs or hardware interlocks. AI output is advisory. Critical events require human verification and, where appropriate, a separately certified alarm system.

## 7. Home sensing, privacy and data governance

- Use sensing only in areas and for purposes explicitly authorised by the resident.
- Provide a clear indication when camera or microphone sensing is active.
- Microphone/audio-event classification is optional and disabled unless explicitly justified and consented to.
- Prefer on-device processing and data minimisation; define retention, deletion, export and access controls before implementation.
- Do not record continuously by default. Event capture, if any, requires a documented purpose, consent model and retention policy.
- Do not infer health status, identity, emotion or sensitive personal attributes.
- Provide a physical or software privacy mode with a clear, testable state.
- Protect credentials and telemetry; never publish secrets, private footage, network details or precise household location in public project materials.

## 8. Mobility and functional safety

- Human stop control must be accessible and independent of AI inference.
- Define a low-speed operating envelope only after mass, wheel geometry, motor characteristics and stopping tests are known.
- Detect stale, disconnected, saturated or implausible sensor data; never silently replace missing data with synthetic values.
- On controller fault, watchdog timeout, unsafe battery condition or loss of critical feedback, transition to a defined safe state.
- Prevent unintended restart after emergency stop or critical fault; require deliberate reset.
- Evaluate pinch, entrapment, collision, tipping, cable snag, thermal, electrical, charging and battery hazards.
- Do not operate on stairs or near unprotected drop-offs without a validated physical prevention system.
- No autonomous manipulation or safety-critical intervention is included in v1.0.

## 9. Product Console requirements

The console must distinguish physical measurements from computed and AI-derived outputs.

Required status groups:
1. **Hardware:** sensor installed/verified, not installed, fault/unavailable.
2. **Embedded:** acquisition and deterministic checks implemented/tested or unavailable.
3. **AI/Analytics:** validated for stated scope, experimental, not implemented or insufficient data.
4. **Telemetry:** live, stale, disconnected or demo/simulated (explicitly labelled).
5. **Evidence:** calibration, test ID, timestamp, software/model version and operating mode.

For every measurement show source, unit, timestamp, data age and quality. Show confidence/uncertainty only when the algorithm defines it. Missing data must be displayed as missing—not zero, normal or healthy. Demo values must never be mixed with live telemetry.

## 10. Preliminary verification plan

| Gate | Verification activity | Exit evidence |
|---|---|---|
| G0 | Confirm users, intended use, exclusions and operating environment | Reviewed mission and use-case list |
| G1 | Requirements and hazard analysis | Traceable requirements, hazards and acceptance criteria |
| G2 | Packaging and mass budget | CAD envelope, subsystem layout, mass estimate with source/confidence |
| G3 | Mechanical/electrical architecture review | Interface drawings, power budget, wiring and service access review |
| G4 | Component and supplier qualification | Datasheets, origin, lifecycle, cost evidence and compatibility review |
| G5 | Bench verification | Documented sensor, power, thermal, communications and safety-path tests |
| G6 | Controlled mobility validation | Measured speed, stopping, stability, obstacle and fault response within defined envelope |
| G7 | Supervised home-environment evaluation | Approved test protocol, consent, logs, failure analysis and user feedback |
| G8 | Release readiness review | All critical requirements closed or explicitly accepted; safety and evidence review signed off |

Passing a gate requires recorded evidence. A document, render, simulation or code test cannot substitute for physical verification where physical behaviour is being claimed.

## 11. Open engineering decisions

The following must remain open until supported by analysis or evidence:
- Drive topology, wheel diameter, wheelbase, track width and ground clearance.
- Motor torque/speed, gear ratio, driver rating and braking approach.
- Battery chemistry, capacity, protection, charging method and runtime.
- Compute board, safety controller, sensor models and country of origin.
- Camera field of view, depth method, microphone decision and environmental sensor list.
- Payload, acoustic limit, thermal limits, ingress target and service interval.
- Connectivity, offline behaviour, notification pathway and data retention.
- Detailed manufacturing process, supplier, unit cost and repairability.

## 12. First engineering deliverables

Before purchasing hardware:
1. User journey and room-level operating scenarios.
2. Hazard analysis and safety concept.
3. Dimensioned 2D packaging drawing and preliminary 3D CAD.
4. Mass budget with estimated component masses and uncertainty.
5. Power budget and duty-cycle model.
6. Sensor placement and field-of-view study.
7. Preliminary wiring and interface diagram.
8. BOM candidates with manufacturer, exact model, datasheet, country of origin, lifecycle, price source and date.
9. Verification matrix linked to requirements.
10. Independent design review of the 8 kg target and 10 kg maximum.

**Current evidence statement:** This document defines proposed requirements and engineering work. No physical AI HOME robot, selected hardware stack, live sensor integration, measured performance, prototype test, home deployment, validation or certification is claimed.

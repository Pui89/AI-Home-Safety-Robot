# PUI89 AI HOME — Power, Battery & Five-Sense Sensor Engineering Baseline

**Document status:** Proposed engineering requirements and verification plan only.  
**Product:** PUI89 AI HOME — compact, four-wheel indoor assistant concept.  
**Scope:** Battery and power architecture plus the approved six-group Five-Sense Multimodal Sensor Intelligence registry.  
**Evidence boundary:** No battery, sensor, semiconductor, compute board or charging component is selected, purchased, integrated or validated by this document. No runtime, detection accuracy, safety certification or physical prototype is claimed.

## 1. Current product design constraints

- Complete robot mass: **8 kg target; 10 kg maximum design ceiling**, including battery, BMS, compute, sensors, wiring, enclosure, wheels and all installed hardware. These are design targets, not measured results.
- Indoor four-wheel assistant; payload and mobility limits remain subject to mechanical validation.
- Software-first, local-first operation. No mandatory cloud, hosted inference, paid API, subscription or metered service.
- No downloads, installations, supplier contact, purchases or account creation are authorised by this document.
- Evaluate non-Chinese-origin suppliers, manufacturers, components, technology, software and infrastructure only; verify origin and ownership from traceable evidence. Reject unclear or unsupported provenance.
- No autonomous operation of locks, breakers, valves, appliances, certified alarms or emergency systems.
- Certified smoke, fire, carbon-monoxide, gas and electrical protection remains independent and primary.

## 2. Power-system objectives

1. Measure and budget energy by subsystem rather than estimating runtime from battery capacity alone.
2. Separate always-on safety supervision from duty-cycled perception, mobility and optional user-interface loads.
3. Use event-triggered sensor activation where it does not compromise required coverage or response time.
4. Prefer efficient local CPU/NPU inference; scale model size, frame rate, resolution and inference frequency to measured hardware capability.
5. Make power state, battery health, temperature, charging state and degraded capabilities visible on the on-device interface.
6. Preserve evidence and event history across controlled shutdown where technically feasible; never silently discard important records.
7. Enter a defined safe hold on uncertain battery state, undervoltage, overtemperature, BMS fault or power-controller fault.
8. Keep certified life-safety devices operational independently of AI HOME.

## 3. Power architecture

**Proposed logical path:**

Battery cells → protected battery pack/BMS → main disconnect and appropriately rated protection → power distribution → regulated rails → compute, MCU, sensors, display/audio and drive electronics.

The final topology, rail voltages, currents, fuse values, connectors, isolation and grounding are **TBD** until exact candidate datasheets and electrical calculations are reviewed.

### 3.1 Required power domains

| Domain | Loads | Design policy |
|---|---|---|
| Essential supervision | MCU, battery monitor, critical fault/status indication | Lowest practical continuous load; independent of high-level AI availability |
| Compute | CPU/GPU/NPU, RAM and storage | Dynamic performance states; bounded peak power; graceful workload shedding |
| Vision and depth | RGB/RGB-D camera, optional depth/LiDAR electronics | Configurable duty cycle and event-triggered capture, subject to coverage validation and physical privacy controls |
| Audio | Microphone/audio front end and speaker | Independent hardware mute; wake/processing only when owner-authorised |
| Environmental sensors | Chemical, thermal and environmental sensor modules | Continuous only where hazard response requires it; otherwise justified sampling schedule |
| Mobility | Motor drivers, motors and encoders | Disabled while stationary; controlled acceleration and current limits; no AI-direct actuator command |
| User interface | Display, indicators and audio output | Adaptive brightness and sleep; critical alerts remain legible and audible as configured |
| Charging | Charger, dock interface and battery monitoring | Charging interlocks, temperature supervision and verified compatibility |

### 3.2 Operating power states

| State | Intended behaviour | Exit / safety rule |
|---|---|---|
| OFF / isolated | Main system loads disconnected; safe service state | Manual, documented restart procedure |
| STANDBY | Essential supervisor and required low-power monitoring only | Wake on approved event or user action |
| MONITOR | Scheduled sensor sampling and lightweight local processing | Escalate only on validated event conditions |
| INVESTIGATE | Temporarily increase relevant sensing/compute duty cycle | Time-bounded; return to MONITOR or report uncertainty |
| MOBILITY | Supervised movement with independent obstacle and stop safeguards | Stop/hold on fault, uncertainty or unsafe battery state |
| LOW-BATTERY | Shed optional workloads and stop initiating nonessential tasks | Preserve essential reporting; request safe docking/charging |
| FAULT / SAFE-HOLD | Disable nonessential loads and inhibit movement | Human inspection and explicit recovery |
| CHARGING | Verified dock/charger state and monitored battery charging | Stop charging on BMS, temperature, voltage or alignment fault |

State transitions must be deterministic, logged and testable. An AI model may recommend a mode but must not bypass deterministic power and safety gates.

## 4. Battery sizing and runtime calculation

Do not publish an operating-hours claim until a representative physical configuration has been measured.

For a first-order estimate:

- Average load power: P_avg = Σ(P_i × D_i), where P_i is measured subsystem power and D_i is its measured duty fraction.
- Nominal energy: E_nominal (Wh) = nominal pack voltage (V) × rated capacity (Ah).
- Usable energy must account for permitted depth of discharge, conversion losses, temperature, ageing, BMS reserve and manufacturer limits.
- Estimated runtime: t (h) = usable energy (Wh) ÷ measured average system power (W).

The estimate is not a validated runtime. Measure idle, monitor, investigate, mobility, display/audio, network-loss and charging/fault scenarios. Record test configuration, battery age/state, ambient temperature, instrument accuracy and raw observations.

### 4.1 Battery and charging safeguards

- Verify cell manufacturer, exact model, chemistry, lot/traceability and country of manufacture.
- Require manufacturer datasheets and applicable transport/safety documentation.
- Select a pack and BMS as a compatible system; verify cell balancing, over/under-voltage, overcurrent, short-circuit and temperature protections as applicable to the chosen chemistry.
- Verify continuous and peak discharge current against measured compute and motor loads, including startup/stall transients.
- Verify charger chemistry/profile, voltage/current limits, connector polarity, temperature sensing and charge termination.
- Provide physical containment, strain relief, protected wiring and service isolation appropriate to the final design.
- Do not charge an unknown, damaged, swollen, wet, overheated or faulted pack.
- Do not conduct improvised cell, short-circuit, puncture, thermal-abuse or mains-electrical experiments.
- Charging must not depend on a cloud connection. Dock identity/alignment and electrical compatibility must be checked before enabling charge.
- Battery temperature or BMS uncertainty must cause charging to be inhibited and a clear fault to be displayed.

## 5. Semiconductor and chip-level inventory

Track semiconductor devices separately from complete modules so that actual silicon origin and supply-chain evidence are visible. No chip is selected by appearing in this inventory.

| Chip class | Function | Evidence required |
|---|---|---|
| AI SoC / CPU / GPU / NPU | Local perception and inference | Exact silicon and board model, manufacturer, fabrication/manufacturing origin evidence, datasheet, power and thermal data |
| MCU | Deterministic supervision, sensor polling and fault handling | Exact model, safety-relevant limitations, datasheet, clock/power and lifecycle |
| DRAM / SRAM | Runtime memory and buffering | Exact part, capacity, manufacturer and origin evidence |
| Flash / storage controller | Firmware, application and event storage | Exact part, endurance, retention, security and origin evidence |
| PMIC / DC-DC / voltage regulators | Rail conversion and sequencing | Exact IC, voltage/current/thermal ratings and protection features |
| Battery monitor / protector / BMS controller | Cell measurement and pack protection | Exact IC and BMS architecture, supported chemistry and safety documentation |
| Charger IC | Controlled battery charging | Exact IC, charge profile, thermal and fault protections |
| Motor-driver ICs | Controlled motor power stage | Exact model, current/thermal limits, fault response and protection |
| Sensor ICs | Image, depth, inertial, chemical, thermal and environmental measurement | Exact sensor IC/module, range, accuracy, calibration and origin |
| Connectivity ICs | Local wired/wireless communication | Exact model, supported security, radio approvals and origin evidence |

For every candidate record: manufacturer, exact part number/revision, assembly and silicon origin separately where known, official evidence URL, date checked, licence/firmware provenance, lifecycle, power, thermal, cost evidence and status (**VERIFIED / UNVERIFIED / RESEARCH ONLY / REJECTED**). Unknown origin remains unknown; do not infer it from a distributor's location.

## 6. Five-Sense Multimodal Sensor Intelligence

The approved registry contains six engineering groups. The six groups are a system taxonomy, not a claim that every sensor is installed or available. Exact sensors, ranges, placements, thresholds and sampling rates remain TBD until a specific use case and component are reviewed.

Every registered sensor must define: sensor ID/type; intended purpose; installation position and coverage; measurement range and units; accuracy/response/drift where specified; known limitations and blind spots; power/interface; calibration and health method; timestamp/freshness; confidence and uncertainty; alert priority; failure behaviour; privacy classification; provenance and validation evidence.

### 6.1 Shared sensor observation contract

Each observation should include:
- sensor_id, sensor_group, channel, value and unit;
- observed_at, received_at, zone and source_type (synthetic or physical);
- status (healthy, degraded, disconnected, stale, invalid, calibration_due, unknown);
- quality_flags, calibration_ref, health_ref and provenance;
- confidence only when a calibrated and documented method exists; otherwise null;
- uncertainty and limitations; never invent a probability;
- privacy_state, owner permission and retention class where personal data may be involved.

Missing, stale, invalid, conflicting or uncalibrated data must never be silently converted into a normal/safe value. Preserve source timestamps and receipt timestamps separately.

### 6.2 Six-group sensor registry

| Group | Intended purpose / candidate channels | Proposed placement | Key limitations and validation |
|---|---|---|---|
| **1. Vision** | RGB imaging, depth/RGB-D, optical flow and visual context for permitted obstacle, object and scene observations | Front-facing protected sensor window; exact height/angle after CAD and coverage study | Lighting, occlusion, reflections, motion blur, privacy and lens obstruction; physical manual lens cover and independent hardware camera inhibit required; no facial recognition by default |
| **2. Audio** | Sound-event awareness such as configured alarm-like sounds, glass-break-like sounds or calls for help | Microphone aperture with acoustic isolation from motors/speakers | Room acoustics, distance, noise, reverberation, language and false positives; separate physical microphone mute; camera shutter does not mute audio |
| **3. Chemical** | Selected gas/VOC/air-quality channels only when a specific sensor is justified | Ventilated location away from heat, exhaust, motor airflow and direct contamination | Cross-sensitivity, warm-up, drift, humidity, poisoning, calibration and sensor lifetime; never identify a gas or concentration without a suitable calibrated sensor |
| **4. Thermal** | Ambient temperature, humidity-associated thermal context and non-contact thermal observations where justified | Ambient sensor away from compute/battery heat; thermal imager only after use-case review | Emissivity, reflected heat, distance, field of view, self-heating and calibration; thermal imagery is not medical or fire certification |
| **5. Tactile & Vibration** | Bump/contact switches, force/contact sensing, IMU vibration and chassis vibration | Protected bumper perimeter, chassis structure and isolated IMU mount | Robot self-vibration, floor resonance, mounting, impact direction and mechanical wear; distinguish robot-generated vibration from environmental evidence |
| **6. Environmental & Safety** | Temperature, relative humidity, water/moisture/leak, ambient light, pressure or other justified environmental channels; isolated status interface to certified alarms only if legally and technically permitted | Distributed at appropriate enclosure/room-facing locations; leak sensors near floor-level risk areas; no assumption that robot placement gives whole-room coverage | Placement and coverage dominate performance; sensor readings do not prove absence of hazards; certified alarms remain independent and primary |

### 6.3 Sensor health, calibration and confidence

- Define startup self-check, periodic health check and fault-latching behaviour per exact component.
- Record calibration date, method, reference instrument, operator/process, result and next due date.
- Detect disconnected, stale, stuck, drifting, implausible, saturated and mutually inconsistent channels.
- A sensor's self-reported healthy flag is not proof of measurement accuracy.
- Confidence must be traceable to validation data and conditions. Where calibration/validation is absent, report **confidence unknown**.
- Alert severity must consider hazard type, proximity, context, persistence and evidence quality—not event count alone.
- A single high-severity observation may warrant a high-priority human alert; many low-risk observations must not automatically outrank it.
- Contradictory modalities remain visible as disagreement; do not average away a potentially important hazard.

### 6.4 Alert priority and human response

| Priority | Meaning | Required response |
|---|---|---|
| P0 — Critical | Credible indication of immediate serious danger or critical system fault | Immediate prominent local warning and configured human escalation; do not delay certified alarm or emergency procedures |
| P1 — High | Significant abnormal condition requiring prompt inspection | Prompt notification with source, timestamp, uncertainty and recommended human check |
| P2 — Advisory | Non-urgent anomaly or maintenance/calibration issue | Show in dashboard and event history; request review |
| P3 — Informational | Normal status, low-risk change or routine reminder | Log or display without alarm escalation |

Priority is policy-driven and requires hazard-specific validation. Quantity alone never determines severity. AI HOME must not diagnose, declare a home safe, or replace a certified alarm or professional inspection.

### 6.5 Cross-modal fusion

1. Validate each modality independently before fusion.
2. Align observations using source timestamps, receipt timestamps and explicit clock-skew limits.
3. Preserve original observations and provenance; derived events reference all supporting and conflicting evidence.
4. Apply context-aware rules with documented freshness, confidence and severity requirements.
5. If modalities conflict, a required sensor is unhealthy, or evidence is insufficient, produce UNKNOWN / SENSOR_FAULT / SYSTEM_UNAVAILABLE as appropriate.
6. Never let a high model score override a failed sensor, privacy control, safety gate or human authority.
7. The fusion layer may create a reviewable Observation, update a proposed WorldState and produce a FailureReport; it cannot directly issue physical actions.

## 7. Privacy and data minimisation

- Local processing and storage by default; no default external upload, remote access or third-party sharing.
- Camera and microphone permissions are independent and physically observable.
- The camera has a manually operated opaque sliding lens cover, visible mechanical OPEN/CLOSED indicator, tactile end positions and independent hardware capture inhibit. The cover is never motorised or remotely/voice/AI controlled.
- Default to no persistent indoor image/video recording. Visual analysis, if explicitly enabled, should be transient and local where feasible.
- Do not store raw audio by default. Any permitted audio processing requires explicit owner control and documented retention.
- Sensor registry and logs must not expose private floor plans, credentials, resident routines or precise personal location in public records.
- Core controls and safety alerts must remain understandable offline; language support begins with Thai and English, with an expandable localisation design.

## 8. Verification plan — software first, then controlled bench tests

### Software-only tests (synthetic data; no hardware required)
- Contract validation: missing fields, wrong units, NaN/infinite values, future timestamps and malformed provenance.
- Freshness and health: stale, disconnected, invalid, stuck, drifting and calibration-due states.
- Fusion: corroborating, conflicting, missing and delayed observations across all six groups.
- Severity: one high-hazard observation versus many low-risk observations.
- Privacy: camera disabled, shutter unknown, microphone muted, no network and no persistence by default.
- Power-state logic: low battery, BMS fault, overtemperature, sensor loss, compute overload, safe hold and recovery.
- Deterministic replay: identical inputs produce identical policy decisions and traceable outputs.

### Bench tests (only after separately approved exact components)
- Measure rail voltage/current, idle and peak power, transient response and thermal rise.
- Validate BMS and charger documentation and safe operating envelope; use supervised, approved test procedures.
- Measure subsystem duty cycles and representative energy consumption.
- Validate sensor range, response, repeatability, drift, calibration and failure detection against suitable references.
- Verify physical camera cover, hardware inhibit, independent microphone mute and power-loss behaviour.
- Record raw data, test setup, instrument calibration, software revision, pass/fail criteria and reviewer.

No hazardous gas, open flame, mains wiring, battery abuse or uncontrolled environmental testing is permitted as an informal bench experiment.

## 9. Release gates

| Gate | Required evidence | Current status |
|---|---|---|
| G0 — Requirements | Approved use cases, hazards, privacy and sensor registry | This document proposes the baseline; review pending |
| G1 — Software contracts | Versioned schemas, validators, synthetic fault tests and traceable outputs | Not verified by this document |
| G2 — Component research | Exact non-Chinese-origin candidate models, official datasheets, provenance, licence and power data | Not selected |
| G3 — Bench integration | Approved parts, wiring/rail design, calibration, measured power and controlled tests | Not started |
| G4 — Integrated prototype | Physical mass, thermal, battery, sensor, privacy and mobility evidence | Not established |
| G5 — Product validation | Repeatable representative-home testing, independent safety review and documented limitations | Not established |

## 10. Change control and unresolved conflicts

This document is a new proposed baseline. The repository's existing hardware/product documents contain older **5 kg preferred / 6 kg maximum** mass wording, while the current product direction is **8 kg target / 10 kg maximum**. These records must be reconciled in a separately reviewed documentation change before the mass target is treated as consistent across the repository. Do not silently treat the older values as current.

All TBD values remain TBD until backed by official documentation, engineering calculations or measured test evidence. Requirements are not implementation; a document or synthetic test does not prove physical performance.

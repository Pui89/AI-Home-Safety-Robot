# PUI89 AI Home Assistant Robot — Safety and Cybersecurity Requirements

**Status:** Proposed engineering requirements. These are not proof that controls exist, and this document is not a safety certification or penetration-test report.

## 1. Non-negotiable boundaries

1. Certified smoke, fire, carbon-monoxide, electrical and other required safety devices remain independent and primary.
2. AI HOME must not delay evacuation, emergency calls or established safety procedures.
3. AI HOME must not operate locks, breakers, mains wiring, gas valves, cooking appliances, certified alarms or emergency systems.
4. No direct model-to-actuator control path is permitted.
5. Unknown, stale, contradictory or low-quality evidence must never be converted into a confident safe state.
6. Physical movement is out of scope until a separate hazard review, supervised test procedure and independent emergency stop are in place.
7. A software privacy toggle is not a substitute for a physical camera barrier and hardware capture inhibit.

## 2. Safety requirements

| ID | Requirement | Verification evidence | Status |
|---|---|---|---|
| HOME-SAF-001 | Certified life-safety equipment remains independent of AI HOME. | Architecture and integration inspection. | NOT VERIFIED |
| HOME-SAF-002 | Emergency instructions are never gated by AI inference. | UI/API review and scenario tests. | NOT VERIFIED |
| HOME-SAF-003 | Uncertain, stale, missing or conflicting evidence causes HOLD/UNKNOWN, not SAFE. | Fault-injection tests. | NOT VERIFIED |
| HOME-SAF-004 | Future mobile prototype includes a physical, independently acting emergency stop before any movement test. | Hardware inspection and supervised stop test. | NOT IMPLEMENTED |
| HOME-SAF-005 | Future mobility has obstacle/drop-off protection and a defined safe-stop state. | Controlled simulation and bench/physical test protocol. | NOT IMPLEMENTED |
| HOME-SAF-006 | Battery, charging and power design has independent protection appropriate to selected components. | Datasheets, electrical review and controlled tests. | NOT VERIFIED |
| HOME-SAF-007 | Water, heat and fire exposure limits are defined before selecting enclosure/materials. | Hazard analysis and component/material evidence. | NOT VERIFIED |
| HOME-SAF-008 | Reports clearly distinguish observation, inference, prediction and recommendation. | Output contract and user-interface tests. | NOT VERIFIED |
| HOME-SAF-009 | Camera privacy uses a hand-operated opaque sliding lens cover with no powered actuator, plus an independent hardware capture/power inhibit mechanically linked to the closed position; only direct local manual action may open the cover. Shutter-state uncertainty or fault fails closed and is never reported as physically covered. | Physical inspection, manual-cycle/wear tests, electrical measurement, fault injection and attempted powered/remote override tests. | NOT IMPLEMENTED |

## 3. Cybersecurity requirements

| ID | Requirement | Verification evidence | Status |
|---|---|---|---|
| HOME-CYB-001 | No credentials, tokens, private resident data or raw sensor recordings are committed to Git. | Automated repository checks and review. | NOT VERIFIED |
| HOME-CYB-002 | All external inputs are treated as untrusted and validated before parsing or use. | Unit tests, fuzz/boundary tests where practical. | NOT VERIFIED |
| HOME-CYB-003 | Dependencies, GitHub Actions, models and datasets have exact versions, provenance and licence records. | Software/model bill of materials and review. | NOT VERIFIED |
| HOME-CYB-004 | GitHub workflows use least-privilege permissions and do not expose secrets to untrusted pull-request code. | Workflow configuration review. | NOT VERIFIED |
| HOME-CYB-005 | Local data access is restricted by defined roles; encryption and key management are specified before resident data is stored. | Threat review and security tests. | NOT VERIFIED |
| HOME-CYB-006 | Updates are authenticated, integrity-checked and recoverable. | Update design review and rollback test. | NOT IMPLEMENTED |
| HOME-CYB-007 | Security events and failed access attempts are logged without collecting unnecessary sensitive content. | Log inspection and privacy review. | NOT VERIFIED |
| HOME-CYB-008 | Offline mode does not silently disable essential safety boundaries. | Network-loss tests. | NOT VERIFIED |
| HOME-CYB-009 | Remote, voice, agent or model requests cannot move/open/close the manual camera shutter or bypass its hardware capture inhibit; no powered shutter actuator is permitted. | Threat review, interface tests and attempted powered/remote-actuation tests. | NOT VERIFIED |
| HOME-CYB-010 | Routine indoor camera frames are not persisted to caches, logs, crash reports, telemetry or backups in privacy-first mode; microphone state is controlled independently. | Data-flow inspection and negative persistence/audio-state tests. | NOT VERIFIED |

## 4. Threat coverage

Use the existing [Security Threat Model](SECURITY_THREAT_MODEL.md) as the threat catalogue. At minimum, verify controls for spoofed/stale sensors, prompt injection, malicious media, model hallucination, dependency compromise, leaked credentials, denial of service, network loss, unauthorised movement and privacy exposure.

For camera privacy, additionally assess shutter jamming or removal, false position signals, hardware capture-enable failure, alternate optical sensors, remote activation attempts, unintended image persistence and misleading UI state.

## 5. Required pre-deployment reviews

Before any resident-data capture or real sensor installation: approve the data-flow and privacy review, retention/deletion policy, sensor inventory, exact software/model/dependency versions, threat review, recovery plan and human-oversight procedure.

Before any physical camera integration: approve the optical coverage design, mechanical wear/jam analysis, hardware camera-power inhibit, state-sensor design, microphone separation, image data-flow map and fault-injection test plan. Do not collect resident imagery until the privacy review is approved.

Before any physical movement: separately approve the mechanical hazard analysis, emergency stop, stability, braking/stopping behaviour, obstacle/drop-off detection, battery and charging safety, test enclosure and supervised test plan.

Before any sale or public safety claim: obtain applicable independent testing, certification and regulatory/legal review. Do not imply these have been obtained.

## 6. Review record

For each requirement, record reviewer, date, revision, evidence link, result, limitations and corrective action. Keep **NOT VERIFIED** until evidence has been reviewed. Documentation alone does not pass a requirement.

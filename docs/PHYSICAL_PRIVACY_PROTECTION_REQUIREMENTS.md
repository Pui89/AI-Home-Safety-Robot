# PUI89 AI HOME — Physical Privacy Protection Requirements v1.0

**Status:** Proposed engineering requirements; not implemented, integrated or physically validated.  
**Scope:** Indoor camera privacy controls for PUI89 AI HOME.  
**Design principle:** **Understand, Don't Record.** The owner must be able to verify camera privacy from the physical device, not merely trust an application status.

## 1. Product intent

AI HOME should support useful home-awareness functions while minimising collection of private household imagery. The default operating profile is text-first and privacy-first: process only the minimum visual input needed for an explicitly enabled task, keep frames transient in memory, and do not persist routine indoor images or video.

A software label, app toggle or status LED alone is not proof that the optical path is physically blocked. The product must provide a visible, mechanical barrier over every camera aperture and an independent means to disable camera capture.

## 2. Required user controls

**Selected control concept: manual-only sliding lens cover.** The owner or an authorised person must physically slide the opaque cover at the robot body to open or close the lens. The shutter is not motorised and has no software-, app-, network-, voice-, agent- or model-controlled opening mechanism. This is a design requirement, not a claim that hardware already exists.

| ID | Requirement | Acceptance evidence | Status |
|---|---|---|---|
| HOME-PRIV-001 | Provide a manually operable, opaque physical shutter that fully covers the camera lens aperture. | Physical inspection from front and oblique angles; no usable optical path while closed. | PROPOSED |
| HOME-PRIV-002 | The shutter control must be accessible on the robot body and operable without an app, network or voice assistant. | Hands-on usability test with the robot powered on and off. | PROPOSED |
| HOME-PRIV-003 | The shutter must have an unmistakable physical indication, mechanically linked to its position (for example, a visible CLOSED/OPEN marker). | Inspection confirms the marker cannot show CLOSED when the cover is not fully closed. | PROPOSED |
| HOME-PRIV-004 | A hardware camera-power inhibit must disable the camera module when Privacy Mode is engaged; software must not be able to override the physical inhibit. | Schematic review, power-rail measurement and negative override test. | PROPOSED |
| HOME-PRIV-005 | A position sensor must report shutter state to the software as OPEN, CLOSED or UNKNOWN. | Switch/sensor fault-injection tests. | PROPOSED |
| HOME-PRIV-006 | If shutter position evidence is missing, contradictory or faulty, report UNKNOWN and keep camera capture disabled. | Disconnect, stuck-switch and contradictory-state tests. | PROPOSED |
| HOME-PRIV-007 | No remote command, agent, model or network request may open the physical shutter. Opening requires deliberate local physical action by the owner or authorised person. | Interface/API threat review and remote-command rejection test. | PROPOSED |
| HOME-PRIV-008 | The enclosure must cover all optical camera apertures; no secondary or auxiliary camera may remain active in Privacy Mode. | Hardware inventory and physical inspection. | PROPOSED |
| HOME-PRIV-009 | Camera privacy state must be visible both on-device and in the local interface, with wording that distinguishes physical confirmation from software request. | UI/state tests for OPEN, CLOSED and UNKNOWN. | PROPOSED |
| HOME-PRIV-010 | Camera shutter state must not be represented as microphone mute. Microphone capture requires its own independent physical control and status. | Hardware/UI inspection and audio-input tests. | PROPOSED |\n| HOME-PRIV-011 | The shutter must be opened and closed only by direct manual operation of the physical slider at the robot; no motor, servo, solenoid or other powered actuator may move the cover. | Physical design inspection and attempted software/remote-actuation tests. | PROPOSED |\n| HOME-PRIV-012 | The slider must provide distinct tactile end positions/detents and a high-contrast position marker mechanically linked to the opaque cover; the marker must not be independently software-controlled. | Mechanical inspection and repeated-cycle usability/wear tests. | PROPOSED |

## 3. Recommended mechanical and electrical design

The selected first-prototype concept is a **manual sliding opaque lens cover**. The owner moves the cover directly with a finger at the robot body; use tactile OPEN/CLOSED end positions or detents and a high-contrast marker mechanically coupled to the cover. **Do not use a motor, servo, solenoid, powered latch or any other actuator to move the shutter.** No application, voice assistant, network service, AI agent or model may open or close it. Materials, dimensions, travel, force, wear life, cleanability, pinch-point risk and child-safety considerations remain to be selected and tested.

The camera power path should include a hardware inhibit mechanically linked to the manual shutter position. When the opaque cover reaches its fully closed position, the physical mechanism must disable the camera module's power or capture-enable path independently of the application. The hardware design must prevent software from re-enabling capture while the shutter is closed. Opening the shutter by hand is necessary but not sufficient to start capture: a separate explicit software permission is still required. The shutter itself must never move in response to software or electrical commands.

A shutter-position sensor may provide software status, but it is not a substitute for the visible mechanical marker or optical inspection. A sensor disagreement, broken wire, boot-time uncertainty or failed self-test must produce **UNKNOWN / CAMERA DISABLED**, never a false CLOSED confirmation.

The shutter must block the full lens aperture and any relevant field-of-view path. It must not rely on a translucent cover, software blur, image masking or a screen overlay.

## 4. Operating states

| State | Physical condition | Camera power/capture | User-facing status |
|---|---|---|---|
| PRIVACY_CLOSED | Opaque shutter fully closed and mechanically indicated | Hardware-inhibited | **CAMERA PHYSICALLY COVERED** only when position evidence is valid |
| CAMERA_ENABLED | Shutter deliberately opened locally | May be enabled subject to separate software permission | **CAMERA OPEN — CAPTURE PERMISSION REQUIRED** |
| UNKNOWN / FAULT | Position uncertain, sensor fault, wiring fault or state mismatch | Disabled (fail-closed) | **CAMERA STATE UNKNOWN — CAMERA DISABLED** |
| STARTUP | State not yet verified | Disabled | **VERIFYING PRIVACY SHUTTER** |

The product must never infer that the camera is physically covered solely because an app toggle is off, a process is stopped, or an LED is dark.

## 5. Privacy-first image handling

- Default to no persistent indoor image or video recording.
- For an owner-enabled visual task, process frames locally and transiently in volatile memory where feasible; discard frames after inference unless the owner has explicitly enabled a narrowly scoped evidence workflow.
- Do not write routine frames to disk, thumbnails, debug logs, crash dumps, telemetry, cloud storage or backups.
- Do not upload indoor camera frames by default. Any future external transfer requires a separate, explicit, informed opt-in and a documented data-flow review.
- Prefer text event summaries containing the minimum necessary details; avoid unnecessary names, identity inference, detailed resident routines or sensitive room descriptions.
- Text event history is also personal data: provide owner-controlled access, retention and deletion.
- If an evidence capture option is later implemented, make it opt-in, time-bounded, visible to the owner and separately configurable from routine AI analysis. No silent or indefinite retention.

## 6. Microphone and other sensors

The camera shutter does not mute microphones. If AI HOME includes a microphone, provide a separate physical microphone mute control with a clear mechanical or electrical state indication. Privacy Mode should disable both camera and microphone by default unless the owner deliberately configures a separate, clearly explained exception. Non-imaging sensors must be documented individually because motion, presence, depth and environmental sensors can still reveal household activity.

## 7. Threat and failure cases

The design review and tests must cover at least:

- App says CLOSED while the shutter is physically open.
- Shutter jammed, partially closed, detached or worn.
- Position sensor stuck, disconnected, shorted or contradictory.
- Camera power switch or capture-enable line stuck on.
- Reboot, brownout, battery removal and power restoration.
- Malicious or compromised software attempts to activate the camera.
- Remote/network/voice command attempts to open or close the shutter.\n- Any proposed motor, servo, solenoid or powered actuator attempts to move the shutter.\n- Repeated manual operation causes wear, loose travel, marker misalignment or incomplete aperture coverage.
- Secondary camera, depth camera or auxiliary optical sensor remains active.
- Frames accidentally written to cache, logs, temporary files, crash reports or backups.
- Microphone remains active while the UI incorrectly implies all sensors are private.

**Required failure response:** keep camera capture disabled where the hardware allows; show UNKNOWN/FAULT rather than CLOSED; provide a clear local alert; preserve manual control; do not silently resume capture after reboot.

## 8. Verification and release gates

1. **Requirements review:** approved mechanical, electrical, privacy and threat requirements; confirm manual-only operation and prohibit powered shutter actuation.
2. **Bench prototype:** inspect full aperture coverage, tactile operation, marker linkage, camera power isolation and sensor state.
3. **Fault injection:** test partial closure, jam, sensor disconnection, stuck states, power loss and hostile software requests.
4. **Data-flow verification:** inspect memory, filesystem, caches, logs, crash handling, telemetry and backups to verify no routine image persistence.
5. **Usability review:** residents can identify camera state at a glance and operate the control without an app.
6. **Controlled home pilot:** only after safety, privacy and security reviews; obtain informed consent from affected household members and visitors as appropriate.
7. **Release claim review:** do not claim tamper-proof, guaranteed privacy, certified safety or verified deletion until the corresponding independent tests support the exact claim.

## 9. Current maturity and non-claims

This document defines proposed requirements only. The selected concept is a manually operated sliding opaque lens cover with no powered shutter actuator. No physical shutter, camera power interlock, shutter sensor, microphone mute switch or privacy-state UI is established as built or tested. No selected component, CAD design, schematic, prototype, supplier or purchase is approved by this document.

A physical shutter reduces the risk of visual capture through the covered aperture; it does not by itself protect stored data, other sensors, network interfaces, microphones, or against every possible tampering method. The design must be reviewed as a complete system.

## 10. Related requirements

- [Product requirements](PRODUCT_REQUIREMENTS.md)
- [Safety and cybersecurity requirements](SAFETY_AND_CYBERSECURITY_REQUIREMENTS.md)
- [System architecture](SYSTEM_ARCHITECTURE.md)
- [Verification and validation plan](VERIFICATION_AND_VALIDATION_PLAN.md)

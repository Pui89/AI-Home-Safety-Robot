# PUI89 AI HOME — 360° Intelligence Profile v1.0

**Status:** Proposed product-specific requirements; no physical robot, camera ring or integrated 360° sensor suite is established.

## Mission
Provide privacy-aware indoor situational awareness around the AI HOME platform and within explicitly authorised rooms. Coverage is defined per room and robot pose, not as a blanket claim that the entire home is visible.

## Candidate workflow
1. Define rooms, permitted observation zones, privacy exclusions and alertable events.
2. Evaluate camera placement and field-of-view against walls, furniture, doorways, low/high objects and robot self-occlusion.
3. Keep camera, depth and environmental-sensor observations time-stamped and individually traceable.
4. Detect/track selected people, pets or objects only for explicitly configured use cases.
5. Combine event cues conservatively; stale, conflicting or unavailable sensors produce UNKNOWN/REVIEW rather than an all-clear.

## Candidate AI and sensing
RGB/depth perception, object detection, segmentation, tracking, optional sound-event classification and approved environmental-sensor fusion. SLAM/room mapping is a candidate only if mobile navigation requires it and a validation protocol is defined. Smoke, fire, CO, gas and electrical hazards require suitable certified independent detectors.

## 360° requirements
- Specify horizontal and vertical coverage, room-level blind zones and privacy masks.
- Include manual physical camera covers for any future physical camera hardware.
- Do not record or transmit private areas, faces, audio or occupancy data without explicit permission and a defined retention policy.
- Do not treat a panoramic view as proof of depth or hazard detection.
- Communicate sensor-health and coverage loss clearly; never display "home fully protected" from incomplete sensing.

## Safety and exclusions
AI HOME is an additional awareness and notification layer, not a replacement for certified smoke, fire, carbon-monoxide, gas, electrical or water-protection devices. Human verification is required for consequential alerts. No emergency response or protection performance is claimed.

## Evidence gates
Privacy/use-case approval → room coverage map → synthetic and rights-cleared test cases → sensor calibration/bench test → event-level false-alarm/miss evaluation → supervised home trial with consent and incident controls.

Measure coverage by room/height/zone, event recall and false alerts, occlusion, latency, sensor failure detection, privacy-mask effectiveness and notification delivery only after implementation.

**Shared architecture:** [PUI89 360° Intelligence Architecture v1.0](https://github.com/Pui89/PUI89-Shared-AI-Core/blob/main/docs/PUI89_360_DEGREE_INTELLIGENCE_V1.0.md)

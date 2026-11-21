# Offline Independence Implementation & Verification Plan — PUI89 AI HOME

**Status:** Engineering specification and verification plan only. Hardware implementation, testing and validation are not claimed.

This plan is normative for product design reviews and must be reconciled with the product hazard analysis, applicable vehicle/robot standards and the exact hardware/software revision.

## Objective
Indoor four-wheel assistant concept. Local user controls and safety sensing must remain available without the app. On loss of remote connectivity, stop or safely hold mobility as determined by occupancy, obstacle and stability state; maintain essential local alerts where hardware supports them.

## Minimum offline capability
Local interaction, local sensing/alerts and local stop when implemented; no remote movement into occupied or unknown spaces; no autonomous resumption after reconnection; physical stop overrides all software.

## Required deliverables
1. Product control inventory and local indication map.
2. Offline capability matrix identifying each function, its sensor/compute/power dependencies and whether it is local, optional-connected or unavailable.
3. Connectivity fault-response table covering phone absence, app failure, local radio loss, Wi-Fi loss, internet/cloud outage, stale data, authentication expiry and reconnection.
4. Product-specific hazard analysis for loss of communication, power, sensing, compute and local storage.
5. Printed manual and Quick Start & Safety Guide proof for each launch language and revision.
6. Local log format, retention policy, storage-full response and offline export/recovery procedure.
7. Verification report for the applicable OFF-01 through OFF-15 tests in the product manual appendix.
8. Defect register and release approval record.

## Mandatory engineering rules
- Core local operation and safety do not depend on phone, app, Wi-Fi, internet or cloud.
- Local physical stop and required safety interlocks override all remote commands.
- No stale, duplicated, expired or replayed command may cause action.
- Reconnection never resumes hazardous activity automatically.
- Restart begins in a defined safe state.
- Missing sensors, models or compute capacity produce explicit unavailable/uncertain status.
- Printed manuals contain all essential instructions; QR is supplementary.
- Customer recovery steps never bypass guards, interlocks or emergency stop.
- Vehicle steering, throttle, braking and propulsion remain under the validated vehicle control architecture; PUI89 remote app cannot actuate them.

## Verification record template
| Field | Required record |
|---|---|
| Test ID | OFF-01 … OFF-15 |
| Product/build | Hardware revision, firmware/software commit and configuration |
| Preconditions | Setup, fixture, battery/power state, safety observer |
| Procedure | Reproducible numbered steps |
| Expected result | Product-specific acceptance criteria |
| Actual result | Observed behaviour and measurements |
| Evidence | Log, photo/video, trace or report reference |
| Result | Pass / Fail / Blocked / Not applicable with rationale |
| Ownership | Tester, reviewer, date, defect ID and corrective action |

## Product-specific safe-state design
Do not choose a generic “power off” response. Derive the safe state from the product hazard analysis. For mobile robots, consider controlled stop/hold, obstacle/terrain state, braking/actuator behaviour and local operator takeover. For road vehicles, loss of PUI89 connectivity must not interfere with rider/driver control or OEM safety functions. For the current Coconut software-first milestone, preserve local image review and manual assessment; do not imply a harvesting machine exists.

## Release gate
This plan is complete as documentation only when reviewed and approved by the responsible engineering and safety reviewers. Product offline-readiness remains **Not yet demonstrated** until applicable tests pass on the actual product build with retained evidence.


## Detailed implementation and release checklist

- Produce offline capability matrix with hardware/sensor/model/compute/storage/power dependencies.
- Define physical controls, local indicators, stop/E-stop and reset; independent from phone/app/network/cloud.
- Define fault responses for phone/app, radio, Wi-Fi, internet/cloud, authentication, stale data, sensors/models and power loss.
- Partition safety logic from remote services; reject expired/duplicate/replayed/out-of-order commands; reconnect only after fresh sync and deliberate local authorisation.
- Define bounded local logs, integrity, retention, storage-full/corrupt handling and offline export.
- Supply complete printed User Manual and Quick Start & Safety Guide; QR supplementary; test manual-only use.
- Run OFF-01–OFF-15 on exact build; record setup, procedure, expected/actual, evidence, tester/date, defects and disposition. N/A requires approved safety rationale.
- No offline-ready claim until applicable tests pass and safety/engineering reviewers approve.

### Product-specific scope
- **PUI89 AI HOME:** Indoor four-wheel assistant concept. Local controls, safety sensing and stop must work without app/cloud. Remote loss during movement requires an occupancy-, obstacle- and stability-aware safe response; no unattended movement into unknown/occupied areas.
- **PUI89 AI NOMAD:** Outdoor/mobile assistant concept. Local operator control and stop must work without app/cloud. Link loss during movement requires hazard-analysis-defined controlled stop/hold, fresh local authorisation and no automatic resume.

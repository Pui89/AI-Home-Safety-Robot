# PUI89 AI HOME — Compact Layout and Complete-Mass Budget

**Status:** Preliminary design study only. No components are selected, purchased, assembled, weighed or validated.  
**Founder-approved complete robot mass target:** **8 kg**, including battery and all installed parts.  
**Maximum complete robot mass:** **10 kg**. This is a hard ceiling, not a target to exceed.  
**Payload:** TBD; it must be defined separately through structural, stability, traction, braking and runtime analysis. Do not assume a payload capacity.  
**Use:** Indoor residential concept; supervised movement only if a mobility prototype is later developed.

> **Supersession record:** This 8 kg target / 10 kg maximum replaces the former 5 kg preferred / 6 kg ceiling and the earlier assumed 1 kg / 2 kg payload cases. Those earlier figures are withdrawn and must not be used for current BOM or design decisions.

## 1. Design rules

1. Design toward a preferred complete robot mass of **8 kg**; the complete assembled robot must never exceed **10 kg**.
2. Complete robot mass includes chassis, enclosure, wheels, motors, battery/BMS, computer, sensors, wiring, connectors, fasteners, guards and all installed accessories.
3. Payload is separate from complete robot mass and must be included in stability, wheel-load, torque, braking and runtime calculations. Payload capacity remains TBD until separately analysed and tested.
4. Do not assume a 1 kg initial payload or 2 kg stretch payload. Establish any payload limit from the selected mechanical architecture, then verify it through controlled testing while keeping total robot mass within the 10 kg ceiling.
5. Do not invent subsystem mass allocations before candidate components and mechanical architecture are selected. Record each candidate's datasheet mass and later measure the physical part.
6. Keep heavy components low and near the centreline. Avoid top-heavy sensor towers and unnecessary displays, duplicate controllers, oversized motors or decorative structure.
7. Certified household smoke/fire/CO/electrical protection remains primary. AI HOME must not control locks, breakers, valves, appliances or certified alarms.

## 2. Preliminary packaging envelope

| Parameter | Proposed range | CAD envelope for initial fit check |
|---|---:|---:|
| Width | 250–280 mm | 280 mm maximum |
| Length / depth | 300–330 mm | 330 mm maximum |
| Height | 300–350 mm | 350 mm maximum |

The envelope includes wheels, fixed sensor housing, guards and permanent external features. Internal zones are not frozen until a CAD layout and exact component dimensions are available.

**Packaging priorities**
- Base: protected wheel/drive arrangement, low centre of gravity and safe floor clearance.
- Lower central zone: battery enclosure, BMS and power protection.
- Middle zone: compute/control electronics and serviceable wiring.
- Upper zone: only the sensors and indicators required for the first product task.
- Reserve ventilation, cable bend radius, connector access, wheel sweep and maintenance clearance.

A candidate two-powered-wheel plus two-support-wheel layout may be evaluated, but no drive arrangement is selected. Motor count and wheel geometry remain TBD pending torque, stability, floor-transition and stopping calculations.

## 3. Component-level mass ledger — required before design freeze

No unsupported per-subsystem allocations are assigned at this stage. Populate this table from official manufacturer datasheets, supplier documentation and physical weighing.

| Subsystem / item | Manufacturer and exact model | Quantity | Datasheet mass (g) | Measured mass (g) | Mounts / wiring allowance (g) | Evidence / status |
|---|---|---:|---:|---:|---:|---|
| Chassis and frame | TBD | TBD | TBD | TBD | TBD | Pending |
| Enclosure and access panels | TBD | TBD | TBD | TBD | TBD | Pending |
| Wheels, motors and drive | TBD | TBD | TBD | TBD | TBD | Pending |
| Battery, BMS and containment | TBD | TBD | TBD | TBD | TBD | Pending |
| Compute and control electronics | TBD | TBD | TBD | TBD | TBD | Pending |
| Sensors and mounts | TBD | TBD | TBD | TBD | TBD | Pending |
| Power conversion, fuses and protection | TBD | TBD | TBD | TBD | TBD | Pending |
| Wiring, connectors and strain relief | TBD | TBD | TBD | TBD | TBD | Pending |
| Guards, fasteners and service parts | TBD | TBD | TBD | TBD | TBD | Pending |
| **Complete robot mass** |  |  | **TBD** | **TBD** | **TBD** | **8 kg target; 10 kg maximum** |

Do not declare the target achieved from estimates alone. Report the measured assembled mass, scale resolution, configuration, battery state and included accessories.

## 4. Preliminary BOM categories

| BOM group | Required evidence before selection |
|---|---|
| Chassis/frame and enclosure | CAD, material datasheets, strength/stability review, mass and manufacturing method |
| Wheels and drive units | Official datasheets, torque/speed/braking calculations, guarded moving parts and mass |
| Battery pack and BMS | Cell provenance, official datasheets, protection design, charging and thermal review, complete mass |
| Compute/control unit | Exact model, supported software, measured power/RAM/storage, licence and mass |
| Environmental sensors | Measurement range, accuracy, drift, calibration and placement data |
| Power conversion and protection | Voltage/current budget, fuse/protection calculations and component ratings |
| Wiring/connectors | Current rating, insulation, strain relief, temperature and service ratings |
| Fasteners, seals and guards | Material/grade, retention, serviceability, inspection and mass |

No purchases, supplier contact, account creation, trials, package installations or paid services are authorised. Research must use official, freely accessible manufacturer documentation where available; country of origin, licence, ongoing cost and safety approvals require separate review.

## 5. Engineering gates before design freeze

- [ ] CAD proves the complete external envelope is within 280 × 330 × 350 mm.
- [ ] Component-level mass ledger supports an **8 kg target** and proves the complete robot remains at or below **10 kg**.
- [ ] Physical weighing confirms the assembled mass; estimates are not reported as measurements.
- [ ] Centre-of-gravity and tip-resistance analysis covers turns, slopes and emergency stops.
- [ ] Drive torque, speed, wheel loading, stopping distance and floor-transition limits are calculated.
- [ ] Payload capacity remains TBD until separately analysed and validated; no assumed payload is added to the 10 kg complete-robot ceiling.
- [ ] Battery energy, peak/continuous current, BMS, charging and thermal limits are documented.
- [ ] Electrical protection, fuse sizing, connector ratings and wiring diagram are reviewed.
- [ ] Sensor placement, coverage, blind spots, calibration and environmental limits are documented.
- [ ] Thermal dissipation, ventilation, ingress paths and maintenance access are assessed.
- [ ] Privacy/data-flow review is complete before camera/audio capture.
- [ ] Bench and supervised validation plans define pass/fail criteria and safe abort conditions.

## 6. Explicit limitations

This document does not establish that the proposed compact envelope, 8 kg target or 10 kg maximum is mechanically feasible. It does not establish a prototype, selected components, real sensor integration, runtime, navigation performance, waterproofing, fire resistance, IP rating, certified alarm function or safety certification. Payload capacity remains TBD. Stair climbing and outdoor terrain operation are out of scope. Unknown values remain TBD.

## 7. Review record

Record revisions, reviewers, exact changed values, supporting datasheets/calculations, physical weighing records and unresolved risks. Never convert a planning target or supplier-listed mass into a measured result without weighing the actual installed part.

## ข้อกำหนดภาษาไทย

น้ำหนักรวมของหุ่นยนต์ PUI89 AI HOME ที่ผู้ก่อตั้งยืนยันคือ **เป้าหมาย 8 กิโลกรัม และสูงสุด 10 กิโลกรัม** โดยต้องรวมแชสซี ตัวถัง ล้อ มอเตอร์ แบตเตอรี่/BMS คอมพิวเตอร์ เซนเซอร์ สายไฟ ขั้วต่อ อุปกรณ์ป้องกัน และอุปกรณ์ติดตั้งทั้งหมด

ข้อกำหนดใหม่นี้ใช้แทนตัวเลขเดิมที่เคยกำหนดเป้าหมาย 5 กิโลกรัมและสูงสุด 6 กิโลกรัม รวมถึงสมมติฐาน payload 1–2 กิโลกรัมเดิม โดยให้ยกเลิกการใช้ตัวเลขเดิมในการออกแบบและจัดทำ BOM ปัจจุบัน ความสามารถในการรับน้ำหนักบรรทุกยังไม่กำหนด ต้องวิเคราะห์และทดสอบแยกต่างหาก และห้ามทำให้น้ำหนักรวมของหุ่นยนต์เกิน 10 กิโลกรัม

ตัวเลข 8 และ 10 กิโลกรัมเป็นข้อกำหนดการออกแบบ ไม่ใช่น้ำหนักต้นแบบที่วัดได้ ยังไม่มีการยืนยันว่าตัวถัง อุปกรณ์ หรือระบบขับเคลื่อนสามารถทำได้จริง ต้องจัดทำ BOM ที่มีแหล่งข้อมูล ตรวจสอบมวลของชิ้นส่วน และชั่งน้ำหนักหุ่นยนต์ที่ประกอบเสร็จจริงก่อนกล่าวอ้างว่าผ่านข้อกำหนด

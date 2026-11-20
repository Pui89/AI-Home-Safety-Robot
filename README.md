# PUI89 AI HOME — Indoor Home Assistant Robot

**A compact four-wheel indoor assistant for household awareness and human-reviewed alerts.**

[English project page](https://pui89.github.io/home.html) · [ภาษาไทย](https://pui89.github.io/home-th.html) · [PUI89 portfolio](https://pui89.github.io/)

![PUI89 AI HOME compact indoor assistant robot concept](docs/images/ai-home-compact-four-wheel.svg)

*Concept illustration only. It is not evidence of a built or validated robot.*

## What this product is

PUI89 AI HOME is an **indoor home-assistance robot** intended to help residents notice selected changes in home conditions and receive understandable prompts for human review. Its mission is home awareness and everyday support—not industrial inspection, outdoor mobility or security enforcement.

**ผู้ใช้งาน:** ผู้อยู่อาศัย ครอบครัว ผู้ดูแล และผู้จัดการอาคาร  
**ประโยชน์หลัก:** ช่วยสังเกตสภาพแวดล้อมภายในบ้านและแจ้งเหตุที่กำหนดไว้ เพื่อให้ผู้ใช้งานตรวจสอบและดำเนินการ

## Product-specific functions

- Four-wheel, compact indoor form for home environments.
- Observe authorised indoor scenes and selected, appropriately instrumented environmental conditions.
- Combine supported sensor observations with time and room context to identify events that may need attention.
- Present understandable status and human-reviewed alerts; preserve event context for later review.
- Respect resident privacy and the limits of each installed and calibrated sensor.

## Physical design constraints

- Complete robot mass target: **8 kg**.
- Maximum complete robot mass: **10 kg**, including battery and all installed hardware.
- These are design limits, not measured prototype results.

## What is not established

- No physical robot or integrated live sensor suite is established.
- No validated home-hazard detection accuracy, continuous monitoring reliability or emergency-response guarantee is claimed.
- AI HOME does **not** replace certified smoke, fire, carbon-monoxide, gas, electrical or water-protection devices. Those remain independent and primary.
- AI observations are advisory and require human interpretation for consequential decisions.

## Current development status

**Implemented — early software foundations.** This does not mean a complete robot or validated home-safety system exists.

**Next evidence gate:** define a narrow household use case, hazard-specific sensor requirements, privacy boundaries and measurable acceptance criteria; then test the software and selected sensors separately under controlled conditions.

## Product documentation

- [Product requirements](docs/PRODUCT_REQUIREMENTS.md)
- [MVP product specification](docs/MVP_PRODUCT_SPECIFICATION.md)
- [Internal layout and mass budget](docs/AI_HOME_INTERNAL_LAYOUT_AND_MASS_BUDGET.md)
- [Sensor integration specification](docs/SENSOR_INTEGRATION_SPECIFICATION.md)
- [Test and validation plan](docs/TEST_AND_VALIDATION_PLAN.md)

## Shared PUI89 engineering

Cross-product architecture, evidence contracts, safety, privacy, security, recovery, device interaction and localization requirements are maintained in the [PUI89 Shared AI Core](https://github.com/Pui89/PUI89-Shared-AI-Core). This README focuses on HOME's indoor mission and mass constraints rather than repeating shared standards.

Current maturity labels follow the [PUI89 Portfolio Alignment Register](https://github.com/Pui89/Pui89.github.io/blob/main/docs/PUI89_PORTFOLIO_ALIGNMENT_REGISTER_2026-11-18.md) and [Evidence-Based Development Maturity Standard](https://github.com/Pui89/Pui89.github.io/blob/main/docs/PUI89_DEVELOPMENT_STAGE_STANDARD.md).

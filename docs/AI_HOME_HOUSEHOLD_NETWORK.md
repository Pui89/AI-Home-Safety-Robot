# PUI89 AI HOME Household Network

## AI HOME Household Network — multi-floor product standard

**Status: PROPOSED PRODUCT STANDARD / NOT IMPLEMENTED OR VALIDATED.**

- **One floor = one AI HOME robot + one dedicated charging dock.**
- **Three floors = three AI HOME robots + three dedicated charging docks.**
- Each robot is assigned to its designated floor/zone. The units coordinate as one logical **AI HOME Household Network**.

Each unit performs its own authorised local sensing, event assessment, on-device status, alerts and event history. The proposed Household Network coordinates device identity, floor assignment, battery/dock/health status, timestamped event summaries, severity, evidence references, uncertainty, acknowledgement, cross-floor event correlation and household-level status.

**Local operation and privacy**
- Essential local functions, alerts, status and recovery must not require a smartphone, app, cloud account or internet.
- Exchange minimum necessary event metadata by default. Raw audio/video is not shared between robots by default; any sharing requires explicit owner authorisation and privacy controls.
- If the network is unavailable, each unit continues only supported local functions and marks household-wide coordination unavailable. Offline floors must never appear monitored or safe.
- Robots are not assumed to climb stairs, use lifts or transfer between floors. Each unit remains assigned to its floor unless a separately designed and validated transfer method is introduced.
- Each unit has one dedicated charging dock. Dock compatibility, alignment, battery protection, electrical safety, clearance and recovery require separate verification.
- AI HOME is an additional awareness layer, not a replacement for certified smoke, fire, carbon-monoxide, gas or electrical protection. Consequential alerts require human verification.

**Package planning**

| Household configuration | AI HOME robots | Charging docks |
|---|---:|---:|
| One floor | 1 | 1 |
| Two floors | 2 | 2 |
| Three floors | 3 | 3 |
| N floors | N | N |

This is a quantity-planning rule, not a final retail price, installation quote, SKU or coverage guarantee. Final packages must account for floor layout, sensing needs, network coverage, dock placement, installation and support.

**Verification gates**

Before claiming a working network, verify device registration and floor assignment; local-network discovery and authentication; clock consistency; event delivery and acknowledgement; duplicate handling; stale/offline status; network partition and recovery; privacy boundaries; alert history; and safe charging/docking. Test one-, two- and three-unit configurations with repeatable synthetic tests, then controlled bench and supervised household trials.

**No multi-robot coordination, cross-floor coverage, charging reliability or household safety performance is claimed as implemented or tested by this specification.**

## มาตรฐาน AI HOME Household Network — ระบบบ้านหลายชั้น

**สถานะ: ข้อกำหนดผลิตภัณฑ์ที่เสนอ / ยังไม่ได้ติดตั้งหรือทดสอบยืนยัน**

- **1 ชั้น = AI HOME 1 ตัว + แท่นชาร์จเฉพาะ 1 จุด**
- **บ้าน 3 ชั้น = AI HOME 3 ตัว + แท่นชาร์จเฉพาะ 3 จุด**
- หุ่นยนต์แต่ละตัวรับผิดชอบชั้นและพื้นที่ที่กำหนด และประสานงานเป็นระบบเดียวชื่อ **AI HOME Household Network**

AI HOME แต่ละตัวทำหน้าที่รับข้อมูลจากเซนเซอร์ที่เจ้าของอนุญาต วิเคราะห์เหตุการณ์ แสดงสถานะ แจ้งเตือน และเก็บประวัติภายในเครื่อง ส่วนเครือข่ายส่วนกลางมีแนวทางประสานรหัสอุปกรณ์ ชั้นที่รับผิดชอบ สถานะแบตเตอรี่/แท่นชาร์จ/สุขภาพอุปกรณ์ สรุปเหตุการณ์พร้อมเวลา ระดับความรุนแรง หลักฐาน ความไม่แน่นอน การรับทราบ การเชื่อมโยงเหตุการณ์ข้ามชั้น และสถานะภาพรวมของบ้าน

**การทำงานภายในเครื่องและความเป็นส่วนตัว**
- การทำงานพื้นฐาน คำเตือน สถานะ และการกู้คืนต้องไม่บังคับใช้โทรศัพท์ แอป บัญชีคลาวด์ หรืออินเทอร์เน็ต
- ค่าเริ่มต้นให้แลกเปลี่ยนเฉพาะข้อมูลสรุปเหตุการณ์ที่จำเป็น ไม่ส่งภาพหรือเสียงดิบระหว่างหุ่นยนต์โดยอัตโนมัติ การแบ่งปันสื่อต้องได้รับอนุญาตจากเจ้าของและมีการควบคุมความเป็นส่วนตัว
- เมื่อเครือข่ายขัดข้อง แต่ละตัวทำงานได้เฉพาะความสามารถภายในเครื่องที่รองรับ และต้องแจ้งว่าการประสานงานทั้งบ้านไม่พร้อมใช้งาน ห้ามแสดงชั้นที่ออฟไลน์ว่าได้รับการดูแลหรือปลอดภัย
- ไม่ถือว่าหุ่นยนต์ขึ้นลงบันได ใช้ลิฟต์ หรือย้ายชั้นได้ หุ่นยนต์แต่ละตัวประจำชั้นที่กำหนด เว้นแต่จะออกแบบและทดสอบวิธีเคลื่อนย้ายแยกต่างหาก
- หุ่นยนต์แต่ละตัวมีแท่นชาร์จเฉพาะหนึ่งจุด ต้องตรวจสอบความเข้ากันได้ การจัดตำแหน่ง ระบบป้องกันแบตเตอรี่ ความปลอดภัยทางไฟฟ้า พื้นที่ว่าง และการกู้คืน
- AI HOME เป็นระบบช่วยสังเกตและแจ้งเตือนเพิ่มเติม ไม่ทดแทนอุปกรณ์ตรวจจับควัน ไฟไหม้ คาร์บอนมอนอกไซด์ ก๊าซ หรือระบบป้องกันไฟฟ้าที่ได้รับการรับรอง การแจ้งเตือนสำคัญต้องให้มนุษย์ตรวจสอบ

**แนวทางวางแผนแพ็กเกจ**

| รูปแบบบ้าน | จำนวน AI HOME | จำนวนแท่นชาร์จ |
|---|---:|---:|
| 1 ชั้น | 1 ตัว | 1 จุด |
| 2 ชั้น | 2 ตัว | 2 จุด |
| 3 ชั้น | 3 ตัว | 3 จุด |
| N ชั้น | N ตัว | N จุด |

เป็นหลักเกณฑ์วางแผนจำนวน ไม่ใช่ราคาจำหน่าย ใบเสนอราคาติดตั้ง SKU ขั้นสุดท้าย หรือคำรับประกันพื้นที่ครอบคลุม ต้องพิจารณาผังบ้าน ความต้องการเซนเซอร์ สัญญาณเครือข่าย ตำแหน่งแท่นชาร์จ การติดตั้ง และบริการหลังการขายก่อนกำหนดแพ็กเกจจริง

**ประตูการทดสอบก่อนกล่าวอ้างความสามารถ**

ต้องทดสอบการลงทะเบียนอุปกรณ์และกำหนดชั้น การค้นหาและยืนยันตัวตนในเครือข่าย เวลาให้ตรงกัน การส่งและรับทราบเหตุการณ์ การจัดการเหตุการณ์ซ้ำ สถานะออฟไลน์/ข้อมูลล้าสมัย การแยกเครือข่ายและการกลับมาเชื่อมต่อ ขอบเขตความเป็นส่วนตัว ประวัติการแจ้งเตือน และความปลอดภัยของการชาร์จ/แท่นจอด เริ่มจากการทดสอบจำลองแบบทำซ้ำได้สำหรับ 1, 2 และ 3 ตัว ก่อนทดสอบบนโต๊ะและในบ้านภายใต้การดูแล

**ข้อกำหนดนี้ยังไม่ใช่หลักฐานว่ามีการประสานงานหลายหุ่นยนต์ การครอบคลุมหลายชั้น ความน่าเชื่อถือของการชาร์จ หรือประสิทธิภาพความปลอดภัยภายในบ้านที่สร้างและทดสอบแล้ว**

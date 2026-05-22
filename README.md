# EEE4775 HW1
**Name**: Andrew VanAuken  
  
## Part A – Classify
### 1. Cardiac pacemaker pacing pulse generation
**Classification:** Hard

Cardiac pacemaker pacing pulse generation is a hard real-time system because the pacing pulse has to occur within a safe timing interval when the heart does not produce a natural beat. If this is missed, it could endanger or kill the patient.

### 2. Netflix video player buffering decision
**Classification:** Soft

Netflix video buffering is a soft real-time system because late buffering decisions can reduce video quality or cause pauses. Timing mishaps affect the experience but do not create any safety hazard.

### 3. Anti-lock braking system actuator command
**Classification:** Hard

An anti-lock braking system is a hard real-time system because adjusting brake pressure must happen quickly during events. If this is missed, it could cause wheel lockup, loss of steering control, or a crash.

### 4. Bank ATM cash dispenser receipt printer
**Classification:** None

A bank ATM receipt printer doesn’t have a significant real-time function because delayed receipt printing causes inconvenience. Timing failures do not affect human safety or system operation.

### 5. Falcon 9 first-stage gimbal control during landing
**Classification:** Hard 

Falcon 9 first-stage gimbal control is a hard real-time system because actuator commands need to continuously stabilize the rocket during landing. If the timing is off, it could result in instability or destruction.

### 6. Smart-fridge temperature display
**Classification:** None

A smart-fridge temperature display has no significant real-time requirement because delayed display updates mainly affect convenience. The display itself is not safety-critical and timing failures usually do not affect refrigerator operation.

### 7. Tesla Autopilot lane-keeping torque command
**Classification:** Firm

Tesla Autopilot lane-keeping torque control can be a firm real-time system because steering corrections should occur within timing limits for proper operation. If some deadlines are missed, it may reduce performance or require manual drive, but a single missed deadline does not immediately cause failure.

### 8. Spotify song crossfade
**Classification:** Soft

Spotify song crossfade is a soft real-time system because delayed audio transitions only affect listening quality and experience. Timing failures are noticeable but are not dangerous.

### 9. Disney Mickey & Minnie Runaway Railway dispatch interlock
**Classification:** Hard

The railway dispatch interlock is a hard real-time system because it must prevent unsafe train movement into occupied track sections. Missing deadlines could create a collision or guest-safety hazard.

### 10. Patient-controlled analgesia infusion pump dose limiter
**Classification:** Hard

A PCA infusion pump dose limiter is a hard real-time system because it must enforce medication lockout timing and dosage limits. If a timing deadline is missed, the patient could receive an overdose.

---

## Part B – Find the deadline

### 1. Cardiac pacemaker pacing pulse generation

**Triggering Event:**  
The pacemaker sensing circuitry detects an atrial contraction (P-wave) without a corresponding ventricular contraction (R-wave) occurring before the programmed AV delay expires.

**Deadline:**  
Within the programmed AV delay interval (typically tens to hundreds of milliseconds depending on device configuration).

**Citation:**  
[ANSI/AAMI/ISO 14708-2 – Implantable Medical Devices: Cardiac Pacemakers.](https://www.iso.org/obp/ui/#iso:std:iso:14708:-2:ed-2:v1:en)

This link defines strict timing and sensing requirements for implantable pacemakers to ensure safe pacing delivery and prevent dangerous cardiac arrhythmias such as ventricular fibrillation.

---

### 2. Anti-lock braking system actuator command

**Triggering Event:**  
A wheel-speed sensor detects rapid wheel deceleration or excessive slip relative to the vehicle’s estimated speed, indicating imminent wheel lockup.

**Deadline:**  
Approximately 10–25 ms.

**Citation:**  
https://www.bosch-mobility.com/en/solutions/driving-safety/antilock-braking-system/

Bosch ABS documentation states that ABS can modulate brake pressure up to 40 times per second, corresponding to approximately 25 ms control intervals.

---

### 3. Falcon 9 first-stage gimbal control during landing

**Triggering Event:**  
The onboard guidance system calculates updated rocket attitude and angular velocity measurements and determines the required trajectory correction.

**Deadline:**  
Approximately milliseconds in duration, requiring continuous closed-loop control updates during powered descent and landing.

**Citation:**
https://link.springer.com/article/10.1007/s12567-022-00423-6

The paper describes the guidance and control architecture required for reusable rocket landing and the need for continuous trajectory corrections throughout powered descent.

---

## Part C – Find a recent failure

### 2024 CrowdStrike Software Update Failure

The 2024 CrowdStrike software update failure was a major incident that caused global disruptions across transportation, healthcare, banking, and communication systems. A faulty CrowdStrike update caused millions of Windows systems to crash and become unavailable, resulting in widespread service outages. Airlines were forced to ground flights, hospitals lost access to critical computer systems, and financial institutions experienced service interruptions around the world. The outage demonstrated how a single software failure can quickly affect many organizations that rely on the same technology infrastructure. Recovery efforts took significant time because affected systems could not start normally and required manual intervention in many cases. From a real-time systems perspective, the failure occurred in critical low-level software that prevented systems from reaching a stable operating state. Because the failure occurred at such a fundamental level, normal services and recovery processes could not operate as intended. The incident highlights the importance of extensive testing, fault tolerance, and recovery planning for software deployed on critical systems. It also demonstrates how failures in foundational software can rapidly propagate across large, interconnected networks and impact millions of users worldwide.

### Citation

[CrowdStrike Incident Report (July 2024)](https://cloudsecurityalliance.org/blog/2025/07/03/what-we-can-learn-from-the-2024-crowdstrike-outage)

---

## Part D – Industry anchor

### ISO 26262

ISO 26262 governs safety-critical automotive real-time systems such as lane-keeping steering control. To handle ASIL D hazards, including unintended lane departure caused by missed task deadlines, the standard requires strict temporal determinism and predictable execution timing (Clause 7.4.11). It also recommends safety mechanisms such as independent hardware watchdogs to detect timing overruns or software failures (Clause 7.4.14). To prevent interference between applications, the architecture can use an MPU to isolate safety-critical steering functions from lower-priority systems like infotainment software (Annex D). In addition, if communication delays or network faults disrupt steering commands, the system must transition to a safe state within a bounded Fault Tolerant Time Interval (Clause 6.4.1). These protections reduce the residual risk of unsafe steering behavior to an acceptable level.

### Citation

[ISO 26262: Road Vehicles – Functional Safety](https://www.iso.org/obp/ui/en/#iso:std:iso:26262:-7:ed-2:v1:en)

https://blog.ansi.org/ansi/iso-26262-2018-road-vehicle-functional-safety/

https://embeddedinembedded.blogspot.com/2017/11/iso-26262-part-67-software.html

https://iccircle.com/static/upload/img20240218104904.pdf

---

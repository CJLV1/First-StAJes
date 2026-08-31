# Documents Overview

Quick summary of the three core reference documents for this project.

---

## `3500ft_rocket_project_plan.pdf`

The master plan for the whole build. Covers the project goal (reach roughly 3,500 ft on a G-class motor with no NAR/Tripoli certification required), 
the ground rules (motor class limits, 915 MHz LoRa radio, frugal DIY parts, reusable electronics), and the full 8-step build sequence — from modeling the rocket in OpenRocket, through ordering parts, 
bench-testing the flight computer/radio/launch controller individually, a full integrated dry run, physical assembly and recovery ground-testing, and finally launch day procedure and post-flight review. 
Also includes an estimated budget breakdown for the first build and for future reflights.

## `Rocket_Electronics_and_Motor_Sourcing.pdf`

A shopping reference for the electronics and motor. Lists every flight computer part (microcontroller, barometer, IMU, GPS, SD module, LoRa radios, battery/regulator) with notes and estimated cost per part. 
Flags an important GPS buying warning about COCOM altitude/velocity limits that can cause cheap GPS modules to stop reporting mid-flight. Also covers where to buy a G-class motor (Apogee Rockets, Wildman Rocketry, 
local hobby shops), with specific 29mm AeroTech/Cesaroni motor candidates to look up on ThrustCurve.org.

## `Rocket_Materials_Guide.pdf`

A dedicated guide to choosing the right material for every physical part of the rocket. An overview table covers the recommended material, the reasoning, and a realistic alternative for each component 
(nose cone, body tube, fins, centering rings, recovery gear, electronics sled, and more). Followed by longer detail sections explaining the trade-offs in plain terms for airframe materials, 
recovery system materials, and electronics/hardware.

## `Electronics_Viability_Research.pdf`

A pre-purchase due-diligence check on every part on the electronics list, based on real datasheet specs rather than general reputation. Goes component by component (Arduino Nano clone, BMP388, MPU6050, NEO-6M GPS, microSD module, RFM95W LoRa radios, LiPo + regulator) 
with a clear viability verdict for each, plus the specific risks and mitigations that matter for this build. Flags two real gotchas worth knowing before ordering: the MPU6050's accelerometer needs to be reconfigured to its ±16g setting in firmware 
(and may still clip at peak boost), and the NEO-6M GPS has a 4g acceleration operating limit that can cause a brief loss of fix during motor burn (recovering well before landing, when it actually matters).
# First-StAJes
This repository contains the precursor documentation, design documents, and source code to a model hobby rocket.

# 3,500 ft DIY High-Altitude Rocket

A beginner-built, no-certification-required model project combining a from-scration launch controller, an onboard flight computer, and live radio telemetry - designed to be resuable and afforable. 

## Inspiration

The idea to combine one person's software development expertise, with another's aerospace engineering skills, seemed like a really fun project, and boy is it. Getting to work on a model rocket
and create it from scratch for the first time is something really invigorating. **will add more detail

## Desgin Philosophy

- (No certificaton required). Staying within G-class motor limits (under FAA/NFPA Class 1 rules) keeps the project accessible to a complete beginner - no NAR/Tripoli certification process needed before flying.
- Generic, well-documented clone components (Arduino Nano clone, common breakout sensors) are chosen over name-brand commercial flight computers, keeping cost low without sacrificing capablility.
- The launch controller and the onboard electronics sled are both built to be pulled out and reused on future rockets - only the motor, igniter, and airframe are single-use per flight.
- Every structural and electronics decision flows from an OpenRocket model built first, rather then guessing dimensions and hoping the numbers work out.

---

## Top-level Schematic 

- **Launch controller** - arms and fires the motor igniter from a safe distance; fully separable from the rocket itself.
- **Flight computer** - onboard sensor suite that measures and logs the flight in real tieme.
- **Telemetry/Recovery** - a LoRa radio pair tgat streams live data to the ground and helps locate the rocket after landing (This is not required for the rocket hence the maximum altitude it will reach is 3,500ft).

---

## Code Architecture *(planned)*

No firmware has been written yet - however the intended structure is:

- **Onboard firmware** (runs on the flight computer):
  - Reads the barometer, IMU, and GPS on a fixed loop
  - Fuses barometer + IMU readings into a single, more accurate altitude/velocity estimate
  - Packages that data and transmits it over LoRa
  - Simultaneously logs everything to the SD card as a backup in case the radio link drops
- **Ground station software**: receives the incoming LoRa packets and displays altitude, velocity, and position live during the flight.

*[Ground station language/platform — e.g. another Arduino + display, or a laptop app — TBD]*

---

## Acknowledgements

TBD

---

## Project Status

Currently on **Step 1** of the build plan: modeling the airframe in OpenRocket and converging on a stable design before any parts are ordered. 
See the full 8-step build plan for what comes next (ordering, bench-testing each subsystem individually, integration, and finally launch day).

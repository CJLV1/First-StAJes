# Design Deep-Dive — 3,500 ft Rocket

This document covers the actual engineering specifics behind the airframe, recovery system, and electronics layout — dimensions, materials, and the reasoning (and a few hard-won corrections) behind each choice. Pairs with the OpenRocket model file and the materials sourcing guide.

---

## 1. Airframe Components

### Nose Cone
| Spec | Value |
|---|---|
| Shape | Ogive, 5:1 length-to-diameter ratio |
| Length | 13 inches (33.0 centimeters) |
| Base outer diameter | 2.6 inches (66 millimeters) |
| Material | Injection-molded plastic (ABS or PVC) |
| Wall thickness | Approximately 0.06–0.08 inches (1.5–2.0 millimeters), standard molded wall |
| Shoulder | 1.5 inches (38.1 millimeters) long, sized to friction-fit into the body tube |
| Finish | Shoulder lightly sanded for a controlled friction-fit slide; light paint coat for surface drag reduction |

**Why plastic, why this shape:** an ogive profile is lower-drag than a simple cone at these speeds, and plastic survives repeated hard landings — a balsa nose cone would need to be replaced or repaired after a few rough recoveries, which runs against the reusability goal for the whole airframe, not just the electronics.

### Body Tube
| Spec | Value |
|---|---|
| Length | 24 inches (61.0 centimeters), single continuous tube |
| Outer diameter | 2.6 inches (66 millimeters) |
| Inner diameter | Approximately 2.5 inches (63.5 millimeters) |
| Material | Kraft-phenolic wound paper composite |
| Wall thickness | Approximately 0.025–0.03 inches (0.6–0.8 millimeters) |
| Finish | 1–2 coats of sanding sealer or thin cyanoacrylate (CA) glue to seal against moisture before paint |

**Design note:** the original concept split this into an upper tube, a coupler, and a lower tube (for a modular build). The current OpenRocket model simplifies this to a single continuous body tube for the first draft — fewer joints, fewer failure points, and one less thing to get wrong on a first build. A coupler/two-tube split remains an option later if you want a disassemble-able airframe for transport.

### Motor Mount Tube
| Spec | Value |
|---|---|
| Length | 6 inches (15.2 centimeters) |
| Outer diameter | 29 millimeters (1.14 inches) — standard 29mm motor size |
| Inner diameter | Approximately 28.5 millimeters (1.12 inches) |
| Material | Phenolic or kraft paper motor tube |
| Wall thickness | Approximately 0.03 inches (0.8 millimeters) |
| Motor overhang | 0.5 inches (12.7 millimeters) extending past the aft end, for motor retainer clearance |
| Finish | None (structural/heat-facing part); epoxy fillets at both ends against the centering rings |

### Centering Rings
| Spec | Value |
|---|---|
| Quantity | 2 minimum (forward and aft of the motor mount) |
| Outer diameter | Matches body tube inner diameter, 2.5 inches (63.5 millimeters) |
| Inner diameter | Matches motor mount outer diameter, 29 millimeters (1.14 inches) |
| Material | Aircraft-grade birch plywood |
| Thickness | 1/8 inch (3.2 millimeters) |
| Finish | Epoxy fillet on both faces of each ring; no separate surface finish needed |

### Fins (×3)
| Spec | Value |
|---|---|
| Configuration | 3 fins, trapezoidal, through-the-wall (TTW) mounted into the motor mount |
| Root chord | 4 inches (10.2 centimeters) |
| Tip chord | 1.5 inches (3.8 centimeters) |
| Span (height) | 2.5 inches (6.4 centimeters) |
| Sweep length | 2.5 inches (6.4 centimeters), approximately 45° sweep angle |
| Material | Birch plywood (basswood as a lighter alternative) |
| Thickness | 1/8 inch (3.2 millimeters) |
| Fillet radius | Approximately 0.08 inches (2 millimeters), epoxy |
| Finish | Edges sanded to a rounded or airfoil profile; sealed with 2–3 coats of sanding sealer, then painted |

**Why TTW over surface-mount:** through-the-wall fins anchor directly into the motor mount rather than just the thin body tube wall, which meaningfully reduces the risk of a fin snapping off on a hard landing — at the cost of one extra build step (slotting the body tube).

### Bulkhead
| Spec | Value |
|---|---|
| Diameter | Matches body tube inner diameter, 2.5 inches (63.5 millimeters) |
| Material | Birch plywood |
| Thickness | 1/8 inch (3.2 millimeters) |
| Finish | Epoxied in place; small drilled hole for the shock cord attachment loop |

### Launch Lugs (×2)
| Spec | Value |
|---|---|
| Outer diameter | 1/4 inch (6.35 millimeters) |
| Length | 1 inch (25.4 millimeters) each |
| Material | Plastic or phenolic tube stock |
| Forward lug position | 1.6 inches (4.0 centimeters) from the top of the body tube |
| Aft lug position | 17.7 inches (45.0 centimeters) from the top of the body tube |
| Angular position | Both lugs aligned at the same rotational position around the tube, offset 60° from every fin |

**Why the specific placement:** with 3 fins spaced 120° apart (at 0°, 120°, 240°), a launch lug placed at 0° sits directly behind a fin — physically overlapping it. 60° is the clean midpoint between two fins, so both lugs sit clear of the fin material while still lining up with each other so a single straight launch rod can pass through both.

### External Finish (whole airframe)
| Spec | Value |
|---|---|
| Sequence | Sanding sealer → primer → enamel or acrylic paint |
| Coats | 2–3 light coats at each stage |
| Rationale | Every additional gram of paint comes directly out of the altitude budget — keep coats thin and functional rather than heavy |

---

## 2. Recovery System

### Parachute
| Spec | Value |
|---|---|
| Diameter | 20 inches (50.8 centimeters) — within the 18–24 inch (45.7–61.0 centimeter) target range |
| Material | Ripstop nylon |
| Shroud lines | 6 lines, kevlar, approximately 24 inches (61 centimeters) each |
| Deployment | At apogee |
| Target descent rate | 15–20 feet per second (4.6–6.1 meters per second) |

### Shock Cord
| Spec | Value |
|---|---|
| Length | Approximately 36 inches (91.4 centimeters), roughly 3× body tube length |
| Material | Tubular nylon or flat kevlar webbing |
| Width | 1/4–3/8 inch (6.4–9.5 millimeters) |
| Anchoring | U-bolt or epoxied loop into a bulkhead or the motor mount — not tape alone |
| Modeled mass | 20 grams (0.7 ounces) placeholder in the current simulation |

### Heat Protection
Not yet modeled as a separate component, but planned: a Nomex or fireproof cloth blanket between the ejection charge and the parachute, or cellulose wadding as a cheaper consumable alternative.

---

## 3. Electronics & Mass Budget

| Part | Est. Mass |
|---|---|
| Arduino Nano (clone) | ~5 grams |
| BMP388 barometer | ~1 gram |
| MPU6050 IMU | ~2 grams |
| NEO-6M GPS + antenna | ~12 grams |
| MicroSD module + card | ~5 grams |
| 1× RFM95W LoRa radio (only one flies) | ~3 grams |
| 1S LiPo battery (500–900 milliamp-hours) | ~15–20 grams |
| Voltage regulator | ~2 grams |
| Sled structure, wiring, connectors | ~15–20 grams |
| **Total onboard mass (placeholder used in simulation)** | **70 grams (2.5 ounces)** |

**Placement:** the electronics mass is modeled inside the body tube, positioned approximately 1.2 inches (3.0 centimeters) below the nose cone/body tube joint — forward enough to help stability, but in the cylindrical section where a real sled can physically fit. It is **not** modeled inside the nose cone itself; the tapered tip doesn't have room for a stacked sensor/radio/battery package. This was a correction made after an early design pass placed it in the nose cone by mistake.

**Sled material:** basswood, balsa, or a 3D-printed rail — light-duty is fine here since the sled sits inside the protected body tube rather than absorbing landing impact directly. It's built to slide in and out rather than being permanently mounted, per the reusability requirement.

---

## 4. Motor Selection Criteria

- **Target:** 29 millimeter motor mount, G-class total impulse (80–160 Newton-seconds by definition of the class), aiming toward the top of that range (roughly 100–160 Newton-seconds) to maximize altitude given the payload weight.
- **Note on naming:** the number after the letter in a motor name (e.g., the "74" in G74) is the average thrust in Newtons, *not* the total impulse — total impulse varies motor-to-motor within G-class regardless of that number.
- **Candidates considered:** AeroTech G64, G74, G77, G80; Cesaroni G69, G125.
- **Selection method:** rather than picking by spec sheet alone, the plan is to import 2–3 candidate thrust curves from ThrustCurve.org directly into the OpenRocket model and compare simulated apogee and stability side-by-side, since motor weight and burn profile both affect the outcome in ways that are easier to simulate than to calculate by hand.

---

## 5. Stability & Simulation Approach

- **Target stability margin:** 1–2 calibers (body-tube diameters) of separation between the center of gravity (CG) and center of pressure (CP), with CG ahead of CP.
- **Reference simulation snapshot (no motor installed):** length approximately 37 inches (94 centimeters), maximum diameter 2.6 inches (6.6 centimeters), dry mass approximately 350 grams (12.3 ounces), CG at approximately 18.5 inches (47 centimeters), CP at approximately 27.8 inches (70.6 centimeters) — a comfortable margin at this stage, before a motor's mass at the tail shifts the numbers.
- **Iteration order when off-target:** (1) try a higher-impulse motor first — cheapest change to test, (2) trim airframe length/diameter if electronics allow, (3) lighten fin material, (4) only enlarge fins for stability as a last resort, since bigger fins add drag and cost altitude.
- *** Finalized selection with the Aerotek G74-6W motor. This seems like the most viable option when considering budget and capacity.
---

## 6. Design Iteration Notes (lessons learned so far)

A running log of real issues hit while building the OpenRocket model — useful context for why certain values are what they are:

1. **Electronics mass mistakenly placed inside the nose cone** in an early draft. Corrected to sit in the body tube instead, since the nose cone's tapered geometry can't physically hold a real electronics sled.
2. **Missing launch lugs entirely** in the first draft — added afterward, since the rocket needs something to ride the launch rod on the way off the pad.
3. **Launch lug overlapping a fin** — the aft lug was initially placed at the same angular position (0°) as one of the three fins, hiding it directly behind the fin. Fixed by offsetting both lugs to 60°, clear of all fins.
4. **Launch lug positioned outside the airframe entirely** — a "distance from the bottom" position value was interpreted as extending *past* the bottom of the tube (into empty space) rather than inset *into* the tube from the bottom, inflating the rocket's total modeled length by exactly that offset. Fixed by re-anchoring the component's position from the top of the tube instead, where the offset direction is unambiguous.

---

## 7. Open Questions / Not Yet Finalized

- Final motor selection (pending side-by-side ThrustCurve simulation comparison)
- Heat protection component for the recovery bay (Nomex blanket vs. wadding)
- Whether the body tube stays a single piece or gets split into a coupler-joined two-piece design for transport
- Ground station display method for live telemetry
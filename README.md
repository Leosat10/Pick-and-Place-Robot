# Servo-Driven Pick & Place Robot — Stellar Edition

> A precision servo motor–based pick and place robot built with Arduino UNO, SG90 micro-servos, a 4×4 keypad, and a transistor driver circuit. Designed for manufacturing training, lab automation, and robotics education.

---

## Live Demo (Web Showcase)
 **[View the interactive project page → eosat10.github.io](https://leosat10.github.io)**

Explore the animated simulation of the robot's pick & place cycle — no hardware needed!

---

## 📰 Full Project Article on Hackster.io

**[Read the full build guide on Hackster.io](https://www.hackster.io/vsatish2k4/pick-and-place-robot-10d302)**

Includes circuit diagrams, component list, wiring instructions, and step-by-step build process.

---

##  What This Project Does

This robot picks up an object from **Zone A (Pickup Station)** and places it at **Zone B (Place Station)** using:

- A **servo motor arm** that rotates between pickup and place positions
- A **servo gripper** that closes to grip and opens to release
- A **4×4 keypad** for operator commands (`A` = Pick, `B` = Place, `C` = Reset)
- A **BC547 transistor driver** that cleanly switches servo power without draining the Arduino

---

## Hardware Components

| Component | Details |
|---|---|
| Arduino UNO | ATmega328P, 14 I/O pins, PWM output |
| SG90 Micro-Servo × 2 | Arm rotation + gripper actuation |
| 4×4 Matrix Keypad | User command input |
| BC547 Transistor (NPN) | Driver circuit for servo power switching |
| 5V/2A Power Supply | Regulated supply + external servo rail |
| 3D Printed Gripper | End-effector and linkage |

---

## Arduino Firmware (Quick Look)

```cpp
#include <Keypad.h>
#include <Servo.h>

Servo armServo;
Servo gripperServo;

// Key 'A' → Pick   |   Key 'B' → Place   |   Key 'C' → Reset
void loop() {
  char key = keypad.getKey();
  if (key == 'A' && !objectHeld) {
    armServo.write(35);         // move to pickup
    gripperServo.write(20);     // close gripper
    objectHeld = true;
  }
  else if (key == 'B' && objectHeld) {
    armServo.write(135);        // move to place zone
    gripperServo.write(90);     // open gripper
    objectHeld = false;
  }
}
```

Full source code is available in [`servoforge.ino`](./servoforge.ino)

---

## Performance

| Metric | Value |
|---|---|
| Cycle time | ~2.2 seconds |
| Max payload | 80g |
| Positional accuracy | ±2mm |
| Power draw (active) | 450mA |

---

## Future Upgrades

- Computer vision with OpenMV camera
- 6-DOF arm configuration
- Industrial conveyor belt sync
- Wireless keyfob control

---

## Author

**LEOSAT** — [@vsatish2k4 on Hackster.io](https://www.hackster.io/vsatish2k4)

---

## License

Open Source Hardware · MIT License · © 2025

# Circuit Schematic Diagrams

This document contains the circuit schematic diagrams for the Ultrasonic Sensor project.

## Overview Circuit Diagram

> **Note:** Add your complete circuit schematic diagram here. You can include images of the circuit layout below.

### How to Add Diagrams

1. **Image Format**: Save your schematic as PNG, JPG, or SVG and place it in a `schematics/` or `diagrams/` folder
2. **Reference in Markdown**: Use the following format:
   ```markdown
   ![Circuit Diagram](./schematics/circuit-diagram.png)
   ```

---

## Main Circuit Schematic

Add your main circuit diagram image here:

```
![Main Circuit Diagram](./schematics/main-circuit.png)
```

---

## Component Connection Diagram

### Ultrasonic Sensor (HC-SR04) Connections
```
HC-SR04 Connections:
├── VCC     → Arduino 5V
├── GND     → Arduino GND
├── TRIG    → Arduino Digital Pin 9
└── ECHO    → Arduino Digital Pin 10
```

### Servo Motor (SG90) Connections
```
Servo Motor Connections:
├── Red (VCC)    → Arduino 5V
├── Brown (GND)  → Arduino GND
└── Yellow (SIG) → Arduino Digital Pin 11
```

### LCD Screen (16x2 I2C) Connections
```
LCD I2C Module Connections:
├── VCC → Arduino 5V
├── GND → Arduino GND
├── SDA → Arduino A4 (SDA)
└── SCL → Arduino A5 (SCL)
```

### LCD Screen (16x2 Parallel) Connections (Alternative)
```
LCD Parallel Connections:
├── VSS (GND)      → Arduino GND
├── VDD (VCC)      → Arduino 5V
├── V0 (Contrast)  → GND (or Potentiometer)
├── RS              → Arduino Pin 2
├── RW              → Arduino GND
├── E               → Arduino Pin 3
├── D4              → Arduino Pin 4
├── D5              → Arduino Pin 5
├── D6              → Arduino Pin 6
├── D7              → Arduino Pin 7
├── A (LED+)        → 5V (through resistor)
└── K (LED-)        → GND
```

---

## Power Distribution

```
Power Supply Layout:
┌─────────────┐
│  Arduino    │
└─────────────┘
      │
  ┌───┴───┐
  │       │
 5V      GND
  │       │
  ├───┬───┼───┬───┐
  │   │   │   │   │
 HC  GND  Servo GND LCD
 SR  │    │    │   Components
 04  │    │    │   │
 VCC│    VCC   │   │
    │    │     │   │
    └─Distributor─┘
```

---

## Breadboard Layout Reference

Add your breadboard layout diagram or ASCII representation:

```
[Add breadboard diagram here]

Example Breadboard ASCII:
+--[+]--[+]--[+]--[+]--
|   1    2    3    4   
+--[-]--[-]--[-]--[-]--
| HC-SR04 (TRIG on Yellow wire)
+-----RED-----BROWN-----
+-----5V------GND-------
```

---

## Wiring Checklist

- [ ] Ultrasonic Sensor connected to pins 9 & 10
- [ ] Servo Motor connected to pin 11
- [ ] LCD Screen I2C connected to SDA/SCL (A4/A5)
- [ ] All GND connections made
- [ ] All 5V connections made
- [ ] No loose connections
- [ ] Power verified before upload

---

## Notes & Modifications

Use this section to document any custom modifications to the circuit:

```
Example:
- Modified sensor connection due to pin availability
- Added resistor for stability on ECHO pin
- Used separate power supply for servo motor
```

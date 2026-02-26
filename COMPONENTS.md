# Components List

This document lists all the hardware components used in the Ultrasonic Sensor project.

## Microcontroller
| Component | Quantity | Description |
|-----------|----------|-------------|
| Arduino Uno | 1 | Main microcontroller board |

## Sensors
| Component | Quantity | Model | Description |
|-----------|----------|-------|-------------|
| Ultrasonic Sensor | 1 | HC-SR04 | Measures distance using ultrasonic waves |

## Actuators
| Component | Quantity | Model | Description |
|-----------|----------|-------|-------------|
| Servo Motor | 1 | SG90 or MG996R | Controls position/rotation |

## Display
| Component | Quantity | Model | Description |
|-----------|----------|-------|-------------|
| LCD Screen | 1 | 16x2 or 20x4 | Displays sensor readings |

## Power Supply
| Component | Quantity | Voltage | Description |
|-----------|----------|---------|-------------|
| USB Cable | 1 | 5V | Powers Arduino Uno from USB |
| Battery Pack | - | - | Optional external power |

## Connectors & Wiring
| Component | Quantity | Description |
|-----------|----------|-------------|
| Jumper Wires | 15-20 | Male-to-male/female pin connections |
| Breadboard | 1 | Optional: for prototyping connections |

## Additional Components
| Component | Quantity | Description |
|-----------|----------|-------------|
| Resistors | - | For pull-up/current limiting (if needed) |
| Capacitors | - | For filtering (if needed) |

## Pin Connections Summary
- **HC-SR04 Sensor**: VCC, GND, TRIG (pin 9), ECHO (pin 10)
- **Servo Motor**: VCC, GND, Signal (pin 11)
- **LCD Screen**: SDA (A4), SCL (A5) or 16 pin interface
- **Power**: 5V from Arduino or external source

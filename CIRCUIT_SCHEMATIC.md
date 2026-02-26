# Ultrasonic Distance Sensor Project
### Arduino Uno + Ping))) Parallax Sensor + Servo Motor + LCD 16x2

This project measures distance using a Ping))) Parallax ultrasonic sensor, displays the reading on a 16x2 LCD, and moves a servo motor based on the detected distance.

---

## Circuit Diagrams

### Breadboard Layout
![Breadboard Diagram](./breadboard-diagram.png)

### Schematic Diagram
![Schematic Diagram](./schematic-diagram.png)

---

## Component List

| Component | Quantity |
|-----------|----------|
| Arduino Uno | 1 |
| Ping))) Parallax Ultrasonic Sensor | 1 |
| Servo Motor (SG90) | 1 |
| LCD 16x2 (Standard, No I2C) | 1 |
| Resistor 220Ω | 1 |
| Jumper Wires | Several |

---

## Connections

### Ping))) Parallax Sensor
```
Ping))) Sensor Connections:
├── 5V      → Arduino 5V
├── GND     → Arduino GND
└── SIG     → Arduino Digital Pin 9
```

### Servo Motor
```
Servo Motor Connections:
├── PWR (Red)    → Arduino 5V
├── GND (Black)  → Arduino GND
└── SIG (White)  → Arduino Digital Pin 13
```

### LCD 16x2 (Standard Parallel)
```
LCD 16x2 Connections:
├── Pin 1  VSS (GND)     → Arduino GND
├── Pin 2  VDD (VCC)     → Arduino 5V
├── Pin 3  V0 (Contrast) → Arduino GND directly
├── Pin 4  RS            → Arduino Digital Pin 2
├── Pin 5  RW            → Arduino GND directly
├── Pin 6  EN            → Arduino Digital Pin 4
├── Pin 7  DB0           → Not Connected
├── Pin 8  DB1           → Not Connected
├── Pin 9  DB2           → Not Connected
├── Pin 10 DB3           → Not Connected
├── Pin 11 DB4           → Arduino Digital Pin 5
├── Pin 12 DB5           → Arduino Digital Pin 6
├── Pin 13 DB6           → Arduino Digital Pin 7
├── Pin 14 DB7           → Arduino Digital Pin 8
├── Pin 15 LED+          → Arduino 5V (via 220Ω resistor)
└── Pin 16 LED-          → Arduino GND
```

> **Important Notes:**
> - V0 (contrast) must be connected directly to GND — no potentiometer needed in Tinkercad
> - RW must be connected directly to GND, NOT to any Arduino pin
> - DB0 to DB3 must be left completely unconnected (4-bit mode)

---

## Wiring Checklist

- [ ] Ping SIG connected to Arduino Pin 9
- [ ] Servo SIG connected to Arduino Pin 13
- [ ] LCD RS connected to Arduino Pin 2
- [ ] LCD RW connected to GND directly
- [ ] LCD EN connected to Arduino Pin 4
- [ ] LCD DB4 connected to Arduino Pin 5
- [ ] LCD DB5 connected to Arduino Pin 6
- [ ] LCD DB6 connected to Arduino Pin 7
- [ ] LCD DB7 connected to Arduino Pin 8
- [ ] LCD VO connected to GND directly
- [ ] LCD DB0–DB3 left unconnected
- [ ] All GND connections made
- [ ] All 5V connections made

---

## Code

```cpp
#include <LiquidCrystal.h>
#include <Servo.h>

// RS, EN, D4, D5, D6, D7
LiquidCrystal lcd(2, 4, 5, 6, 7, 8);

Servo myServo;

const int pingPin = 9;
const int servoPin = 13;

long readDistance() {
  long duration, distance;
  pinMode(pingPin, OUTPUT);
  digitalWrite(pingPin, LOW);
  delayMicroseconds(2);
  digitalWrite(pingPin, HIGH);
  delayMicroseconds(5);
  digitalWrite(pingPin, LOW);
  pinMode(pingPin, INPUT);
  duration = pulseIn(pingPin, HIGH);
  distance = duration * 0.034 / 2;
  return distance;
}

void setup() {
  Serial.begin(9600);
  myServo.attach(servoPin);
  lcd.begin(16, 2);
  lcd.setCursor(0, 0);
  lcd.print("Distance Meter");
}

void loop() {
  long distance = readDistance();

  Serial.print("Distance: ");
  Serial.print(distance);
  Serial.println(" cm");

  lcd.setCursor(0, 1);
  lcd.print("Dist: ");
  lcd.print(distance);
  lcd.print(" cm   ");

  if (distance < 20) {
    myServo.write(90);
  } else {
   lcd.print("NO OBJECT FOUND");
  }

  delay(300);
}
```

---

## How It Works

1. The Ping))) sensor sends an ultrasonic pulse and measures the time it takes to bounce back
2. The Arduino calculates the distance using the formula: `distance = (duration × 0.034) / 2`
3. The distance is displayed on the LCD screen in centimeters
4. If the object is **closer than 20 cm**, the servo rotates to **90°**
5. If the object is **farther than 20 cm**, the servo returns to **0°**

---

## Simulating in Tinkercad

1. Start the simulation
2. Click on the Ping))) sensor
3. A distance slider will appear — drag it to simulate an object at different distances
4. Watch the LCD update and the servo move in real time

---

## Notes & Modifications

```
- Using standard 16x2 LCD (not I2C) as Tinkercad does not support LiquidCrystal_I2C library
- VO pin connected to GND instead of potentiometer for contrast in simulation
- Ping))) Parallax sensor used instead of HC-SR04 as it uses a single SIG pin
- Servo threshold set to 20 cm — modify in code as needed
```
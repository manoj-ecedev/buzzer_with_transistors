# Buzzer Control Using PNP Transistor

This project demonstrates how to control both **active** and **passive** buzzers using a **PNP transistor** with an Arduino or any microcontroller. It shows how to drive buzzers safely without drawing too much current from GPIO pins.

---

## 🧠 What You’ll Learn

- Difference between active and passive buzzers
- How to use **PNP transistor** to switch buzzers
- How to safely control buzzers using GPIO pins

---

## 🔊 Buzzer Types

### ✅ Active Buzzer
- Makes sound when given power (DC)
- No need for PWM
- Use `digitalWrite(pin, HIGH/LOW)` to control

### ✅ Passive Buzzer
- Needs square wave (PWM)
- Use `tone(pin, frequency)` and `noTone(pin)` in Arduino

---

## 🔌 Circuit 1: Active Buzzer with PNP Transistor

### Components:
- Arduino / any microcontroller
- **PNP Transistor** (e.g., BC557)
- 1kΩ resistor (for transistor base)
- Active Buzzer
- Power supply (3.3V or 5V)

### Wiring:
- Buzzer `-` to GND
- Buzzer `+` to **Emitter** of PNP transistor
- **Collector** of transistor to 5V
- GPIO pin to transistor **Base** through 1kΩ resistor
- Add **pull-up resistor (10kΩ)** on base to Vcc

### Arduino Code:
```cpp
int buzzer = 7;

void setup() {
  pinMode(buzzer, OUTPUT);
}

void loop() {
  digitalWrite(buzzer, LOW);  // Buzzer ON (PNP triggered)
  delay(1000);
  digitalWrite(buzzer, HIGH); // Buzzer OFF
  delay(1000);
}
```

---

## 🔌 Circuit 2: Passive Buzzer with PNP Transistor

- Same setup as above
- Use `tone()` and `noTone()`
- Make sure tone is sent while base is LOW

### Arduino Code:
```cpp
int buzzer = 7;

void setup() {}

void loop() {
  tone(buzzer, 1000); // 1kHz tone
  delay(1000);
  noTone(buzzer);
  delay(1000);
}
```

---

## ⚠️ Tips

- Never power buzzers directly from GPIO if they draw more than 20-30 mA.
- Always use a base resistor for transistors (typically 1kΩ).
- Use diode protection (like 1N4007) across buzzer terminals for inductive spikes.

---

## 🧰 Optional Tools

- Breadboard
- Multimeter
- Oscilloscope (for testing passive buzzer waveform)

---

## 📷 Circuit Diagrams

> Diagrams not included here. Ask for visuals if needed!

---

## ✅ License

MIT License — Use freely for learning and projects.

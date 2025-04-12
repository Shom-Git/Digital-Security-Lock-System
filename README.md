# RFID-Enabled Door Lock System with SMS-Based Remote Control

An integrated security system built on Arduino that combines **RFID authentication**, **keypad-based password entry**, and **SMS communication** via the SIM800 module. This project demonstrates a secure, remotely operable door locking mechanism with real-time alerts and dual-factor authentication.

---

## 🚀 Features

- **RFID Authentication:** Validates access using a unique RFID tag via the MFRC522 module.  
- **Password Protection:** Requires a secondary 4-digit password for added security.  
- **SMS-Based Control:** Enables remote operation (`open` / `close`) through SMS using the SIM800 GSM module.  
- **Real-Time Alerts:** Sends SMS notifications on unauthorized access attempts or successful entries.  
- **Visual & Audible Feedback:** Uses LEDs and buzzer to indicate access status.  
- **Servo-Controlled Locking:** Controls a servo motor to physically lock/unlock the door.

---

## 🧰 Hardware Components

| Component            | Description                        |
|---------------------|------------------------------------|
| Arduino (Uno/Nano)  | Microcontroller unit               |
| MFRC522              | RFID module                        |
| 4x4 Keypad           | For password input                 |
| SIM800 GSM Module    | SMS communication                  |
| 16x2 LCD (I2C)       | User interface display             |
| Servo Motor          | Door lock actuator                 |
| Buzzer + LEDs        | Status indicators                  |

---

## 📌 Pin Configuration

| Component     | Arduino Pins            |
|---------------|--------------------------|
| MFRC522       | SS (10), RST (9), SPI bus|
| Keypad        | Rows: D0–D2, Cols: A0–A3 |
| Servo Motor   | D8                       |
| Green LED     | D7                       |
| Red LED       | D6                       |
| Buzzer        | D5                       |
| SIM800        | TX (D3), RX (D4)         |
| LCD (I2C)     | SDA (A4), SCL (A5)       |

---

## ⚙️ System Workflow

1. **Idle Mode:** LCD displays prompt to scan RFID tag.
2. **RFID Scan:**
   - If valid tag detected: User is prompted to enter a 4-digit password.
   - If invalid: System denies access and sends an alert via SMS.
3. **Password Entry:**
   - If correct: Unlocks door (servo rotates), sends confirmation SMS.
   - If incorrect: Access denied, sends alert SMS.
4. **Remote Control via SMS:**
   - Send `open` to unlock the door remotely.
   - Send `close` to temporarily disable user interaction mode.

---

## 📲 SMS Configuration

The SIM800 module handles SMS functionality.  
To set your recipient number, modify the following line:

```cpp
SIM800.println("AT+CMGS=\"+91xxxxxxxxxx\"");
```

> Replace `+91xxxxxxxxxx` with your mobile number in international format.

---

## 📦 Required Libraries

Ensure these libraries are installed in your Arduino IDE:

- `MFRC522`
- `Keypad`
- `LiquidCrystal_I2C`
- `SoftwareSerial`
- `Servo`
- `SPI`

---

## 🔐 Security Considerations

- Two-factor authentication: RFID + password.
- SMS alerts notify the user of any unauthorized attempts.
- Remote shutdown capability enhances control in critical situations.

---

## 🔄 Potential Improvements

- Store multiple RFID tags and passwords in EEPROM or external storage.
- Add real-time clock (RTC) for timestamped logs.
- Integrate with a web dashboard or IoT platform (e.g., Blynk, ThingSpeak).
- Use fingerprint module for biometric authentication.

---

## 📷 Media

*(Add setup photos, wiring diagram, or demo video link here)*

---

## 📚 License

This project is open-source and available under the [MIT License](LICENSE).

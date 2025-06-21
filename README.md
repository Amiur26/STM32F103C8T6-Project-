
# 🛠️ STM32 Master-Slave Embedded System Project (CSE331 Lab Tasks 5–8)

This project was developed as part of the **CSE331L: Microprocessor Interfacing and Embedded Systems** course at **North South University**. It involves building a master-slave communication system using two **STM32F103C8T6** microcontrollers to demonstrate sensor integration, real-time control, and UART-based inter-device communication.


## 🔧 Tools and Components Used

- 2× STM32F103C8T6 Blue Pill Boards  
- DHT11 Temperature & Humidity Sensor  
- HC‑SR04 Ultrasonic Sensor  
- SSD1306 OLED Display (I2C)  
- IR Sensor  
- Servo Motor  
- External LED  
- STM32CubeIDE + HAL Library  

---

## 🔄 System Overview

### Master Board
- Reads temperature and humidity from **DHT11**
- Measures distance using **HC‑SR04 Ultrasonic**
- Displays readings on **SSD1306 OLED**
- Sends UART signal to Slave Board every 2 seconds

### Slave Board
- Listens on UART, blinks LED when receiving `'1'`
- Detects objects with **IR sensor**
- Controls Servo Motor to simulate door opening/closing

---

## 📚 Tasks Breakdown

### ✅ Task 5: Door Control (Slave)
- **Trigger:** IR sensor detects object  
- **Action:** Rotate servo to 90° to “open”  
- **Revert:** Return to 0° for “closed”

### ✅ Task 6: Distance Display (Master)
- Measure distance via **HC‑SR04**, show on OLED

### ✅ Task 7: Temperature & Humidity (Master)
- Read **DHT11**, display °C and % on OLED

### ✅ Task 8: UART Inter‑Board Communication
- Master sends `'1'` every 2 s  
- Slave blinks LED upon reception

---

## 🔗 Interfaces Summary

| Component         | Interface | Master   | Slave            |
|------------------|-----------|----------|------------------|
| OLED Display      | I2C       | Yes      | No               |
| UART (USART2)     | TX/RX     | PA2 → TX | PA3 ← RX         |
| IR Sensor         | GPIO      | No       | PA2              |
| Servo Motor       | PWM       | No       | TIM2_CH2 (PA1)   |
| DHT11 Sensor      | GPIO      | PB5      | No               |
| Ultrasonic Sensor | GPIO      | PA11/PA12| No               |

---

## 📸 Architecture Overview

```

\[Master Board]
├─ DHT11 → Temp/Humidity readings
├─ Ultrasonic → Distance readings
├─ OLED ← I2C display
└─ UART TX → Slave Board

\[Slave Board]
├─ UART RX → LED blink on '1'
└─ IR Sensor + Servo → Door control

```

---

## 👏 Special Acknowledgment

We’d like to extend our sincere gratitude to **MicroPeta (Nizar Mohideen)**. His comprehensive STM32CubeIDE tutorials—covering OLED I2C, servo PWM, DHT11, ultrasonic sensors, and more—were an invaluable learning resource during this project 

---

## ⚠️ Challenges Faced

- Synchronizing UART transmissions across boards  
- Accurate PWM configuration for servo  
- Managing timing and peripheral delays  
- Ensuring reliable power distribution  
- Preventing resource contention between I2C and UART

---

## ✅ Conclusion

The project successfully integrates multiple sensors, actuators, and inter-board communication, showcasing embedded design, real-time automation, and software-hardware interface skills—all built using STM32CubeIDE and the STM HAL library.

---

## 📁 File Structure

```

/project-root
├── Master/
│   └── main.c
├── Slave/
│   └── main.c
├── README.md
└── report.pdf

```

---

## 📜 License

This project is for academic use only. All STM32-related code uses the STM HAL license included with STM32CubeIDE.
```

---


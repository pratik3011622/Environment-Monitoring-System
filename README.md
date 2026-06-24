# 🌿 Smart Environmental Monitoring System using STM32

> Real-time monitoring of air quality, temperature & humidity using embedded technology.

---

## 👥 Team

| Name | Roll No |
|------|---------|
| Pratik Ranjan | 24EC034 |
| Priyanshu Verma | 24EC036 |
| Vidhan Jain | 24EC045 |
| Avi Sinha | 24EC106 |
| Nilendu Das | 24EC110 |

---

## 📖 About the Project

Air pollution is one of the most serious environmental issues affecting human health worldwide. Harmful gases like **CO**, **CH₄**, and **LPG** can cause severe health hazards when present beyond safe limits. At the same time, temperature and humidity play a significant role in human comfort and industrial processes.

This project implements a **smart, low-cost environmental monitoring system** that continuously tracks air quality and environmental parameters, providing real-time data using sensors interfaced with an STM32 microcontroller.

---

## ⚙️ System Overview

```
MQ9 Gas Sensor ──► STM32 MCU ──► LCD Display
DHT11 Sensor   ──►     │
                        └──► Real-time Output
```

| Stage | Description |
|-------|-------------|
| **Gas Detection** | MQ9 detects CO, CH₄ & LPG via resistance change; ADC reads analog output |
| **Env. Sensing** | DHT11 measures temperature (0–50°C) & humidity (20–90% RH) digitally |
| **Processing** | STM32 processes sensor inputs, runs conversion logic and formats output |
| **Display** | 16×2 LCD (I2C) shows real-time sensor values in a human-readable format |

---

## 🛠️ Hardware Components

### Core Components

| Component | Description |
|-----------|-------------|
| **STM32F103RB** | 32-bit ARM Cortex-M3 MCU @ 72 MHz |
| **MQ9 Gas Sensor** | Detects CO, CH₄, LPG (analog output) |
| **DHT11 Sensor** | Temperature (0–50°C) & Humidity (20–90% RH) |
| **16×2 LCD (I2C)** | Real-time data display via I2C bus |

### Supporting Parts

- 10kΩ pull-up resistor (for DHT11)
- Breadboard for prototyping
- Jumper wires
- 5V USB / regulated power supply

---

## 🔌 Pin Configuration

| Pin | Connected To |
|-----|-------------|
| PA0 | MQ9 Analog Input |
| PA1 | DHT11 Digital Input |
| PB6 | I2C SCL (LCD) |
| PB7 | I2C SDA (LCD) |

---

## 🧠 STM32 Microcontroller Specs

| Parameter | Value |
|-----------|-------|
| Architecture | 32-bit ARM Cortex-M3 |
| Clock Speed | Up to 72 MHz |
| Flash Memory | 128 KB |
| SRAM | 20 KB |
| Package | STM32F103RB |

### Key Functional Units

- **ADC** — Converts analog MQ9 signal to digital values
- **GPIO** — Handles single-wire DHT11 digital communication
- **I2C** — Communicates with the 16×2 LCD display module
- **Timers** — Manages sensor polling intervals and delays

---

## 🔬 Sensor Details

### MQ9 Gas Sensor

Detects: **Carbon Monoxide (CO)**, **Methane (CH₄)**, **LPG (C₃H₈)**

**Working Principle:**
1. SnO₂ (tin dioxide) forms the active sensing layer
2. Gas concentration alters the electrical resistance of the sensing material
3. A variable voltage proportional to gas concentration is produced at the output
4. STM32 ADC reads this analog voltage and converts it to a digital value

> ⚠️ **Note:** The MQ9 requires preheating for stable readings and periodic calibration for accurate concentration values.

---

### DHT11 Sensor

| Parameter | Value |
|-----------|-------|
| Temperature Range | 0°C – 50°C |
| Humidity Range | 20% – 90% RH |
| Calibration | Factory calibrated |
| Protocol | Single-wire digital communication |
| Data Output | 40-bit digital data frame |

**Data Frame Structure:**  
`8-bit Humidity` + `8-bit Decimal` + `8-bit Temperature` + `8-bit Decimal` + `8-bit Checksum`

---

## 🔄 Working Principle

```
1. Power On → Initialize sensors & LCD
2. Gas Detection → MQ9 detects gas via resistance change
3. ADC Conversion → STM32 converts analog MQ9 signal to digital
4. Temp/Humidity → DHT11 sends 40-bit data over single wire
5. Processing → STM32 processes and formats all sensor data
6. LCD Output → Data displayed on 16×2 I2C LCD
7. Loop → Entire cycle repeats continuously
```

---

## 💻 Software Design

The firmware handles four key tasks:

| Task | Description |
|------|-------------|
| **ADC Reading** | Reads analog voltage from MQ9, converts to gas concentration |
| **DHT11 Protocol** | Implements 1-wire protocol to receive 40-bit sensor data |
| **Data Conversion** | Applies formulas to convert raw ADC/DHT values to meaningful units |
| **LCD Interface** | Formats and writes sensor data to I2C LCD |


---

## ✅ Advantages & ❌ Limitations

| ✅ Advantages | ❌ Limitations |
|--------------|----------------|
| Real-time environmental monitoring | MQ9 requires periodic calibration |
| Low-cost and easy to build | DHT11 has limited accuracy range |
| Portable and compact design | No buzzer/alert in the base design |
| Multi-parameter sensing in one device | Not suitable for high-precision industrial use |

---

## 🌍 Applications

- **Indoor Air Quality** — Monitor homes, classrooms, and offices for CO & pollutants
- **Industrial Safety** — Detect gas leaks in factories and chemical processing plants
- **Smart Buildings** — Integrate with HVAC systems for automated environmental control
- **Environmental Stations** — Deploy in outdoor monitoring stations for city-wide data

---

## 🚀 Future Scope

- [ ] Add buzzer/alert system for gas leakage detection
- [ ] Wi-Fi / IoT integration for remote monitoring
- [ ] Cloud storage and real-time analytics dashboard
- [ ] Upgrade to MQ135 / DHT22 for higher accuracy
- [ ] Battery-powered portable standalone version

> This project can evolve into a **fully automated smart IoT-based environmental safety system**.





---

*"Prevention is better than cure — early detection saves lives."*

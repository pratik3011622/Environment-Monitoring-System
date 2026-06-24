

INTRODUCTION
Air pollution is a critical environmental issue that significantly impacts human health and global ecosystems. Harmful gases like Carbon Monoxide (CO), Methane (CH4), and Liquefied Petroleum Gas (LPG) can pose severe health hazards if they exceed safe limits. Additionally, temperature and humidity play a crucial role in human comfort, climate conditions, and industrial processes.

This project is a smart monitoring system designed to continuously track air quality and environmental parameters, providing real-time data to users via sensors and an STM32 microcontroller.

TEAM MEMBERS
• Pratik Ranjan (24EC034)
• Nilendu Das (24EC110)
• Avi Sinha (24EC106)
• Vidhan Jain (24EC045)
• Priyanshu Verma (24EC036)

OBJECTIVES
• Develop a real-time environmental monitoring system.
• Detect harmful gases using dedicated gas sensors.
• Measure temperature and humidity accurately.
• Display data clearly for user awareness and early hazard detection.

HARDWARE COMPONENTS
• STM32F103RB Microcontroller: Core processing unit (32-bit ARM Cortex-M3 running up to 72 MHz).
• MQ9 Gas Sensor: Detects CO, CH4, and LPG via resistance changes. Outputs an analog voltage proportional to gas concentration.
• DHT11 Sensor: Measures ambient temperature (0 to 50°C) and relative humidity (20 to 90% RH) via a single-wire digital protocol.
• 16x2 LCD Display (I2C): Displays real-time sensor values. The I2C module reduces wiring to just two communication lines.
• Supporting Parts: 10kΩ pull-up resistor, breadboard, jumper wires, and 5V power supply.

PIN CONFIGURATION
• PA0: MQ9 Analog Input
• PA1: DHT11 Digital Input
• PB6: I2C SCL (LCD Display)
• PB7: I2C SDA (LCD Display)

WORKING PRINCIPLE

1) Initialization: The system initializes the sensors and the LCD display on power-up.

2) Data Acquisition: The MQ9 sensor detects gas concentration and outputs a proportional analog voltage. The DHT11 sensor transmits a 40-bit digital data frame over a single wire.

3) Processing: The STM32 microcontroller's internal ADC converts the analog signal from the MQ9 into digital values, while handling the digital communication from the DHT11.

4) Display: The MCU formats all sensor data and writes it to the 16x2 I2C LCD for real-time visualization.

5) Continuous Polling: The system loops continuously, managing sensor polling intervals and updating the display.

ADVANTAGES
• Provides continuous, real-time environmental monitoring.
• Features multi-parameter sensing in a single device.
• Low-cost, portable, and modular design.

LIMITATIONS
• MQ9 sensor requires periodic calibration.
• DHT11 sensor has a limited accuracy range, unsuitable for high-precision industrial use.
• The base design currently lacks an audible buzzer or alert mechanism.

APPLICATIONS
• Indoor Air Quality: Monitoring homes, classrooms, and offices for pollutants.
• Industrial Safety: Early detection of hazardous gas leaks in factories.

FUTURE UPGRADES
• Integrating with HVAC units for automated building controls.
• Adding an alert buzzer for immediate hazard notifications.
• Upgrading to more precise sensors like the MQ135 or DHT22.
• Adding Wi-Fi/IoT connectivity for cloud storage and remote monitoring.
• Developing a standalone, battery-powered portable unit.

CONCLUSION
This project successfully implements a smart, cost-effective, and scalable environmental monitoring system using an STM32 microcontroller. By providing reliable, real-time data on gas concentration, temperature, and humidity, the system keeps users informed and aids in accident prevention.

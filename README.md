This project implements a Digital Floor Mat Security System using Raspberry Pi, pressure sensor, and MCP3008 ADC.
When human foot pressure is detected on the floor mat, the system triggers:

🔔 Buzzer alert

📩 Telegram notification

📧 Email alert

This system is useful for theft detection, restricted area security, and smart surveillance applications.

🚀 Features

Detects human foot pressure using analog sensor

Uses MCP3008 ADC to read analog values

Sends real-time Telegram alerts

Sends Email alerts via Gmail SMTP

Activates buzzer alarm

Includes cooldown time to prevent alert spamming

🧰 Hardware Requirements

Raspberry Pi (any model with GPIO & SPI)

Pressure sensor / Force Sensitive Resistor (FSR)

MCP3008 Analog to Digital Converter

Buzzer

Jumper wires

Breadboard

Internet connection (for Telegram & Email)

🧑‍💻 Software Requirements

Python 3

Raspberry Pi OS

Required Python libraries:

pip install spidev RPi.GPIO requests

🔌 Circuit Connections
MCP3008 to Raspberry Pi (SPI)
MCP3008 Pin	Raspberry Pi Pin
VDD	3.3V
VREF	3.3V
AGND	GND
DGND	GND
CLK	GPIO 11 (SCLK)
DOUT	GPIO 9 (MISO)
DIN	GPIO 10 (MOSI)
CS	GPIO 8 (CE0)
CH0	Pressure Sensor
Buzzer

Positive → GPIO 18

Negative → GND

🔔 Working Principle

Pressure sensor produces an analog signal when stepped on.

MCP3008 converts analog value to digital ADC value.

Raspberry Pi continuously monitors ADC readings.

If ADC value crosses the threshold:

Buzzer turns ON

Telegram alert is sent

Email alert is sent

Cooldown delay avoids repeated alerts for the same event.

⚙️ Configuration
Telegram Setup

Create a Telegram bot using BotFather

Replace values in code:

BOT_TOKEN = "YOUR_BOT_TOKEN"
CHAT_ID = "YOUR_CHAT_ID"

Email Setup

Use Gmail App Password

SENDER_EMAIL = "your_email@gmail.com"
APP_PASSWORD = "your_app_password"
RECEIVER_EMAIL = "receiver_email@gmail.com"

🧪 Threshold Settings
LOCKED_THRESHOLD = 100   # Pressure sensitivity
COOLDOWN = 10            # Seconds between alerts


Adjust threshold based on sensor sensitivity.

🟢 System Start Message

Telegram message:
"🟢 Floor Security System Started"

🔴 System Stop Message

Telegram message:
"🔴 Floor Security System Stopped"

🛑 Safety Notes

Never expose Raspberry Pi to high voltage

Use proper grounding

Keep credentials secure (use environment variables for production)

📌 Applications

Home security

Office restricted areas

Anti-theft systems

Smart floors

Industrial safety monitoring


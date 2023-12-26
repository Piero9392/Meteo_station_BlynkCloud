# The LoRa-based Wireless Weather Station 📡📶

This LoRa-based wireless weather station monitors various environmental parameters, including temperature, humidity, pressure, altitude, dew point, gas and light intensity.


The weather station comprises two LoRa devices: Sender and Receiver.

The Sender measures environmental parameters using BME680 (temperature🌡️, humidity☔️, pressure⏱️, altitude⛰️, dew point💧, gas💨 sensor), BH1750 (light sensor💡) and transmits this data over the LoRa protocol to the Receiver. You can place the Sender remotely, even a few kilometers away from the Receiver.


The data obtained by Receiver can be viewed in multiple ways:
* Display data on the Receiver’s OLED display 🖥️
* Send data by RECEIVER to Blynk.Cloud server over WiFi 🌐, enabling you to remotely monitor 🔍 all data in real-time using the 'Blynk IoT' application📱for iOS or Android

Additionally, you can retrieve the value of any parameter 📈 for the last period: hour, day, week, month, etc. The Receiver also retrieves Time 🕖 and Date 📅 from the NTP Server at [https://www.ntppool.org](https://www.ntppool.org). You can choose what to display on the OLED (received Telemetry or Time/Date from the server) by switching the button 🖲 on the Receiver itself or the virtual button 🔘 in the “Blynk IoT” application 📲 for iOS or Android.

The RECEIVER includes three LEDs🚦:
* 🔴 Red LED used as an indicator of low RSSI level (less than -120dB) from Sender
* 🟡 Yellow LED used as an indicator of data receipt from Sender
* 🟢 Green LED used as an indicator of successful Blynk.Cloud server connection

## Hardware Components

### Sender 📡:
* 🛠 Arduino Pro Mini 3.3V microcontroller
* 🗼 BME680 sensor
* 🗼 BH1750 sensor
* 📡 LoRa module Ra-02 SX1278
* 🔌 AMS1117CD-3.3 voltage regulator

### Receiver 🖥️:
* 🛠 ESP32 microcontroller 
* 📡 LoRa module Ra-02 SX1278
* 🖥️ SSD1306 OLED display
* 🖲 Push button
* 🚦 3 x LED
* ®️ 3 x 220 Ohm resistors

## Software

The Arduino code for this project is written in C++. It uses the built-in libraries.

## Wiring

### Sender (Arduino Pro Mini 3.3V):

* 📡 LoRa module Ra-02 SX1278 :
    * 3.3V: connect to 3.3V
    * GND: connect to GND
    * RST: connect to D6
    * D100: connect to D2
    * NSS: connect to D10
    * MOSI: connect to D11
    * MISO: connect to D12
    * SCK: connect to D13

* 🗼 BME680 sensor:
    * VCC: connect to 3.3V
    * GND: connect to GND
    * SDA: connect to A4
    * SCL: connect to A5

* 🗼 BH1750 sensor:
    * VCC: connect to 3.3V
    * GND: connect to GND
    * SDA: connect to A4
    * SCL: connect to A5

* 🔌 AMS1117CD-3.3 voltage regulator:
    * VCC: connect to Programming Header VCC Pin
    * GND: connect to Programming Header GND Pin

### Receiver (ESP32):

* 📡 LoRa module Ra-02 SX1278:
    * 3.3V: connect to 3.3V
    * GND: connect to GND
    * RST: connect to GPIO14
    * D100: connect to GPIO2
    * NSS: connect to GPIO5
    * MOSI: connect to GPIO23
    * MISO: connect to GPIO19
    * SCK: connect to GPIO18

* 🖥️ SSD1306 OLED display:
    * VCC: connect to 3.3V
    * GND: connect to GND
    * SDA: connect to GPIO21
    * SCL: connect to GPIO22

* 🖲 Switch button:
    * PIN1: connect to GPIO17
    * PIN2: connect to GND

* 🔴 Red LED:
    * Cathode: connect to GPIO4 through resistor 220 Ohm
    * Anode: connect to GND

* 🟡 Yellow LED:
    * Cathode: connect to GPIO13 through resistor 220 Ohm
    * Anode: connect to GND

* 🟢 Green LED:
    * Cathode: connect to GPIO12 through resistor 220 Ohm
    * Anode: connect to GND

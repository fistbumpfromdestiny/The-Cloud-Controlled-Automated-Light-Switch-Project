# The Cloud Controlled Automated Light Switch Project

## Project Overview
This project is to be considered a Proof of Concept of an automated lighting system. 
It is governed by the amount of light received by a photo transistor in relation
to the time of the day. Data is being sent over MQTTS to AWS IoT Core, where 
rules dictate whether or not it's appropriate to light a lamp.

### Hardware
- The project uses an ESP32-C3-DevKitM-1 development board to gather, send and receive data over
  Wi-Fi to an MQTT topic in AWS IoT Core. An MCL053GD LED acts as a lamp.


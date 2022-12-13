# The Cloud Controlled Automated Light Switch Project

## Project Overview
This project is to be considered a Proof of Concept of an automated lighting system. 
It is governed by the amount of light received by a photo transistor in relation
to the time of the day. Data is being sent over MQTTS to AWS IoT Core, where 
rules dictate whether or not it's appropriate to light a lamp.

### Hardware
- The project uses an ESP32-C3-DevKitM-1 development board to gather, send and receive data over
  Wi-Fi to an MQTT topic in AWS IoT Core. An MCL053GD LED acts as a lamp.

# Architecture Overview
<img src="aws.jpg" width="800"/>

## Workflow
Information flows as following:

1 - Light data is gathered with the photo transistor.

2 - The ESP32 (or the device) averages the light data gathered over 10 seconds and sends the data 
    to AWS IoT Core 
    over MQTTS. The ESP32 also receives data back from AWS upon which it acts. It can either turn
    lamp on or off.

3 - The lamp. It gets turned on and off by the ESP32.

4 - MQTT, a network procotol for Message Queuing. It's used to enable the ESP32 to communicate with 
    AWS Cloud Services. 

5 - Messages is being sent to an MQTT Topic in AWS's IoT Core. In this case our device sends (or
    publishes) messages to the topic 'esp32/+/pub' where the + character is a wildcard for our 
    devices' unique ID. Since we're only operating one device in this PoC, the device ID has been
    set to '1'. Our device also subscribes to the topic 'esp32/+/sub' which enables it to receive messages or commands which to act upon.

6 - Whenever a message has been received 

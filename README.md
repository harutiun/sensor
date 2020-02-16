# General purpose
This project consists of an air quality measurement data logger. We are a school, and want to know the air quality and the environment in the classrooms and common spaces of the school, especially while the children are in class. The stations will be in the school, will be powered by a charger connected to the network, and will access the school's WIFI.

As hardware we used Arduinos, with an Environmental Shields, to measure temperature, humidity and more values, and also different SeeedStudio Grove sensors.

The Arduinos are connected to an SSID and a MQTT broker, housed in my case in a Raspberry Pi. Each Arduino makes the measurements every certain period of time, and sends that string of characters (maximum 240) to the MQTT broker, hosted on a Raspberry Pi. This is  mosquitto. To control mosquitto, I use NodeRed, which writes the data to an influxDB database. This database is readen and displayed by Grafana.

To change the logging times, Node Red sends a message to all the users at certain times, with the new logging interval. All this services are in a docker. The hole docker configuration comes from https://www.youtube.com/watch?v=a6mjt8tWUws&t=656s.

Each station should measure the following values throughout the school: Temperature, Humidity, CO2, TVOC, General Air quality, PM1.0 concentration, PM2.5 concentration, PM10 concentration, noise, Illuminance. The stations will be indoors (classrooms and common areas) and one will be outdoors, and will also measure pressure. 

# Hardware
As Hardware we decided to use: Arduino mkr 1010 board, with MKR EnvShield and MKR Grove Carrier, and 3.3V Grove sensors from Seedstudio.

-ARDUINO MKR WIFI 1010: https://store.arduino.cc/mkr-wifi-1010
-ARDUINO MKR ENV SHIELD: https://store.arduino.cc/arduino-mkr-env-shield
-ARDUINO MKR CONNECTOR CARRIER (GROVE COMPATIBLE): https://store.arduino.cc/arduino-mkr-connector-carrier

-Grove - VOC and eCO2 Gas Sensor (SGP30): https://www.seeedstudio.com/Grove-VOC-and-eCO2-Gas-Sensor-SGP30.html
-Grove - Air quality sensor v1.3: https://www.seeedstudio.com/Grove-Air-quality-sensor-v1-3-p-2439.html
-Grove - Sound Sensor: https://www.seeedstudio.com/Grove-Sound-Sensor.html
-Grove - Laser PM2.5 Sensor (HM3301): http://wiki.seeedstudio.com/Grove-Laser_PM2.5_Sensor-HM3301/

As this is a school project, we will start with simple MKR 1010 projects, and then gradually scale up. In the end we will set up the whole station, applying things that the boys and girls have worked on before.

# About me
I am a secondary school teacher, teaching the subjects Biology, German Culture and OFFICE/Computer Science. Kawum. At the beginning of the school year I was asked to set up a series of environmental measurement stations in our school, in order to measure and monitor the air quality there. It was focused as a project to be done partly with students, but with a real production purpose. To be honest, I am a mathematician, have programmed for several years, and I knew a little about Arduino, without having come to make any project until that moment, only some workshop of lighting leds. At the beginning I found it quite a simple task. I knew that measuring the temperature is one of the first exercises you learn with Arduino. 
I started on my own with a WeMos board, borrowed from a friend, and a DHT11 sensor, uploading the data via WiFi to https://thingspeak.com/. Things got complicated when I was told that many other values had to be measured as well, ... I didn't know where to go anymore, as I couldn't find simple shields that could measure all those values. And I found myself unable to weld a single wire, and with students... Ufff. So I asked some experts for help, and was led back to the world of arduino, mkr1010, with environmental shields, and GrooveConnector. As sensors, Seedstudio at 3.3V. The sensors are plug and play. It's more expensive than other stuff, but it's solid and easy to use.


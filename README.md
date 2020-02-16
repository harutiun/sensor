# Sensor
This project consists of an air quality data logger. I am a teacher, and our school wants to know the air quality and the environment values in classrooms and common spaces, especially while the children are there. The stations will placed in different rooms in our school, powered by a charger, and will access the school's WIFI.

As hardware we use Arduinos, with environmental shields, to measure temperature, humidity and more values, and also different SeeedStudio Grove sensors.

The Arduinos are connected to an SSID and a MQTT broker, housed in a Raspberry Pi (RPI). Each Arduino makes the measurements every certain period of time, and sends that string of characters (maximum 240) to the MQTT broker, hosted on the RPI. This broker runs under  mosquitto. To control mosquitto, I use NodeRed, which writes the data to an influxDB database. This database is readen and displayed by Grafana.

To change the logging times, Node Red sends a message to all the users at certain times, with the new logging interval. All this services are in a docker. The hole docker configuration comes from https://www.youtube.com/watch?v=a6mjt8tWUws&t=656s.

Each station should measure the following values throughout the school: Temperature, Humidity, CO2, TVOC, General Air quality, PM1.0 concentration, PM2.5 concentration, PM10 concentration, noise, Illuminance. The stations will be indoors (classrooms and common areas) and one will be outdoors, and will also measure pressure. 

# Hardware
As Hardware we decided to use: Arduino mkr 1010 board, with MKR EnvShield and MKR Grove Carrier, and 3.3V Grove sensors from Seedstudio.

-ARDUINO MKR WIFI 1010: https://store.arduino.cc/mkr-wifi-1010
-ARDUINO MKR ENV SHIELD: https://store.arduino.cc/arduino-mkr-env-shield
-ARDUINO MKR CONNECTOR CARRIER (GROVE COMPATIBLE): https://store.arduino.cc/arduino-mkr-connector-carrier

-Grove - Air quality sensor v1.3: https://www.seeedstudio.com/Grove-Air-quality-sensor-v1-3-p-2439.html
-Grove - Sound Sensor: https://www.seeedstudio.com/Grove-Sound-Sensor.html
-Grove - VOC and eCO2 Gas Sensor (SGP30): https://www.seeedstudio.com/Grove-VOC-and-eCO2-Gas-Sensor-SGP30.html
-Grove - Laser PM2.5 Sensor (HM3301): http://wiki.seeedstudio.com/Grove-Laser_PM2.5_Sensor-HM3301/
-Grove - Grove-I2C-Hub: https://www.seeedstudio.com/Grove-I2C-Hub.html

The VOC and eCO2 Gas Sensor, and the Laser PM2.5 Sensor use the i2c interface, but the mkr1010 only has one i2c port. 




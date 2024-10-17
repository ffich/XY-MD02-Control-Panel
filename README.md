# XY-MD02-Control-Panel
A Node-RED based control panel for the XY-MD02 RTU Modbus Temperature and Humidity Sensor.

# General Description
The XY-MD02 is a cheap Modbus Temperature and Humidity sensor, easy to find in various online store, like Amazon:

[Amazon Link](https://www.amazon.it/Nagoyuki-Trasmettitore-Temperatura-Acquisizione-Trasduttore/dp/B0CW9FK4QB/ref=sr_1_5?dib=eyJ2IjoiMSJ9.2Qq9TAs8_4z1WQKL5v_kfGe0PumFSk9Jfykix-x036QKABYK8seTRj0b9OYZ7scjIIrs4WKz9XZRrKEe9mxVw3nyVbhEdyNIEvzj1l7yyDJ6J5nIJVqWm9PPCcVRa37-c_PxQhGLHVDMzvOyenlaN1EIFN4B5tPRgqvc0ydwzzcN7h6FpSq4zvr62JFfuztMF6H3EKQwXl4fy69vsvdVMjIY4xm6Pv53jTPDbcRCy-W2QTaf56cpWI5M6YCon7bqOqIWVovilGJKwU310XjFD84Oi_Ru8xYhD4Pa8NRX6lU.HKLJhw2PwbLfF8s3DggYezA2Gf8M4DkvBWiueeu4K0o&dib_tag=se&keywords=modbus+sensor&qid=1729166459&sr=8-5)

This sensor is pretty handy for various applications and is a valuable resource to play with the Modbus protocol. I used one of this for a demo with [Arduino OPTA](https://www.arduino.cc/pro/hardware-arduino-opta/), and so, sice I needed to double check sensor readings and also to configure some parameter, I created a Node-RED panel to control and configure the device.

![image](https://github.com/user-attachments/assets/0f1bfdad-7b6e-4db1-b944-af1158b237fe)

With the interface you can:
- Read Temperature value
- Read Humidity Value
- Target diferent Unit ID
- Chage the device Address on the bus

Fetures that are "In development":
- Temperature&Humidity Logging
- Change baud rate and T&H calibration
- Device Address discovery
- Dinamyc change of the serial interface (if possible...)

# Setup and Dependencies
The node-RED project has some dependecies. They are:
- [Node-RED Dashboard](https://flows.nodered.org/node/node-red-dashboard) - Used creating the graphical panel
- [Node-RED Contrib Modbus](https://flows.nodered.org/node/node-red-contrib-modbus) - Used for interfacing the Modbus bus

You can run the panel from your PC or from another Linux-capable device, like raspberry and so on (by the way, have a look to the amazing [Arduino Portenta X8](https://store.arduino.cc/products/portenta-x8?gad_source=1&gclid=CjwKCAjw68K4BhAuEiwAylp3ku5NtZtFFGDzBeeaoA0KxLho1t2LwTcz2eu62Fy6S00V-7IdB3SvCRoC10gQAvD_BwE)). In the PC/Raspberry case you may need this [RS485 interface](https://www.amazon.it/Waveshare-USB-RS485-Converter-Lightningproof/dp/B0B87YJLJQ/ref=sr_1_1_sspa?crid=2DY7H0KWT15AA&dib=eyJ2IjoiMSJ9.ICo4Iu9xv8XUDsiut3LkYPzifZzEPBmrQ6JDB7l6d-DiNVEAYGu4fmZYigEnKQpW8__3MnMXmaWgLJNfBZUhKAyqwmbaLZ5fizVla6yKRKEJ_zAkYQGveU4HT-wfM09aN3ewPtUniMtFEcMJePBpMajQfh1jCSq4wTCa6rdGh_CMHjPrCpFAip3QsSJgMWay3kcnMLbkOAtP36KJGeFTeeNKzqYz_rhLLN_gyuXBCI6VSJw0-tgPTYMmlxuKWUS7hFEPdIdCbNzTDduSfTSHv0cVevFTO4nWWUxkoCELAME.X6tX_ncXIRps4Puo02c8nEa0AV2A6povcZTzd0_cRqs&dib_tag=se&keywords=usb+rs485&qid=1729167241&sprefix=usb+rs485%2Caps%2C130&sr=8-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1)

For instruction about how to run Node-RED, please have a look [here](https://nodered.org/docs/getting-started/).

Once you have node-RED up and running and you have installed all the dependencies, the last thing you need to do is to update the serial interface reference in the Modbus configuration node. The serial interface may have different names depending on the platform and overall system configuration. So open the flow, locate one of the modbus nodes and click on the pencil icon to open the Modbus server configuration (see pictures below):

![image](https://github.com/user-attachments/assets/2fe5ee68-8a49-4a66-83f2-9b557956c14e)

![image](https://github.com/user-attachments/assets/da0246cc-5bc4-4e47-a504-501a99733ba9)

Then identify the Serial Port section and click on the magnifier lens icon and select the correct one (in the picture is COM16):

![image](https://github.com/user-attachments/assets/67c441e1-e9cc-49fa-8b40-06de70545e95)

Update and deploy and you're all set, you should be able to use the Panel now.

# Device Address Change
To change the device addressing, put the new address in the "Address Update" Secrtion of the Panel and click on the "Update Address" Button. The device will reply with an updated configuration string that contains the new address. The change on the address will be effective at the next device power on (so make a power cycle if you want to use the new address).

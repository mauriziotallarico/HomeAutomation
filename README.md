# HomeAutomation
Fun projects in collaboration and mentored by Victor Turcu

Original suggestion follows:

here are, for the beginning, some info, recommendations :

The principle is simple : on a raspberry pi install home automation and remote devices with compatible fw (sensors or actuators) will be controlled/read. 

All sw and hw presented below are cheap, open source and are very well documented/supported by community. These are few principles that I follow in order to have a reasonable cost and time implementation.

- buy few items just to start :

    Raspberry Pi model 3 or 4 (I use model 3B+ working fine, but I think is no longer manufactured, it was replaced with new one model 4) - for home automation is not needed high power computation or high memory, is needed stability and reliability. This RPI will be the main server on which will be installed all the software. For SO I recommend to use raspbian
    Raspberry Pi zero W (W is from Wifi, there is simple Pi zero without wifi) - for bluetooth devices far away from server RPI

  https://www.raspberrypi.org/products/ 

    wifi smart relay - sonoff - https://sonoff.tech/ For start I recommend https://sonoff.tech/product/diy-smart-switch/basicr3/ or https://sonoff.tech/product/diy-smart-switch/basicr2/ ; https://sonoff.tech/product/diy-smart-switch/minir2/ ; or any other that you want. From China aliexpress.com sonoff basic is ~5euro ... and are very reliable . I do not recommend devices over RF433MHz because does not provide feedback, are not secured, they have long range, but.... I recommend switches over WiFi.
    Temperature Humidity  sensor Xiaomi Mijia LYWSD03MMC Bluetooth. Here are other sensors, maybe you find other that you need/like https://xiaomi-mi.com/sockets-and-sensors/  for example door sensors, motion sensors, water sensor against flooding https://xiaomi-pedia.com/xiaomi-mijia-lywsd03mmc-bluetooth-4-2-househo-for-only-15-99.html From Aliexpress I bought with ~5euro/pcs ...  
    wifi uC - NodeMCU with ESP8266 uC build with module ESP-12E and  CP2102. This design does not have bugs... what is on aliexpress are replicas and have bugs...   https://www.aliexpress.com/item/1005001804808377.html?spm=a2g0s.12269583.0.0.31d87964UFHusD  
    USB to TTL module needed to programm firmware in uC ESP8266 from sonoff - I recommend CP2102 - https://www.aliexpress.com/item/1005001510943320.html?spm=a2g0o.productlist.0.0.39e06cfaklWIN0&algo_pvid=b041ebae-f690-4050-b067-98ce3c8d377b&algo_expid=b041ebae-f690-4050-b067-98ce3c8d377b-0&btsid=0bb0622e16190295823888839e7823&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_ 
    wifi camera - ESP32cam - just for fun :) you can find free sw which can be handy - https://www.aliexpress.com/item/33017905531.html?spm=a2g0s.12269583.0.0.3af356ba7LMlOz 

I recommend to buy on few from Italy just to have them in few days, and the rest if you need more from aliexpress.

The list is long, think to what you want to do then on aliexpress.com you will find the device/module like :

    actuator for turning on/off heating radiator https://www.aliexpress.com/item/1005001334390676.html?spm=a2g0s.9042311.0.0.27424c4dXQFDvN
    ultrasonic sensors for distance measurement (i used it for water level check)
    ToF sensor for motion gestures
    RFID cards & modules for door access 
    PM sensors for air quality
    gas sensors for air quality or protection (like smoke / fire sensors) 
    and so on ... 

https://www.aliexpress.com/item/1005002286940374.html?spm=a2g0o.productlist.0.0.726736ddJV4Ami&algo_pvid=null&algo_expid=null&btsid=0bb0623916190284872975508e54a2&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_ 
https://www.aliexpress.com/item/32243897050.html?spm=a2g0o.productlist.0.0.726736ddJV4Ami&algo_pvid=null&algo_expid=null&btsid=0bb0623916190284872975508e54a2&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_ 

      displays like OLED, LCD   https://www.aliexpress.com/item/1005001950055514.html?spm=a2g0o.productlist.0.0.19517e90Le1Dic&algo_pvid=e59d6796-7e4d-400f-b053-909103fddd02&algo_expid=e59d6796-7e4d-400f-b053-909103fddd02-0&btsid=0bb0623216190289344375974e234d&ws_ab_test=searchweb0_0,searchweb201602_,searchweb201603_


- software for start :) 
https://www.raspberrypi.org/software/ - SO for RPI
https://www.domoticz.com/ - home automation integration - there are others but domoticz and home assistant are the most used/popular https://www.home-assistant.io/getting-started/ - I use domoticz because is much easy 
https://randomnerdtutorials.com/how-to-install-mosquitto-broker-on-raspberry-pi/  / https://mosquitto.org/download/ - MQTT broker which make the bridge between domoticz and tasmota firmware, but not only. MQTT is used by many devices/fw for communication.
https://github.com/arendst/tasmota/ - alternative firmware for sonoff and any module based on esp8266 which works with domoticz. The original fw from sonoff can not be integrated on domoticz. 
https://www.letscontrolit.com/wiki/index.php/ESPEasy - other ESP8266 firmware which works with domoticz
https://github.com/enesbcs/rpieasy - similar with espeasy but for Raspberry PI, any model. I use a sperate RPI zero W with RPIeasy to read temperature  sensor Xiaomi LYWSD03MMC Bluetooth 
https://pi-hole.net/ - best ad blocker ever - install on rpi then put in router at DNS server the ip from RPI and done. All devices which will be connected to that router is free of ads, except youtube vide ads... this is a must in home network ...

To avoid connecting monitor, mouse, keyboard to RPI it can be done like this ( create SSH empty file and in wpa_supplicant.conf put wifi ssid and password, these 2 file save them on SDcard after you copy the OS image). Then with Putty over ssh you can connect to RPI, activate VNC over command prompt then you can connect with VNC in visual mode.
- https://thepihut.com/blogs/raspberry-pi-tutorials/securely-logging-into-a-raspberry-pi-without-a-password 
- https://www.raspberrypi.org/documentation/remote-access/ssh/passwordless.md 

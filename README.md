# **ESP32 GAMEPAD**







### Návod:

  *Komponenty pro gamepad:*
  
 1x [**ESP32**](https://dratek.cz/arduino/1581-esp-32s-esp32-esp8266-development-board-2.4ghz-dual-mode-wifi-bluetooth-antenna-module.html?_gl=1*s3cekh*_up*MQ..&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE),
 1x [**Joystick s měřením analogové hodnoty X a Y**](https://dratek.cz/arduino/884-joystick-ps2.html?gad_source=1&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE) ,
 12x **Drátků (4x [Samice](https://dratek.cz/arduino/1214-40-x-m-f-dupont-kabel-20-cm.html?_gl=1*56f225*_up*MQ..&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE), 8x [Samci](https://dratek.cz/arduino/1063-eses-40-x-m-m-dupont-kabel.html?_gl=1*820k7h*_up*MQ..&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE))** ,
 4x **[Tlačítka](https://dratek.cz/arduino/51540-sada-25-tlacitek-s-klobouckem-pro-arduino.html?_gl=1*1upvtqs*_up*MQ..&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE)**,
	4x **[Resistory](https://dratek.cz/arduino/7660-rezistor-4k7-0.25-w-1.html)**,
1x **[Nepájivé pole](https://dratek.cz/arduino/121755-nepajive-pole-750-pinu.html?_gl=1*1jdeqs*_up*MQ..&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE)**
	
  
# **POSTUP**

# **1.** Zapojení tlačítek do nepájivého pole (pravé nožičky tlačítek do **-** a levé do **+**)

<sub>viz. foto:</sub>
	
![ZAPOJENI TLACITEK](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/673f655d-6d1d-4a5c-8fc1-4722c93829a9)

# **2.** Zapojení levé nožičky tlačítek s PINY (Zelená - G26, Červená - G25, Žlutá - G33, Modrá - G32) a u ESP napojení **GND** do (-) a **3V3** do (+)

<sub>viz. foto:</sub>

![tlacitka a esp](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/5a03ef0b-583b-4272-a161-6e6bc32fa1f8)


# **3.** Poslední krok je zapojení joysticku zapomocí **samic**  (X do G34, Y do G35, GND do - (GND) a VCC do +(3V3) )

<sub>viz. foto:</sub>

![JOYSTICK222](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/f19add8b-1371-415e-aedb-0623c0159e6c)




# **Hotový projekt:**


![FINALNI PROJEKT](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/e2c691ce-71f2-4abf-ab08-afd8b9206736)


## Poté stačí dát  kód do [Arduino IDE](https://www.arduino.cc/en/software) a stáhnout knihovnu BLE Gamepad
![KNIHOVNAAA](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/d080be79-55c4-4ea3-803c-ebe0c89b5582)


- Gamepad funguje s aplikacemi které podporují PS kontroler jako například Asphalt 8


<sub>[1.Zdroj a inspirace](https://www.instructables.com/DIY-ESP32-Bluetooth-GamePad-for-Android-PlayStatio/)</sub>
<sub>[2.Zdroj a inspirace](https://www.youtube.com/watch?v=zOuCZpH0Dqg)</sub>

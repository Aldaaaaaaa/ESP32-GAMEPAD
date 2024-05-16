# **ESP32 GAMEPAD**







### Návod:

  *Komponenty pro gamepad:*
  
- 1x [**ESP32**](https://dratek.cz/arduino/1581-esp-32s-esp32-esp8266-development-board-2.4ghz-dual-mode-wifi-bluetooth-antenna-module.html?_gl=1*s3cekh*_up*MQ..&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE)
- 1x [**Joystick s měřením analogové hodnoty X a Y**](https://dratek.cz/arduino/884-joystick-ps2.html?gad_source=1&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE) 
- 12x **Drátků (4x [Samice](https://dratek.cz/arduino/1214-40-x-m-f-dupont-kabel-20-cm.html?_gl=1*56f225*_up*MQ..&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE), 8x [Samci](https://dratek.cz/arduino/1063-eses-40-x-m-m-dupont-kabel.html?_gl=1*820k7h*_up*MQ..&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE))** 
- 4x **[Tlačítka](https://dratek.cz/arduino/51540-sada-25-tlacitek-s-klobouckem-pro-arduino.html?_gl=1*1upvtqs*_up*MQ..&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE)**
-	4x **[Resistory](https://dratek.cz/arduino/7660-rezistor-4k7-0.25-w-1.html)**
- 1x **[Nepájivé pole](https://dratek.cz/arduino/121755-nepajive-pole-750-pinu.html?_gl=1*1jdeqs*_up*MQ..&gclid=CjwKCAjwupGyBhBBEiwA0UcqaH6J5DjgpT64NVNzaj-crNZk7CDaJllbJJJvBpg1rio_UimbY8WeMBoCJT8QAvD_BwE)**
	
  
*Zapojení:*
    
**1.** Do nepájivého pole dáme 4 tlačítka a propojíme pravé nožičky tlačítek s (-) a levé s (+) (potom do - zapojime GND a do + 3v3 aby vše fungovalo)

<sub>viz. foto:</sub>
	
 ![TLACITKA](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/21047784-ff6b-43e4-84f2-8fc94fe3ccf2)

**2.** Zapojíme k levé nožičce tlačítek drátek s libovolným PINY (v našem případě: Zelená - G26, Červená - G25, Žlutá - G33, Modrá - G32) a nakonec u ESP napojíme **GND** do (-) a **3V3** do (+)

<sub>viz. foto:</sub>

 ![TLACITKA PLUS ESP](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/3e3c941c-41ad-49da-a1a5-01d5fd7468b8)


**3.** Nakonec zapojíme pomocí **samic** Joystick (X do G34, Y do G35, GND do (-) a VCC do (+) )

<sub>viz. foto:</sub>

![JOYSTICK](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/e347ee8d-a419-4ae2-8829-d32af1d5d0c1)



### Finální produkt vypadá nějak takto:


![CELY PROJEKT](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/737a2224-fc5c-4d7f-83d7-fbe50db9a0ac)


### Po složení stačí dát  kód do [Arduino IDE](https://www.arduino.cc/en/software), uploadnout a spustit

- Gamepad funguje s Asphalt 8 a ostatními hrami
- Výsvětlivky jsou v **kódu**

### Pro kód je potřeba pouze knihovna BLE Gamepad: 
![image](https://github.com/vojtamm69/gamepad-esp32/assets/169904042/d0045388-b5fc-4c4d-957b-8fa14dd30e42)

 



<sub>[1.Zdroj a inspirace](https://www.instructables.com/DIY-ESP32-Bluetooth-GamePad-for-Android-PlayStatio/)</sub>
<sub>[2.Zdroj a inspirace](https://www.youtube.com/watch?v=zOuCZpH0Dqg)</sub>

# ***ESP32 GAMEPAD***







### Návod:

  *Na gamepad potřebujeme:*
  
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

**2.** Zapojíme k levé nožičce tlačítek drátek s libovolným GPIO (v našem případě: Zelená - G26, Červená - G25, Žlutá - G33, Modrá - G32) a nakonec u ESP napojíme **GND** do (-) a **3V3** do (+)

<sub>viz. foto:</sub>

 ![TLACITKA PLUS ESP](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/3e3c941c-41ad-49da-a1a5-01d5fd7468b8)


**3.** Nakonec zapojíme pomocí **samic** Joystick (X do G34, Y do G35, GND do (-) a VCC do (+) )

<sub>viz. foto:</sub>

![JOYSTICK](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/e347ee8d-a419-4ae2-8829-d32af1d5d0c1)



### Finální produkt vypadá nějak takto:


![CELY PROJEKT](https://github.com/Aldaaaaaaa/ESP32-GAMEPAD/assets/170012616/737a2224-fc5c-4d7f-83d7-fbe50db9a0ac)


### Po složení stačí dát tento kód do [Arduino IDE](https://www.arduino.cc/en/software), uploadnout a spustit

- Gamepad funguje s Asphalt 8 a ostatními hrami
- Výsvětlivky jsou v **kódu**

### Pro kód je potřeba pouze knihovna BLE Gamepad: 
![image](https://github.com/vojtamm69/gamepad-esp32/assets/169904042/d0045388-b5fc-4c4d-957b-8fa14dd30e42)

 

```
// Knihovny: 
#include <Arduino.h>
#include <BleGamepad.h>
 
 
//ABXY TLACITKA:
 
#define X_BUTTON 26         // A (Pin G26) - Zeleny tlacitko
 
#define CIRCLE_BUTTON 25   // B (Pin G25) - Cerveny tlacitko
 
#define TRIANGLE_BUTTON 33  // Y  (Pin G33) - Zluty tlacitko 
 
#define SQUARE_BUTTON 32    // X  (Pin G32) - Modry tlacitko
 
 
// Levý joystick: 
#define LEFT_VRX_JOYSTICK 34 // Pohyb na souřadnici X (zleva do prava)
 
#define LEFT_VRY_JOYSTICK 35  // Pohyb na souřadnici Y (Zhora dolů)
 
/*
  Pravý joystick nepoužijeme, ale tady je kod pro něj:

  #define RIGHT_VRX_JOYSTICK 0
 
  #define RIGHT_VRY_JOYSTICK 0
*/

//nastaveni tlacitek:
int buttonsPins[NUM_BUTTONS] = {X_BUTTON, CIRCLE_BUTTON, TRIANGLE_BUTTON, SQUARE_BUTTON,
 
                          R1_BUTTON, R2_BUTTON, L1_BUTTON, L2_BUTTON,
 
                          START_BUTTON, SELECT_BUTTON, PS_BUTTON,
 
                          R3_BUTTON, L3_BUTTON};
 
//nastaveni pro ruzne zarizeni:

int androidGamepadButtons[NUM_BUTTONS] = {1, 2, 3, 4, 8, 10, 7, 9, 12, 11, 13, 15, 14};
 
int PS1GamepadButtons[NUM_BUTTONS] = {2, 3, 4, 1, 6, 8, 5, 7, 10, 9, 13, 12, 11};
 
int PCGamepadButtons[NUM_BUTTONS] = {1, 2, 4, 3, 6, 8, 5, 7, 10, 9, 0, 12, 11};
 
 
uint16_t leftVrxJoystickLecture = 0;
 
uint16_t leftVryJoystickLecture = 0;
 
uint16_t rightVrxJoystickLecture = 0;
 
uint16_t rightVryJoystickLecture = 0;
 
uint16_t leftVrxJoystickValue = 0;
 
uint16_t leftVryJoystickValue = 0;
 
uint16_t rightVrxJoystickValue = 0;
 
uint16_t rightVryJoystickValue = 0;
 
 
typedef enum{ANDROID, PS1, PC} GamepadModes;
 
GamepadModes gamepadMode = ANDROID;
 
 
BleGamepad bleGamepad("Android Gamepad", "ESP32 Home");
 
BleGamepadConfiguration bleGamepadConfig;  
 
// Setup kod:
void setup() {

  delay(1000);
 
  Serial.begin(115200);
 
  for(int i=0; i<NUM_BUTTONS; i++){
 
    pinMode(buttonsPins[i], INPUT_PULLUP);
 
  }
 
  bleGamepadConfig.setAutoReport(false);
 
  bleGamepadConfig.setControllerType(CONTROLLER_TYPE_GAMEPAD); 
 
  bleGamepadConfig.setVid(0xe502);
 
  bleGamepadConfig.setPid(0xabcd);
 
  bleGamepadConfig.setHatSwitchCount(4);
 
  bleGamepad.begin(&bleGamepadConfig);
 
}

// Hlavní část kodu která se bude opakovat: 

void loop() {
 
  if(bleGamepad.isConnected()){
 
    
 
    leftVrxJoystickLecture = analogRead(LEFT_VRX_JOYSTICK);
 
    leftVryJoystickLecture = analogRead(LEFT_VRY_JOYSTICK);
 
    rightVrxJoystickLecture = analogRead(RIGHT_VRX_JOYSTICK);
 
    rightVryJoystickLecture = analogRead(RIGHT_VRY_JOYSTICK);
 
    
 
    leftVrxJoystickValue = map(leftVrxJoystickLecture, 4095, 0, 0, 32737);
 
    leftVryJoystickValue = map(leftVryJoystickLecture, 0, 4095, 0, 32737);
 
    rightVrxJoystickValue = map(rightVrxJoystickLecture, 4095, 0, 0, 32737);
 
    rightVryJoystickValue = map(rightVryJoystickLecture, 0, 4095, 0, 32737);
 
   
  // Mody gamepadu: 
    switch(gamepadMode){
 
      case ANDROID:
 
        for(int i=0; i<NUM_BUTTONS; i++){
 
          if(!digitalRead(buttonsPins[i])){
 
              bleGamepad.press(androidGamepadButtons[i]);  
 
          }
 
          else{
 
              bleGamepad.release(androidGamepadButtons[i]);    
 
          }
 
          joysticksHandlerForMobile(leftVrxJoystickValue, leftVryJoystickValue, rightVrxJoystickValue, rightVryJoystickValue);
 
        }
 
        break;
 
      case PS1:
 
        for(int i=0; i<NUM_BUTTONS; i++){
 
          if(!digitalRead(buttonsPins[i])){
 
            bleGamepad.press(PS1GamepadButtons[i]);    
 
          }
 
          else{
 
            bleGamepad.release(PS1GamepadButtons[i]);      
 
          }
 
          joysticksHandlerForMobile(leftVrxJoystickValue, leftVryJoystickValue, rightVrxJoystickValue, rightVryJoystickValue);
 
        }
 
        break;
 
        case PC:
 
          for(int i=0; i<NUM_BUTTONS; i++){
 
            if(!digitalRead(buttonsPins[i])){
 
              bleGamepad.press(PCGamepadButtons[i]);
 
            }
 
            else{
 
              bleGamepad.release(PCGamepadButtons[i]);
 
            }
 
            joysticksHandlerForPC(leftVrxJoystickValue, leftVryJoystickValue, rightVrxJoystickValue, rightVryJoystickValue);
 
          }
 
          break;
 
    }
 
    bleGamepad.sendReport();
 
  }
 
}
//nastaveni pro telefon: 
void joysticksHandlerForMobile(uint16_t leftVrx, uint16_t leftVry, uint16_t rightVrx, uint16_t rightVry){
 
  bleGamepad.setLeftThumb(leftVrx, leftVryJoystickValue);
 
  bleGamepad.setRightThumb(rightVrxJoystickValue, rightVryJoystickValue);  
 
}
//nastaveni pro PC:
void joysticksHandlerForPC(uint16_t leftVrx, uint16_t leftVry, uint16_t rightVrx, uint16_t rightVry){
 
  bleGamepad.setX(leftVrxJoystickValue);
 
  bleGamepad.setY(leftVryJoystickValue);
 
  bleGamepad.setZ(rightVrxJoystickValue);
 
  bleGamepad.setRX(rightVryJoystickValue);
 
}
```

<sub>[Zdroj a inspirace](https://www.instructables.com/DIY-ESP32-Bluetooth-GamePad-for-Android-PlayStatio/)</sub>

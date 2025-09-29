# Unterrichtsprojekt: Temperaturmessung mit PT100 und 4-Leiter-Schaltung
Das Projekt "Temperaturmessung mit PT100 in 4-Leiterschaltung" ist im Rahmen meines Unterrichts für Elektroniker für Geräte und Systeme an der Friedrich-Ebert-Schule in Esaslingen entstanden. Es werden Lerninhalte aus mehreren Lernfeldern vertieft, gefestigt und wiederholt. Einzelne Teile des Projektes lassen sich am 
Dazu zählen
Temperaturmessung gehört zu den Standardanwendung in der Mess-, Steuer- und Regelungstechnik. 
<img src="https://github.com/user-attachments/assets/c56eee07-a990-43ef-b775-0674f715a58f" alt="Arduino-Carrier-Board mit ATMega3238PXPlainedMini und Temperaturmessplatine" width="500">


### **Was wird benötigt?**
**Software**
+ <a href="https://www.multisim.com/">MultisimLive-Account</a> (kostenlos oder Premium) oder anderes Simulationsprogramm (z.B. LTSpice).
+ MS-Excel oder gleichwertige Tabellenkalkulation.
+ <a href ="https://www.microchip.com/en-us/tools-resources/develop/microchip-studio">MicrochipStudio (IDE)</a>
 mit <a href ="https://github.com/feslehrer/FA205.git">FA205-Bibliotheken</a>
+ oder <a href="https://www.arduino.cc/en/software/?_gl=1*sbuq35*_up*MQ..*_ga*MjU4NDg3MTE4LjE3NTg3NDcyOTA.*_ga_NEXN8H46L5*czE3NTg3NDcyOTAkbzEkZzAkdDE3NTg3NDcyOTAkajYwJGwwJGgxNDgzNTc4MjM2#ide">Arduino (IDE)</a>
mit FA205-Bibliotheken für <a href="https://github.com/feslehrer/FA205-ESP32.git">ESP32</a>
oder <a href="https://github.com/feslehrer/FA205_Library_for_Arduino.git">ArduinoUno/Nano</a>
</br>**Hardware**
+ <a href="https://ase-schlierbach.de/produkt/arduino-carrier-board_fertigprodukt/">Arduino-Carrier-Board</a> oder
  gleichwertiges Arduino-Board mit Uno-Formfaktor und LC-Display.
+ ATmega328PXplainedMini-Controllerboard für MicrochipStudio oder Arduino Uno/Nano mit ATmega328P-Controller
+ (Alternativ: <a href="https://ase-schlierbach.de/produkt/esp32-carrier-board-v1-5/">ESP32-Carrier-Board mit ESP32PicoKit</a>)
+ <a href="https://ase-schlierbach.de/kontakt/">PT100-Temperaturmess-Platine</a> (Anfrage Formular)
<img src="https://github.com/user-attachments/assets/25e51c46-99d9-4df9-ba7d-5bb1d87641d1" alt="PT100-Messplatine" width="300">


### Weitere FA205-Implementierungen
Implementierungen sind für folgende Plattformen verfügbar: 
+ ATmega328P-Xplained Mini mit Microchip-Studio: 
+ ArduinoUno/Nano mit ATmega328P und ArduinoIDE: https://github.com/feslehrer/FA205_Library_for_Arduino.git

## Installation
+ Auf GitHub Resource: https://github.com/feslehrer/FA205-ESP32.git
<br>Download der Bibliothek als Zip-Datei (<>Code --> Download Zip)
+ In der Arduino-IDE auf **Sketch --> Bibliothek einbinden --> .Zip-Bibliothek hinzufügen...**
+ Im Sketch muss **controller.h** inkludiert werden.
<br>Beispiel: Blink-Sketch mit FA205-Funktionen
```c
#include "controller.h"     // FA205-Bibliotheken einbinden

void setup(void)
{
  bit_init(PORTx,7,OUT);    // PORTx,7 als Ausgang initialisieren
}

void loop(void)
{
  bit_write(PORTx,7,0);      // PORTx,7 --> 0
  delay_ms(500);             // 500ms warten
  bit_write(PORTx,7,1);      // PORTx,7 --> 1
  delay_ms(500);             // 500ms warten
}
```
**Anmerkung:** Im Boardmanager muss das ESP32 Boardpackage (ab Version 3.x) installiert sein. Als Board wird **ESP32 PICO-D4** ausgewählt.
## Implementierung für Arduino-IDE
Die Richtlinien-Funktionen mussten für die Verwendung in der Arduino-IDE leicht modifiziert werden. Die Änderungen sind im einzelnen:
#### 8-Bit-Ports (Byte): 
+ Da der ESP32 keine 8 Bit-Ports mehr besitzt, wurden 8 Pins zum **PORTx** zusammengefasst, damit die 8 LEDs auf dem ESP32-Carrier-Board mit einem einzigen Byte-Zugriff geschrieben werden können. 8 weitere Pins wurden zum **PORTy** zusammengefasst. Hier befinden sich u.a. die 4 Taster des ESP32-Carrier-Boards (siehe unten).
#### Zeichenketten: 
+ Abweichend von der Definition in der Technischen Richtlinie müssen für die Funktionen `lcd_print()` und `rs232_print()` konstante Zeichenketten vom Typ **char** und nicht **uint8_t** übergeben werden.
  ```c
  char text[] = "Hallo Welt";     // Definition als char und nicht uint8_t
  
  lcd_print ( text );
  rs232_print ( text );
  ```
  alternativ:
  ```c
  lcd_print ( "Hallo Welt" );
  ```

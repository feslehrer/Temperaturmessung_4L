# Unterrichtsprojekt: Temperaturmessung mit PT100 in 4-Leiter-Schaltung
Das Projekt "Temperaturmessung mit PT100 in 4-Leiterschaltung" ist als Lernfeld-übergreifendes Unterrichtsprojekt für **Elektroniker für Geräte und Systeme** entstanden. Das Projekt lässt sich in Teilgebiete gleidern und auch zeitlich über die Fachstufe verteilen. Es werden Lerninhalte aus mehreren Lernfeldern geübt, vertieft und lernwirksam gefestigt:
+ Temperatursensor PT100 (Exemplarisch für Temperaturabhängigkeit von Metallen)
+ Operationsverstärker Grundschaltungen (Invertierender/Nichtinvertierender Verstärker, Subtrahierverstärker, Instrumentenverstärker, ...)
+ Messwertverarbeitung mit Excel (Formeln, Diagramme)
+ Sensorschaltungen (Brückenschaltung, Konstantstromquelle, 2-,3- und 4-Leiterschaltung)
+ Schaltungsabgleich (Simulation/Real)
+ Erstellen eines Abgleichprogramms mit Technischer Richtlinie FA205

Die Lösungen und fertigen Programmcodes sind in der Passwort-geschützten Datei **docx.zip** enthalten. Als Lehrer kontaktieren Sie mich bei Bedarf über: rahm@fes-es.de

#### Schaltungsbeschreibung
Die 4-Leiterschaltung besteht im wesentlichen aus einer Stromquelle, die den Sensor über 2 Leitungen mit einem temperaturunabhängigen, konstanten Messstrom versorgt. Über die beiden Spannungsabgriffe am PT100 wird dann eine lineare Messspannung abgegriffen, die nur noch vom temperaturabhängigen Widerstand selbst abhängt. Der Verstärker mit hochohmigem Eingang sorgt dafür, dass die Spannung möglichst gut auf den Eingangsspannungsbereich des AD-Wandlers angepasst wird. 

<img width="600" alt="4-Leiterschaltung. Schema" src="https://github.com/user-attachments/assets/7263ae91-febd-4821-a0ea-012f24b9749e" />

Der Signalfluss des Analogteils lässt sich folgendermaßen mittels Blockschaltbild darstellen:

<img width="600" alt="Blockschaltbild der Messkette" src="https://github.com/user-attachments/assets/782025e0-17fb-40f1-b05c-de2a26e3d6ca" /><br>
Die lineare Widerstandskennlinie über den gesamten Messbereich von -25°C ... 100°C wird in eine lineare Spannungsänderung transformiert und in der ersten Verstärkerstufe um den Faktor 5 verstärkt. Anschließend wird ein Offset abgezogen, bevor in der zweiten Verstärkerstufe die Anpassung an den Messbereich des AD-Wandlers erfolgt.

### **Was wird benötigt?**
<img src="https://github.com/user-attachments/assets/c56eee07-a990-43ef-b775-0674f715a58f" alt="Arduino-Carrier-Board mit ATMega3238PXPlainedMini und Temperaturmessplatine" width="500">

#### **Software**
+ <a href="https://www.multisim.com/">MultisimLive-Account</a> (bis 09.2026 abgekündigt) oder anderes Simulationsprogramm (z.B. LTSpice).
+ MS-Excel oder gleichwertige Tabellenkalkulation.
+ <a href ="https://www.microchip.com/en-us/tools-resources/develop/microchip-studio">MicrochipStudio (IDE)</a>
 mit <a href ="https://github.com/feslehrer/FA205.git">FA205-Bibliotheken</a>
+ oder <a href="https://www.arduino.cc/en/software/?_gl=1*sbuq35*_up*MQ..*_ga*MjU4NDg3MTE4LjE3NTg3NDcyOTA.*_ga_NEXN8H46L5*czE3NTg3NDcyOTAkbzEkZzAkdDE3NTg3NDcyOTAkajYwJGwwJGgxNDgzNTc4MjM2#ide">Arduino (IDE)</a>
mit FA205-Bibliotheken für <a href="https://github.com/feslehrer/FA205-ESP32.git">ESP32</a>
oder <a href="https://github.com/feslehrer/FA205_Library_for_Arduino.git">ArduinoUno/Nano</a>

#### **Hardware**
+ <a href="https://ase-schlierbach.de/produkt/arduino-carrier-board_fertigprodukt/">Arduino-Carrier-Board</a> oder
  gleichwertiges Arduino-Board mit Uno-Formfaktor und LC-Display.
+ ATmega328PXplainedMini-Controllerboard für MicrochipStudio oder Arduino Uno/Nano mit ATmega328P-Controller
+ (Alternativ: <a href="https://ase-schlierbach.de/produkt/esp32-carrier-board-v1-5/">ESP32-Carrier-Board mit ESP32PicoKit</a>)
+ <a href="https://ase-schlierbach.de/kontakt/">PT100-Temperaturmess-Platine</a> (Anfrage Formular)
<img src="https://github.com/user-attachments/assets/25e51c46-99d9-4df9-ba7d-5bb1d87641d1" alt="PT100-Messplatine" width="300">

### **Arbeitsaufträge**
+ Sensor
1. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/0_Sensor_PT100/1_2_1_Temperaturmessung_mit_PT100_FTM1.pdf">PT100-Sensor</a>
2. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/0_Sensor_PT100/1_8_1_Tempabhaengigkeit_von_Metallen_LF1.pdf">Kennlinienaufnahme (Versuch)</a>
+ Schaltungstheorie
3. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/1_Schaltungstheorie/1_1_PT100_Sensor_mit_Spannungsteiler.pdf">PT100-Sensor mit Spannungsteiler</a> Simulation: <a href="https://www.multisim.com/content/ztNrqoLsVMBNv6kWRXQJ3Y/1_1_pt100-sensor_spannungsteiler/open/">MultisimLive</a>
4. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/1_Schaltungstheorie/1_2_PT100_Sensor_mit_Spannungsteiler_und_OPV.pdf">Spannungsteiler mit OPV</a> Simulation: <a href="https://kurzelinks.de/pd39">MultisimLive</a>
5. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/1_Schaltungstheorie/1_3_1_Exkurs_Subtrahierverstaerker.pdf">Exkurs Subtrahierverstärker</a> Simulation: <a href="https://kurzelinks.de/od7v">MultisimLive</a>
6. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/1_Schaltungstheorie/1_3_2_1_PT100_Sensor_mit_Brueckenschaltung_ohne_RLtg.pdf">Sensor in Brückenschaltung</a> Simulation: <a href="https://kurzlinks.de/k2ep">MultisimLive</a>
7. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/1_Schaltungstheorie/1_3_2_PT100_Sensor_mit_Brueckenschaltung.pdf">Brückenschaltung mit Leitungswiderständen</a> Simulation: <a href="https://kurzelinks.de/1xkf">MultisimLive</a>
8. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/1_Schaltungstheorie/1_4_1_Exkurs_Instrumentenverstaerker.pdf">Exkurs: Instrumentenverstärker</a> Simulation: <a href="https://kurzelinks.de/ydv8">MultisimLive</a>
9. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/1_Schaltungstheorie/1_4_2_PT100_Sensor_mit_Instrumentenverstaerker.pdf">Brückenschaltung mit Instrumentenverstärker</a> Simulation: <a href="https://kurzelinks.de/4v5m">MultisimLive</a>
10. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/1_Schaltungstheorie/1_5_1_PT100_Sensor_in_Vierleiterschaltung.pdf">Sensor in 4-Leiterschaltung</a> Simulation: <a href="https://kurzelinks.de/ipss">MultisimLive</a>
11. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/1_Schaltungstheorie/1_5_2_PT100_Sensor_in_Vierleiterschaltung_mit_2_INA.pdf">4-Leiterschaltung mit Offset-Kompensation</a> Simulation: <a href="https://kurzelinks.de/m65m">MultisimLive</a>
12. <a href="https://github.com/feslehrer/Temperaturmessung_4L/blob/main/1_Schaltungstheorie/1_5_3_Konstantstromquelle_mit_LM317.pdf">Konstantstromquelle mit LM317</a> Simulation: <a href="https://kurzelinks.de/vvo9">MultisimLive</a>

12. <a href=""></a> Simulation: <a href="">MultisimLive</a>



@rah, 2025.09.29

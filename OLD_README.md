### **FUSEE UF2**

Interner, Mikrocontroller-basierter Payload-Loader/-Booter für die Nintendo Switch.

Bestehend aus:

Einer UNGEPATCHTEN Nintendo Switch v1 Konsole

Einem SAMD21-Gerät (Adafruit Trinket / Gemma / ItsyBitsy usw.)

Part 1 dieser Software: Der SWITCHBOOT-RCM-Bootloader, der – sobald der Chip in deiner Konsole verbaut ist – den RCM-Modus auslöst.

Part 2: Die eigentliche Software zum Laden des Payloads sowie die Chip-Einstellungen...

### **Features**

Ich war über 2 Jahre lang inaktiv, daher wird es eine Weile dauern, bis ich hier wieder alles auf dem aktuellen Stand habe. Auf meinen alten Account bei GBATemp habe ich keinen Zugriff mehr.

### **Fusee_UF2 V9 BETA Änderungen**

Neue Code-Basis

* Stark vereinfacht. Nur noch 6 Chip-Optionen
* Schnelleres Booten – Vorab-Prüfung (Pre-Checking) / Pre-Caching des Payloads während der Bootlogo-Anzeige
* Wahlweise Nutzung von Langdruck- (Long-press) oder Mehrfachdruck-Optionen (Multiple-press) für die Chip-Einstellungen
* Batterie-Icon verbessert
* Weitere Modifikationen an der Basis
* Unterstützung für Bootlogo-Bitmaps aus Geschwindigkeitsgründen entfernt
* Arduino-Code bereinigt
* Schau nach dem Flashen in den „About“-Bereich (Info) im Menü für weitere Details.

### **Fusee_UF2 V7 Änderungen**

#### **Vereinfachte Bedienung:**

Sucht im Hauptverzeichnis (Root) der SD-Karte nach `fusee.bin` und bootet diese.

Wird sie nicht gefunden, sucht der Chip nach `bootloader/update.bin` (von SDSetup.com).

Halte VOL- gedrückt, um `fusee.bin` zu überspringen und Hekate vom Standardpfad (`bootloader/update.bin`) zu starten. Im Menü anpassbar.

„Payload(x)“-Funktion entfernt. Sinnlos... Führte nur dazu, dass versehentlich auf einen falschen Payload gewechselt wurde.

Halte VOL+ gedrückt, um das Konfigurationsmenü zu öffnen.

#### **Es sind jetzt nur noch 3 Aktionen direkt am Chip nötig, alle erreichbar durch langes Drücken von VOL+.**

**Erste Option:** AutoRCM umschalten. Lass die Taste beim ersten LANGEN Aufblinken los... Oder

weiter gedrückt halten bis:

**ZWEIMALIGES BLINKEN:** Lass die Taste an einem beliebigen Punkt während des zweimaligen Blinkens los. Helligkeit der RGB-LED (0-250). Drücke VOL+ bei der gewünschten Helligkeitsstufe. Oder

weiter gedrückt halten bis:

DREIMALIGES BLINKEN + HALTEN BIS ZUM LANGSAMEN AN- UND AUSBLINKEN – (gleichmäßiges Blinken (Weiß bei Adafruit-Boards)): Chip-EEPROM-Reset + SAMD21-Update-Modus beim nächsten Neustart. Kehrt bei darauffolgenden Neustarts wieder in den Normalzustand zurück.

### **Änderungen**

Schnellere Bootzeit. Schnellere Animation (kann im Hex-Editor leicht deaktiviert werden, oder lade einfach die entsprechende UF2-Binary herunter).

Bildschirm-Dimmung / Bildschirmschoner (wenn die Variable für den Bildschirmschoner auf 0 steht, dimmt das Display automatisch ab, um den Akku zu schonen).

Option zum Neugenerieren der SXOS-Lizenz entfernt, da SXOS tot ist.

Grüner Text, weil es schicker aussieht.

Option für „Reboot to Bootloader“ hinzugefügt.

„About“-Option (Info) hinzugefügt – lies sie dir mal durch.

Ungenutzten Ballast aus der alten Hekate-Basis gelöscht – Kleinere Binary-Größe (wirst du nicht direkt bemerken, da UF2-Dateien immer 512 KB groß sind).

Bootlogo-Unterstützung und -Manager. Bis zu 2 Bootlogos ansehen / auswählen:

Für **Atmosphère:** Leg deine BMP-Datei irgendwo auf der SD-Karte ab und wähle sie direkt in der App inklusive Vorschau aus. Oder platziere sie direkt unter `atmosphere/splash.bmp`.

Für **Hekate:** Leg deine BMP-Datei irgendwo auf der SD-Karte ab und wähle sie direkt in der App inklusive Vorschau aus. Oder platziere sie direkt unter `bootloader/bootlogo.bmp`.

Die Bootlogos werden abhängig vom genutzten Payload geladen. Beispiel: Wenn `fusee.bin` nicht genutzt wird, wird `bootloader/bootlogo.bmp` gerendert.

Wenn `fusee.bin` genutzt wird, wird `splash.bmp` gerendert; ist `fusee.bin` zwar vorhanden, wird aber durch Gedrückthalten von VOL- übersprungen (um Hekate zu booten), wird stattdessen `bootlogo.bmp` gerendert.

### **Bugfixes usw...**

#### **Bugs aus dem letzten öffentlichen UF2-Release:**

Die „Payload(x)“-Funktion konnte auf einen ungenutzten Payload-„Slot“ gestellt werden, was für Verwirrung sorgte, wenn versehentlich ein ungültiger Payload „ausgewählt“ wurde.

Billige Ladegeräte (z. B. von Venom) liefern keinen so sauberen Strom wie das originale Nintendo-Netzteil (Stock). Das führte zu zufälligen Neustarts, Verbindungsabbrüchen bei den Joy-Cons und Problemen mit der Lautstärkeregelung.

Schlechte, aussetzende Ladeverbindungen der Joy-Cons führten ebenfalls zu zufälligen Neustarts. Das lag daran, dass der USB-Strap durch nicht ganz saubere Joy-Con-Pins ausgelöst wurde. Halte die Pins sauber!

Zu viele ungenutzte Funktionen waren einfach über das Drücken von VOL+ erreichbar. Das war verwirrend für die Nutzer.

#### **Fixes in diesem Release:**

PayloadX entfernt. Dafür gibt es wirklich keinen Bedarf mehr.

Jetzt sind nur noch 3 Aktionen am Chip nötig, alle erreichbar über langes Drücken von VOL+.

Code für den USB-Strap überarbeitet, sodass ein Wakeup-Interrupt nur noch unter folgenden Bedingungen gesetzt wird:

* ChipRCM (Chip-basiertes AutoRCM) ist aktiviert
* Der Payload-Start (Launch) ist fehlgeschlagen (wie es passiert, wenn die Konsole per USB am PC hängt)
* USB-Spannung wird erkannt (wird eventuell nicht ausgelöst, wenn der Akku bei 100 % ist und das Ladegerät gerade keinen Strom liefert)
* Werte für den USB-Strap werden nicht mehr im EEPROM gespeichert

#### **Ich hätte noch viel mehr Funktionen einbauen können, aber ich möchte, dass es weiterhin auf einen SAMD21E17 (128 KB) passt**

### **Einbaudiagramme**

**Unterstützte Mikrocontroller:**

* Trinket M0
* RCMX86
* Rebug
* Gemma M0
* ItsyBitsy M0
* Feather M0

### [Diagramme << Hier klicken](https://github.com/glitched-nx/FUSEE_UF2_SUITE/tree/master/Install%20Diagrams)

#### [TidyMemloader - einfach per Drag & Drop auf die SD-Karte ziehen und vergessen. Ermöglicht USB-Zugriff ohne Hekate/Nyx](https://github.com/glitched-nx/FUSEE_SUITE/tree/master/Fusee-Suite/Tidy_Memloader)

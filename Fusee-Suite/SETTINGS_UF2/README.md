## Dies sind Einstellungsdateien für alle Versionen von Fusee_UF2. Öffne einfach dein UF2-Laufwerk und ziehe die gewünschte Datei per Drag & Drop darauf. Dadurch wird deine aktuelle Firmware nicht überschrieben, es werden lediglich die Werte im virtuellen EEPROM geändert. Natürlich kannst du diese Einstellungen wie gewohnt auch weiterhin im laufenden CFW-Betrieb über die VOL+ Taste anpassen.

## Du kannst das EEPROM in den VOL+ Einstellungen zurücksetzen oder einfach die Datei `BLANK.UF2` flashen, um die Standardwerte wiederherzustellen.

## Namenskonvention

Der Dateiname besteht aus 5 „Abschnitten“...

#### SETTINGS _ (FARBE) _ (STRAPS) _ (VERFÜGBARE BOOT-OPTIONEN) _ (BOOT-PRIORITÄT) _ (METHODE ZUR EINSTELLUNGSÄNDERUNG). UF2

#### Abschnitt 1: Farbe des Bootlogos – Schwarz (Black) oder Rot (Red) (B / R)

#### Abschnitt 2: Vorab erkannte Strap-Belegung. J - Joy-Con, V - Volume, U - USB... z. B. JVU (alle Straps vorregistriert) oder JV (alle außer dem USB-Strap registriert) usw.

#### Abschnitt 3: (B1 - Dual-Boot / ChipRCM) / (B2 - Dual-Boot / FailsafeRCM) / (B3 - Dual-Boot / ChipRCM / FailsafeRCM)

#### Abschnitt 4: Vorausgewählte Boot-Option. 1 = Dual-Boot, 2 = ChipRCM, 3 = FailsafeRCM

#### Abschnitt 5: Langdruck / Long-press (LP), Mehrfachdruck / Multiple-press (MP) oder Bootloader-Press (BP) – Long-press ist für Boards mit verbauter LED gedacht. Halte die Taste einfach lange gedrückt und lass sie im richtigen Moment los, um eine Einstellung zu ändern. Multiple-press stellt dir einen „Assistenten“ im Menü zur Verfügung – ideal für Installationen OHNE LED.

#### Beispiel 1: SETTINGS_B_JVU_B1_2_LP.UF2

* B = SCHWARZ (BLACK)
* JVU = ALLE STRAPS VORAUSGEWÄHLT (PRE-CHECKED)
* B1 = DUAL-BOOT / CHIP_RCM VERFÜGBAR
* 2 = OPTION 2 (CHIP_RCM – bzw. AUTORCM AUSGEWÄHLT)
* LP = ANPASSUNG DER ONBOARD-CHIP-EINSTELLUNGEN ÜBER LANGDRUCK DER LAUTSTÄRKETASTE (VOL+)

#### Beispiel 2: SETTINGS_R_JVU_B2_1_BP.UF2 (ideal für Kinderkonsolen)

* R = ROT (RED)
* JVU = ALLE STRAPS VORAUSGEWÄHLT (PRE-CHECKED)
* B2 = DUAL-BOOT / FAILSAFE_RCM VERFÜGBAR
* 1 = OPTION 1 (DUAL-BOOT AKTUELL AUSGEWÄHLT)
* BP = ÜBER VOL+ IST NUR DER BOOTLOADER-MODUS AUFRUFBAR. ERREICHBAR DURCH 20 SEKUNDEN LANGES GEDRÜCKTHALTEN VON VOL+

#### Beispiel 3: SETTINGS_R_JVU_B3_3_MP.UF2 (ideal für „blinde“ Installationen ohne Reset-Taster oder LED)

* R = ROT (RED)
* JVU = ALLE STRAPS VORAUSGEWÄHLT (PRE-CHECKED)
* B3 = DUAL-BOOT / CHIP_RCM / FAILSAFE_RCM VERFÜGBAR
* 3 = OPTION 3 (FAILSAFE_RCM AKTUELL AUSGEWÄHLT)
* MP = CHIP-EINSTELLUNGEN ÜBER MEHRFACHDRUCK (TIMEOUT NACH 30 SEKUNDEN)

#### Beispiel 4: SETTINGS_B_J_B1_1_LP.UF2 (Anwendungsbeispiel – Jemand, der lediglich den Joy-Con-Strap angelötet hat)

* B = SCHWARZ (BLACK)
* J = Nur Joy-Con-Strap vorausgewählt (der einzige Strap, der bei diesem Nutzer verbaut ist)
* B1 = DUAL-BOOT / CHIP_RCM VERFÜGBAR
* 2 = OPTION 2 (CHIP_RCM – bzw. AUTORCM AUSGEWÄHLT – DIE KONSOLE WÜRDE AUFGRUND DER FEHLENDEN STRAPS DENNOCH IMMER IM DUAL-BOOT STARTEN)
* LP = ANPASSUNG DER ONBOARD-CHIP-EINSTELLUNGEN ÜBER LANGDRUCK DER LAUTSTÄRKETASTE – SPIELT HIER KAUM EINE ROLLE, DA OHNE VOL+ STRAP OHNEHIN NICHT ERREICHBAR

## Eigene Datei erstellen? Ganz einfach...
![settingsgraphic](https://user-images.githubusercontent.com/41282276/172249882-cffa847a-9cb9-408e-9b36-6d4df604d758.jpg)

---
---

## These are settings files for all versions of Fusee_UF2. Just open your UF2 drive and drag / drop. This will not overwrite your current firmware, this merely changes virtual EEPROM settings. You can of course use VOL+ to change these settings when CFW is running, as always.

## You can "reset" the EEPROM in the VOL+ settings, or just flash BLANK.UF2 for some default values.

## Naming Convention

The filename has 5 "sections"...

#### SETTINGS _ (COLOUR) _ (STRAPS) _ (BOOT OPTIONS AVAILABLE) _ (BOOT PRIORITY) _ (SETTINGS-CHANGE-METHOD). UF2

#### Section 1: Bootlogo colour - Black or Red (B / R)

#### Section 2: Strap presence prechecked. J - Joycon, V - Volume, U - USB... eg JVU (all straps pre-registered) or JV (all but USB strap registered) etc etc

#### Section 3: (B1 - Dualboot / ChipRCM) / (B2 - Dualboot / FailsafeRCM) / (B3 - Dualboot / ChipRCM / FailsafeRCM)

#### Section 4: Boot option preselected. 1 = Dual-boot, 2 - ChipRCM, 3 - FailsafeRCM

#### Section 5: Long-press(LP), Multiple-press(MP) or Bootloader Press (BP)- Long-press is for LED fitted devices. Just long-press and let go to change a setting. Multiple-press gives you an "assistant" in the menu, handy for people WITHOUT LED.


#### Example 1: SETTINGS_B_JVU_B1_2_LP.UF2
- B = BLACK
- JVU = ALL STRAPS PRE_CHECKED
- B1 = DUAL-BOOT / CHIP_RCM AVAILABLE
- 2 = OPTION 2 (CHIP_RCM - aka AUTORCM SELECTED)
- LP = LONG-PRESS VOLUME ONBOARD CHIP SETTINGS ADJUSTMENT


#### Example 2: SETTINGS_R_JVU_B2_1_BP.UF2 (ideal for childrens console)
- R = RED
- JVU = ALL STRAPS PRE_CHECKED
- B2 = DUAL-BOOT / FAILSAFE_RCM AVAILABLE
- 1 = OPTION 1 (DUAL-BOOT CURRENTLY SELECTED)
- BP = BOOTLOADER ONLY OPTION SETTABLE WITH VOL+. ACCESSIBLE WITH 20 SECOND LONG_PRESS ON VOL+


#### Example 3: SETTINGS_R_JVU_B3_3_MP.UF2 (ideal for blind installations (No reset switch or LED)
- R = RED
- JVU = ALL STRAPS PRE_CHECKED
- B3 = DUAL-BOOT / CHIP_RCM / FAILSAFE_RCM AVAILABLE
- 3 = OPTION 3 (FAILSAFE_RCM CURRENTLY SELECTED)
- MP = MULTIPLE-PRESS CHIP SETTINGS (TIMES OUT AFTER 30 SECONDS)

#### Example 4: SETTINGS_B_J_B1_1_LP.UF2 (Example Use-case - Someone with only Joycon strap attached)
- B = BLACK
- J = Joycon Only Prechecked (Only strap fitted for this chap)
- B1 = DUAL-BOOT / CHIP_RCM AVAILABLE
- 2 = OPTION 2 (CHIP_RCM - aka AUTORCM SELECTED - CONSOLE WOULD ALWAYS BE DUAL-BOOT, DUE TO LACK OF STRAPS FITTED)
- LP = LONG-PRESS VOLUME ONBOARD CHIP SETTINGS ADJUSTMENT - MATTERS LITTLE AS WITH NO VOL+ STRAP, NOT ACCESSIBLE

## Make your own? Easy...
![settingsgraphic](https://user-images.githubusercontent.com/41282276/172249882-cffa847a-9cb9-408e-9b36-6d4df604d758.jpg)

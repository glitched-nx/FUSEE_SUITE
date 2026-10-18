## Aktuelle Version: 9.2.1 - Scrolle nach unten für Infos / Intro...

#### TL;DR? Changelog und sonstige Infos...

* 19/06/22 - Der Seeeduino XIAO verfügt über TX/RX-LEDs. Diese befanden sich in den Beta-Builds vom 18/06 in der „Schwebe“. Neue Betas hinzugefügt. Die TX/RX-LEDs sollten nun synchron mit der regulären Onboard-LED arbeiten.
* 18/06/22 - BETA-Unterstützung für Seeeduino XIAO hinzugefügt. Dies ist komplett ungetestet, da ich kein solches Gerät besitze. Ich verlasse mich darauf, dass das Board korrekt aufgebaut ist und keine üblen Bugs aufweist. Trinket-Builds usw. funktionieren auf diesem Board NICHT, da es wie ein Feather über einen externen Oszillator verfügt. Wenn du also eine „falsche“ Version flashst, läuft sie nicht an, sondern tut einfach gar nichts. (Die Straps wären ohnehin falsch...) Part 1 und Part 2 hinzugefügt. `SETTINGS.UF2` kann genau wie bei anderen Boards verwendet werden.
* 06/06/22 - Stiller Bugfix. Helligkeitsanpassung für Neopixel behoben. VOL+ Sperre hinzugefügt (für Kinder-Switches – nur über `SETTINGS.UF2` einstellbar oder beim Selbstkompilieren via Arduino). Dateinamenkonvention für Einstellungen geändert. `SETTINGS.UF2`-Dateien verbessert. Nach dem Flashen startet der UF2-Modus nun automatisch, um das Hinzufügen der `SETTINGS.UF2` zu erleichtern. Falls nicht benötigt, schalte die Konsole einfach aus und starte sie neu, um die Standardwerte zu laden. Alles vollautomatisch.
* 05/06/22 - OK... Alle Dateien sind jetzt aktualisiert. Part 1 - Viele Modifikationen. Part 2 - Ebenso. - `SETTINGS.UF2`-Dateien eingeführt.

## Die alte README und ältere (Basis-)Versionen findest du [HIER](https://github.com/glitched-nx/FUSEE_SUITE/tree/master/Fusee-Suite/Old)

## Schnelles Upgrade-Verfahren von einer früheren Version...

* Stelle sicher, dass deine SD-Karte so eingerichtet ist, wie SDSetup es vorsieht... Mindestens `bootloader/update.bin` MUSS vorhanden sein. Ziehe `fusee.bin` per Drag & Drop in das Hauptverzeichnis (Root) der SD-Karte (befindet sich im Ordner `payloads`), falls gewünscht. Wenn du deine eigene Dateistruktur bevorzugst, musst du deinen `fusee.bin`-Payload (kann beliebig heißen) und die `update.bin` (ebenfalls beliebig) im Menü von Fusee_UF2 manuell auswählen.
* Boote deine Switch entweder in die OFW oder CFW.
* Wechsle in den UF2-Modus, indem du entweder leicht auf die Gehäuserückseite drückst, um den Reset-Taster ZWEIMAL zu betätigen. Also: Drücken... Drücken... Wenn du keinen RESET-Taster hast, nimm die Rückseite der Konsole ab und verbinde RESET kurz mit GND (Masse). Falls du bereits eine relativ aktuelle Version von Fusee_UF2 nutzt, gibt es Möglichkeiten, den UF2-Modus zu starten, ohne das Gehäuse zu öffnen... Schau dazu oben unter „Old Releases“ nach.
* Stelle sicher, dass der Switch-Bildschirm im Standby und ausgeschaltet ist – NICHT NEU STARTEN!
* Verbinde die Konsole über ein USB-C-Kabel mit dem PC. Du erhältst eine Fehlermeldung („Laden nicht möglich“ / „Unable to charge“). Das ist völlig normal.
* Versetze den Bildschirm wieder in den Standby (falls er aufgewacht ist), indem du kurz auf POWER drückst, um den Bildschirm auszuschalten.
* Es sollte nun ein UF2-Laufwerk am PC erscheinen (gemountet werden). Es heißt wahrscheinlich `SWITCHBOOT`.
* Ziehe den neuen Part 1 für deinen Chip per Drag & Drop auf das Laufwerk (wahrscheinlich ein Trinket oder ein entsprechender Klon). Sobald du Part 1 draufziehst, ändert sich der Laufwerksname von `SWITCHBOOT` zu `FUSEE`. Wenn er sich nicht in `FUSEE` ändert, ist etwas schiefgelaufen. Versuche es erneut.
* Das UF2-Laufwerk sollte kurz verschwinden und nach einigen Sekunden wieder auftauchen. Falls nicht, drücke erneut zweimal auf die Gehäuserückseite und schalte den Bildschirm wieder aus... Jetzt sollte es erscheinen. Prüfe, ob das Laufwerk `FUSEE` heißt! Das ist wichtig.
* Wähle einen Part 2. Langdruck (Long-press) oder Mehrfachdruck (Multiple-press)? Du entscheidest. Mehrfachdruck ist für Leute ohne verbaute LED gedacht, kann aber von jedem genutzt werden. Ziehe die Datei per Drag & Drop auf das Laufwerk. Das UF2-Laufwerk sollte sich erneut öffnen...
* Du bist fertig. Du kannst die Konsole nun entweder ausschalten oder noch eine `SETTINGS.UF2` flashen. Die Konsole bootet danach ganz normal bzw. genau so, wie du sie konfiguriert hast.
* Ende. Wenn alles gut gegangen ist, musst du deine Konsole nie wieder öffnen (falls du es diesmal getan hast), um in den UF2-Modus zu gelangen. Niemand sollte seine Konsole zerlegen müssen, nur um den Chip in den UF2-Modus zu versetzen.

## Schnellstmögliche Minimal-Installation (Bare Minimum):

* Verwende ein unterstütztes Adafruit-Board (Empfehlung: Trinket).
* Mit dem PC verbinden und durch zweimaliges Drücken von RESET in den Bootloader-Modus wechseln.
* Trinket Part 1 per Drag & Drop aufspielen.
* Trinket Part 2 per Drag & Drop aufspielen.
* USB-Port auf dem Trinket mit Heißluft entfernen.
* Trinket mit Kaptonband zur Isolierung und etwas doppelseitigem VHB-Klebeband auf dem RAM-Abschirmblech fixieren.
* USB D+/D-, 3V, GND und den Joy-Con-Strap anlöten (DAS IST DAS ABSOLUTE MINIMUM. Ein permanenter CFW-Boot ist so nicht möglich; da der VOL+ Strap nicht angeschlossen ist, läuft es IMMER auf Dual-Boot hinaus).
* Alles sauber und ordentlich mit Kaptonband isolieren.
* Nimm eine vernünftige Schere und schneide einen Schlitz in das Abschirmblech, um Platz für den Trinket zu schaffen.
* FERTIG...
* Löte bei Bedarf zusätzliche Straps an. Wenn du glaubst, dass du die Zusatzfunktionen des Chips ohnehin nicht nutzt, kannst du sie weglassen.
* Die zusätzlichen Straps sind VOL+ und USB. Diese sind erforderlich, wenn du dauerhaft und automatisch in die CFW booten möchtest.

#### Wichtige Unterschiede...

* Es wird nicht mehr nach `payload.bin` gesucht. Stattdessen sucht der Chip nach `fusee.bin` (oder `bootloader/update.bin`). Du kannst deine `payload.bin` aber im Fusee_UF2-Menü umbenennen.
* Du willst jedes Mal direkt in Hekate booten? Ganz einfach: Deaktiviere oder lösche einfach die `fusee.bin`, falls vorhanden (oder benenne Hekate entsprechend um, wenn du möchtest). Hekate / Nyx bootet dann automatisch.
* Halte BEIDE Lautstärketasten (VOL+ und VOL-) gedrückt und schalte die Konsole ein, wenn du einen Kaltstart (Cold-Boot) direkt in Hekate / Nyx statt in die `fusee.bin` durchführen willst (nicht dauerhaft, gilt nur für diesen einen Bootvorgang. Um es dauerhaft zu machen, deaktiviere `fusee.bin` im Menü).

## FUSEE UF2

Interner, Mikrocontroller-basierter Payload-Loader/-Booter für die Nintendo Switch.

Bestehend aus:

Einer UNGEPATCHTEN Nintendo Switch v1 Konsole

Einem SAMD21-Gerät (Adafruit Trinket / Gemma / ItsyBitsy usw.)

Part 1 dieser Software: Der SWITCHBOOT- oder FUSEE-RCM-Bootloader, der – sobald der Chip in deiner Konsole verbaut ist – den RCM-Modus auslöst.

Part 2: Die eigentliche Software zum Laden des Payloads sowie die Chip-Einstellungen...

## Features - Danke an CTCAer für die Hekate-Basis, die teilweise in Part 2 genutzt wird. Der andere Teil basiert auf Arduino.

* Schneller Exploit und Bootvorgang
* Schnelles Auslösen des RCM (ca. unter 5 ms)
* Integrierte Tools zum Durchsuchen der SD-Karte
* Neukalibrierung von Akku und Ladestandsanzeige (wirkt allerdings keine Wunder – ein toter Akku bleibt ein toter Akku)
* „Korrekter“ Bootscreen: Entweder klassisch Schwarz (Stock) oder Rot/Weiß
* Wechsel zwischen OFW / CFW / Linux usw. einfach durch Gedrückthalten einer Taste beim Einschalten
* Schnelle SAFE-Backup-Funktion
* Software ist einfach zu programmieren und zu aktualisieren (sobald man das Prinzip einmal verstanden hat)
* Wirf PC-Launch-Tools, Joy-Con-Jigs und das akkufressende AutoRCM für immer in den Müll
* Viele Nutzer seit über 4 Jahren (lief lange Zeit ohne Updates, da schlicht keine nötig waren)
* Wenn dein Chip sauber verbaut ist, hält er ein Leben lang

## Kurzanleitung:

* Chip einbauen
* „Part 1“ flashen
* Einen „Part 2“ auswählen... Flashen
* Optional `SETTINGS.UF2` flashen
* SD-Karte über sdsetup.com einrichten
* `fusee.bin` in das Hauptverzeichnis (Root) der SD-Karte legen
* Einschalten
* Kurzes Drücken auf VOL+ bootet `fusee.bin` (oder Hekate/Nyx). Langes Drücken auf VOL+ öffnet das Menü
* VOL- UND VOL+ startet Hekate/Nyx (keine weitere Konfiguration nötig – der Payload sollte bereits unter `bootloader/update.bin` liegen)
* Keine Taste drücken – der gewählte Payload oder die Original-Firmware (OFW) startet, abhängig von deinen Chip-Einstellungen

## EINBAU EINES CHIPS

Die meisten SAMD21-Geräte werden unterstützt oder können passend gemacht werden.

Unterstützte Boards sind:

* Adafruit Trinket M0
* Adafruit QTPY M0
* SEEEDUINO XIAO (Testphase BETA)
* Rebug SWITCHME
* RCM-X86
* Adafruit Gemma
* Adafruit ItsyBitsy
* Adafruit Feather
* **NEU** Naked Chip – wenn du WIRKLICH gut löten kannst, verbaue einen reinen QFP-Chip auf der Unterseite. Keine Tasten oder LEDs erforderlich

Sieh dir die [Einbaudiagramme](https://github.com/glitched-nx/FUSEE_SUITE/tree/master/Install%20Diagrams) an, um zu erfahren, wie man den Chip einbaut. Oder verbaue einen „Naked“-Chip ganz ohne Tasten, LED oder eigene Platine (PCB).

## NUTZER OHNE RESET-TASTER

Um auf den UF2-Bootloader zuzugreifen, HALTE ENTWEDER VOL+ FÜR 20 SEKUNDEN GEDRÜCKT oder WÄHLE DIE ENTSPRECHENDE OPTION IM CHIP-ASSISTENTEN-MENÜ.
Wenn du keinen Part 2 geflasht hast (oder dieser beschädigt ist) und du keinen Zugriff auf den RESET-Pin hast, kannst du den Chip alternativ stromlos machen,
SWDIO mit GND verbinden und die Konsole einschalten. Dadurch gelangst du in den Part-1-Bootloader... Siehe unten...

Es wird in den meisten Fällen empfohlen, deinen Chip VOR DEM EINBAU zu flashen. Das bleibt aber deine Entscheidung. Du kommst unter allen Umständen in den UF2-Bootloader. Ein fabrikneuer, leerer („VIRGIN SOLO“) Chip MUSS jedoch vor dem Einbau geflasht werden, schon um deine eigenen Nerven zu schonen.

Also...

* Flashe Part 1 – ein Laufwerk namens `FUSEE` öffnet sich.
* Flashe Part 2 – die Software startet sofort.
* OPTIONAL – Im Fusee-Branch auf dieser Seite findest du neue `SETTINGS.UF2`-Dateien. Diese sind universell für alle SAMD21-Chips einsetzbar. Wechsle in den UF2-Modus und ziehe sie per Drag & Drop auf das Laufwerk, um deine Chip-Einstellungen zu ändern.

## Bedienung

#### Part 1 flashen

Bei regulären („stock“) Mikrocontrollern (z. B. von Adafruit) ziehst du deinen Part 1 einfach per Drag & Drop auf das UF2-Laufwerk deines Chips. Das war's schon.

Wenn du einen FABRIKNEUEN SAMD21-Chip flashst, musst du dies mit einem Flasher deiner Wahl tun oder alternativ mein fertig konfiguriertes Raspberry Pi / OpenOCD-Image verwenden.
Verbinde Strom (Power), GND, SWCLK sowie SWDIO und flashe eine BIN-Datei. Ich empfehle die TRINKET-Version, aber jede andere geht auch. Denk daran: Wenn du die FEATHER-Version nutzt, benötigt dein Chip
einen externen Oszillator. Egal wofür du dich entscheidest, dein leerer Chip nutzt exakt dieselbe Pinbelegung wie das entsprechende vollwertige Board. Du musst deine Straps also genau wie bei diesem Board-Typ verkabeln.

Wenn du einen gebrickten Chip neu flashst, gilt genau derselbe Ablauf.

#### Part 2 flashen

Ziehe den gewählten Part 2 per Drag & Drop auf das `FUSEE`-UF2-Laufwerk. Das Flashen ist damit abgeschlossen.

Ich werde 2 identische Versionen hochladen: Eine mit der Einstellungsmethode über langes Drücken (Long-press), eine für mehrfaches Drücken (Multiple-press). Es handelt sich um absolut identische Dateien, bei denen lediglich eine
Option ab Werk voreingestellt ist, um Long-press oder Multiple-press zu aktivieren. Du kannst diese Option jederzeit im Menü oder über deine VOL+ Taste ändern. Das dient nur der Bequemlichkeit. Die Dateien sind ansonsten exakt
gleich. Du kannst deine Einstellungen auch über eine `SETTINGS.UF2`-Datei anpassen.

**Long-press (Langdruck)** – Zu JEDEM ZEITPUNKT, an dem die Konsole eingeschaltet ist, kannst du VOL+ GEDRÜCKT HALTEN, woraufhin die LED anfängt zu blinken. Zähle das Aufblinken für die gewünschte Einstellung mit.
Die Einstellungen sind:

* 1x Blinken - Wechsel zwischen Dual-Boot / Chip-basiertem RCM oder FailsafeRCM (standardmäßig ist ChipRCM aktiviert und die Konsole startet bei jedem Booten in den RCM, sofern die Straps verbunden sind)
* 2x Blinken - Wechsel der Bootlogo-Farbe – „Stock“ Schwarz oder „Switch“ Rot
* 3x Blinken - Helligkeit für RGB-LED / Dotstar / Neopixel (sofern an den richtigen Pins angeschlossen; bei unveränderten Adafruit-Boards ist das der Fall)
* 4x Blinken - Wechsel der Einstellungsmethode zwischen Long-press und Multiple-press
* 5x Blinken - Alle Chip-Optionen auf Werkseinstellungen zurücksetzen (AutoRCM bzw. ChipRCM aktiviert, schwarz-weißer „Stock“-Bootscreen)
* 6x Blinken - Zugriff auf den UF2-Bootloader. Aktiviere dies, während du im Fusee_UF2-Programm bist, verbinde die Konsole mit dem PC und starte irgendetwas (OFW / CFW?) – das Laufwerk `FUSEE` (ehemals `SWITCHBOOT`) öffnet sich sofort am PC. Nutzer ohne LED können dies ebenfalls auslösen, indem sie VOL+ für 20 Sekunden gedrückt halten.

**Multiple-press (Mehrfachdruck)** – Dieser Modus ist nach einem Kaltstart (Cold-Boot) nur für 30 Sekunden aktiv. Wenn du also mehrere Optionen ändern möchtest, musst du eventuell neu starten, um den Countdown zurückzusetzen.
Der Countdown wird auf dem Bildschirm angezeigt. Warum ein Countdown? Damit der Modus nicht versehentlich aktiviert wird. Kinder und Erwachsene drücken im normalen Betrieb oft mehrfach auf VOL+, um die Lautstärke zu erhöhen.
Dadurch könnten sich sonst ungewollt Einstellungen verstellen. Dieser Modus hat aber einen großen Vorteil: Du kannst die Optionen direkt im Fusee-Menü einstellen. Schau dir dort den
„Chip Setting Assistant“ (Chip-Einrichtungsassistent) an. Dadurch ist es möglich, einen Chip komplett „blind“ und „naked“ zu nutzen – also völlig ohne LED oder Reset-Taster.

Die Optionen 1 bis 6 sind identisch mit den oben genannten.

Öffne den Chip Setup Assistant im Menü und drücke schnell hintereinander VOL+, um die gewünschte Option zu ändern.

Warum gibt es nicht einfach ein Menü, das man ganz „normal“ bedienen kann?
Technische Limitierungen.
Es ist nicht möglich, direkt mit dem Chip zu kommunizieren, sobald der integrierte „Payload“ auf der Switch läuft. Bzw. es IST theoretisch möglich... Aber der USB-Code würde EXTREM VIEL Arbeit erfordern, um vom Host- in den Device-Modus zu wechseln,
von der Switch-Seite aus zu enumerieren und über eine serielle Schnittstelle zu kommunizieren. Es wurde überlegt, zusätzliche Kabel für I2C oder Ähnliches zu ziehen. Aber das hilft den Nutzern der ersten Stunde mit ihren bestehenden Installationen nicht weiter.
Außerdem ist der Speicherplatz knapp. Bei der aktuellen Größe ist es ohnehin schon extrem eng, alles auf einen SAMD21E17 zu quetschen. Deshalb ist der E18 (mit 256 KB Flash) der Standard.
Für die paar verfügbaren Optionen lohnt sich dieser Aufwand schlichtweg nicht.
Daher „spiegeln“ wir das mehrfache Tastendrücken, das wir in der Hardware machen, einfach in der Software. Das ist alles.

Weitere menübasierte Funktionen – minimalistisches SCHNELL-Backup. Keine Geduld, auf einen vollständigen rawnand-Dump zu warten? Sichere einfach nur deine Partitionen `BOOT0/1` und `PRODINFO`. Einen NAND
komplett von Grund auf neu aufzubauen ist zwar immer noch lästig, aber so bleiben dir zumindest all deine Zertifikate und Kalibrierungsdaten erhalten. Da draußen gibt es ein paar echt miese Typen (Malware/Bricker). Mach ein SAFE-Backup. Sofort.

## Zusammenfassung der Änderungen in dieser Paketversion

Modifikationen am UF2-Bootloader

* Aktualisiert für QTPY
* (Noch unveröffentlichte Unterstützung für Raspberry Pi Pico – erfordert weitere Tests und ist daher aktuell noch nicht enthalten)
* Erkennungscode zur Prüfung des Dual-Boot-Flags, inklusive neuer Failsafe-Option
* Umbenennung des Laufwerks
* Option zum Entfernen der RST-Taster-Unterstützung für schnelleres Booten und für Konsolen ohne eigenen RST-Taster – standardmäßig nicht aktiv. Nach reiflicher Überlegung wurde entschieden, den Doppeldruck
beizubehalten. Wenn du den RESET-Taster aus irgendeinem Grund deaktivieren möchtest, musst du den Code nach einer Anpassung der Datei `board_config.h` selbst aus dem Quellcode neu kompilieren.
* Part 1 erkennt nun, ob über USB Strom anliegt, bevor die Straps auf Low (GND) gezogen werden (sofern die Einstellung FailsafeRCM genutzt wird). Liegt Spannung an, ist die Konsole am PC angeschlossen und der Chip kann keinen Payload senden. Das könnte sonst dazu führen, dass sich der Akku im RCM komplett tiefentlädt
und Schaden nimmt. Die neue Option (einstellbar in Part 2) verhindert genau das: Wenn versucht wird, über den Chip zu booten, während ein USB-Kabel eingesteckt ist,
erfolgt stattdessen ein NORMALER OFW-BOOT und der Chip schaltet sich bis zum nächsten Neustart ab. Dies ist optional und keineswegs zwingend erforderlich, kann aber sehr praktisch sein. ACHTUNG: Dadurch WERDEN eFuses durchgebrannt (gebrannt) – wenn du also aus irgendeinem Grund versuchst, deine Fuses auf einem niedrigen Stand zu halten
(wofür es eigentlich keinen echten Grund mehr gibt), solltest du diese Funktion nicht verwenden.
* Notfall-Zugriff auf den Bootloader (falls du keinen Zugriff auf den RESET-Pin hast o. Ä.)... Verbinde SWDIO mit GND, während du PWR drückst, um in den UF2-Modus zu gelangen (Konsole ausschalten, SWDIO auf GND halten, einschalten).
* Anpassbare Verzögerung für die Straps (aktuell 75 ms – ich hatte auch mit einer Haltezeit von 25 ms gute Ergebnisse). Wenn du diesen Wert ändern möchtest, musst du selbst aus dem mitgelieferten Quellcode kompilieren. Bearbeite dazu die `board_config.h` für dein jeweiliges Board.
* Kompiliert mit der GCC-Toolchain 2019-9-Q4. Neuere Versionen erzeugen eine langsamere Binary, die nicht schnell genug initialisiert, um rechtzeitig den RCM auszulösen.
* Um den größeren Initialisierungscode und die Fuse-Einstellungen im SAMD21 unterzubringen, ist die Binary für Part 1 deutlich angewachsen. Es war daher notwendig, die RGB-LED-Unterstützung NUR FÜR PART 1 zu entfernen. Du siehst dort also nur noch eine einfache
Standard-LED leuchten, falls verbaut. Die RGB-LED funktioniert wieder völlig normal, sobald Part 2 geflasht ist. Dies betrifft ausschließlich Part 1. Für Part 1 brauchen wir ohnehin keine RGB-LED... Der Adafruit QTPY ist hiervon ausgenommen – da er keine eigene
einfarbige Onboard-LED besitzt, bleibt die RGB-LED bei diesem Board auch in Part 1 aktiviert.

#### Modifikationen am Hauptprogramm

* Basiert auf Hekate 5.2+
* Bildschirmausrichtung horizontal gedreht
* Schriftart geändert
* Farben angepasst
* TUI modifiziert – Neuimplementierung der Statusleiste. Neues Timeout-Feature – kehrt nach einer gewissen Zeit automatisch zum Hauptbildschirm zurück
* GFX modifiziert – neue Schriftart, neues Batterie-Icon, Bildschirm-Dimmung
* Dateibrowser – aufgeräumt. Unterstützung für mehrere Seiten. Einfach zu bedienende „API“. Durchsuche, starte oder lösche beliebige Dateien an jedem Ort auf der SD-Karte
* SAFE-Backup hinzugefügt (Schnell-Backup von `BOOT0/1` und `PRODINFO`)
* Unterstützung für das Flashen von Reparatur-Paketen für `BOOT0/1` (auch bei geringerer Dateigröße / Undersize)
* Löschen von Dateien und Ordnern
* Aktivieren / Deaktivieren von Nyx
* Backup und Wiederherstellung (Restore) aus beliebigen Ordnern
* Pre-Caching / Vorab-Prüfung („stat“) von Payloads während der Anzeige des Bootscreens für höhere Geschwindigkeit
* Chip Setup Assistant neu sortiert, damit auch Nutzer ohne RST-Taster oder LED problemlos in den Bootloader-Modus gelangen können
* Durch den Chip Setup Assistant (bei Nutzung von Multiple-press) wird keine LED mehr benötigt
* Du kannst nun einen „Naked“-Chip auf der Unterseite des Mainboards verbauen und alle Funktionen komplett ohne LED oder RST-Taster nutzen
* Informativeren Hilfe- / Info-Bildschirm zum Chip hinzugefügt

#### Modifikationen am Arduino-Code

* Code bereinigt
* Beschleunigung von Check / Launch / Stack-Collapse. Das Starten von Fusee (zumindest bis zum Atmosphère-Logo) ist doppelt so schnell wie im Originalzustand (Stock).
* Neopixel-Unterstützung hinzugefügt
* 20 Sekunden Langdruck (Long-press) für den „blinden“ Zugriff auf den UF2-Bootloader ganz ohne LED.

## PROBLEME / FAQ

* Ich habe Part 1 geflasht – Nichts ist passiert. Es ist kein Laufwerk aufgetaucht.

Trenne die USB-Verbindung (falls eingesteckt), schalte die Konsole komplett aus und wieder ein. Wenn immer noch nichts passiert, musst du den RESET manuell auslösen. Verbinde dazu entweder den RESET-Pin kurz mit GND oder halte SWDIO auf GND, während du die Konsole einschaltest.

* Ich kann nichts per Drag & Drop auf meinen Chip ziehen. Es passiert nichts, wenn ich RESET drücke.

Hast du einen fabrikneuen (Virgin) Chip? Dieser muss beim allerersten Mal zwingend mit OpenOCD / einem Raspberry Pi / einem anderen Programmiergerät geflasht werden. Ich kann das gegen Übernahme der Portokosten für dich erledigen.
Wenn du ein Board hast, das bereits funktioniert hat, mach einen kurzen Test... Wenn es in der Konsole verbaut ist, schalte sie ein, während du VOL+ gedrückt hältst. Wird der RCM ausgelöst? Dann musst du lediglich in den UF2-Modus wechseln. Siehe dazu die erste Frage.
Passiert gar nichts, hast du es tatsächlich irgendwie geschafft, Part 1 zu beschädigen. Behandle ihn wie einen fabrikneuen Chip: Verbinde SWCLK und SWDIO und flashe ihn über OpenOCD neu.
Falls der USB-Port noch auf dem Board vorhanden ist, versuche, ihn direkt an den PC anzuschließen und zweimal schnell auf RESET zu drücken.

#### TODO: Ausführlichere Anleitung zum Flashen und zur Nutzung

#### TODO: Link zum Raspberry Pi OpenOCD-Image und Kurzanleitung hier einfügen.

## Glossar der in diesem Dokument verwendeten Begriffe

* CFW - Custom Firmware (angepasste Firmware)
* OFW - Original (Stock) Firmware (originale Systemsoftware von Nintendo)
* RCM - Recovery Mode. Ein spezieller Modus der Switch für Wartungszwecke, vermutlich für die Produktion im Werk gedacht. Für Endnutzer normalerweise nicht zugänglich. Wir nutzen ihn als notwendiges Einfallstor, um eigene „Payloads“ über eine Sicherheitslücke auszuführen.
* AutoRCM - Automatisches Auslösen des RCM-Modus beim Einschalten, was nötig ist, um den Bootvorgang einer CFW auf der Switch ohne manuelle Hilfsmittel einzuleiten.
* Payload - Ein kleines Softwareprogramm, das vor dem eigentlichen Betriebssystem auf der Konsole startet, die Hardware-Schwachstelle ausnutzt und beliebigen eigenen Code ausführt.
* ChipRCM - Meine eigene Version von AutoRCM. Anstatt wie bei anderen Methoden gezielt Daten im internen Flash-Speicher (BOOT0) zu korrumpieren, nutzt diese Methode im Grunde den „offiziellen“ Hardware-Weg über den Chip, um in den RCM zu gelangen.
* FailsafeRCM - Identisch mit ChipRCM, deaktiviert sich jedoch automatisch selbst, wenn der Chip keinen Payload senden kann – z. B. wenn die Konsole am PC angeschlossen ist (die Nutzung von Fusee-UF2 über einen internen Chip ist technisch nicht möglich, solange die USB-Leitung durch einen PC blockiert wird, wodurch die Konsole im RCM-Modus „gefangen“ wäre. Im normalen AutoRCM- oder ChipRCM-Modus würde sich der Akku dadurch komplett entladen und potenziell Schaden nehmen). FailsafeRCM verhindert dies. Du MUSST den USB-Strap angelötet haben, um diese Funktion nutzen zu können.
* SAFE-Backup - Ein unverzichtbares Backup der Partitionen `BOOT0/1` und `PRODINFO`. Diese enthalten konsolenspezifische Zertifikate und Kalibrierungsdaten deiner Switch. Sie sind nicht zwischen verschiedenen Konsolen austauschbar. Google nach „Brickachu“ für weitere Informationen.
* Strap - Ein dünnes Kabel bzw. eine Datenleitung, die einen Ein-/Ausgang des Chips (unseres SAMD21, den wir für Fusee_UF2 nutzen) mit einem bestimmten Lötpunkt auf dem Switch-Mainboard verbindet, um eine Hardware-Aktion auszulösen. Beispiel: Der VOL+ Strap simuliert das physische Drücken der VOL+ Taste. Wir nutzen insgesamt 3 Straps: Joy-Con (Pin 10), Volume (VOL+) und USB. Nur der Joy-Con-Strap ist zwingend erforderlich, um eine CFW zu starten. VOL+ kann beim Einschalten auch manuell per Hand gedrückt werden.
* Drop the straps / Einen Strap auf Low ziehen - Eine dieser Leitungen auf Masse (GND) ziehen, wodurch das entsprechende Signal ausgelöst wird.

## Warum arbeitest du immer weiter an so einem simplen Stück Software für eine so simple Aufgabe?

* Weil ich möchte, dass es sauber läuft und so fehlerfrei wie möglich ist
* Es soll einfach zu bedienen sein
* Und einfach zu installieren

## Wie funktioniert das technisch?

* Der Chip generiert den benötigten Payload im Bruchteil einer Sekunde „on-the-fly“ (in Echtzeit) basierend auf den gewählten Einstellungen. Dabei kommt Code von mir, Usbhost, anderen Entwicklern aus der Anfangszeit sowie vom Schöpfer von Hekate und aus dem Arduino-Projekt zum Einsatz. Es ist (bzw. war) ein echtes Gemeinschaftsprojekt.

## Verschleißt der Chip nicht, wenn ständig darauf geschrieben wird?

* Ja, irgendwann schon. Vielleicht. Atmel gibt 10.000 Schreibzyklen an, bevor der Chip langsam „demenzkrank“ wird. Diese Software nutzt jedoch vollständiges Wear-Levelling (Verschleißausgleich), und es werden immer nur einzelne Bits genau dann geschrieben, wenn es wirklich nötig ist – anstatt dieselben Datenblöcke immer und immer wieder neu zu überschreiben. Das verschafft uns effektiv $10000^{15}$ Schreibzyklen (wir nutzen 15 Speicherseiten ganz am Ende des Flash-Speichers). Das hält vermutlich länger als jede SD-Karte... Ich nutze seit 2018 exakt denselben SAMD21-Testaufbau mit demselben Chip. Er wird fast täglich beschrieben und genutzt. Er läuft immer noch einwandfrei. Zudem wird im Alltag ja nicht permanent darauf geschrieben: Wahrscheinlich stellst du deine Optionen einmal ein und änderst sie danach nie wieder.

## Haftungsausschluss (Disclaimer): Du solltest ganz genau wissen, was du tust, bevor du dich an diese Modifikation wagst. Es ist nicht einfach – die Lötpunkte sind wirklich extrem winzig. Dieses Projekt enthält keinerlei kryptografische Schlüssel (Keys) oder urheberrechtlich geschütztes Material von Nintendo. Die Veröffentlichung erfolgt als Open-Source-Projekt ohne jegliche ausdrückliche oder stillschweigende Garantie. WENN ETWAS SCHIEFGEHT, BIST ALLEIN DU SELBST DAFÜR VERANTWORTLICH.

-----

## Current Version: 9.2.1 - Scroll down for info / intro...

#### TL;DR? Changelog and other bits...

- 19/06/22 - On Seeeduino XIAO, it has TX/RX LEDs. These were left in "limbo" in the 18/06 beta builds. New betas added. TX/RX LEDS should be working in unison with the standard onboard LED now.
- 18/06/22 - Added BETA Seeeduino XIAO support. This is completely untested as I do not have such a device. I'm relying on the board being built correctly and not having any nasty bugs. Trinket etc will NOT work on this board as it has external oscillator, like a Feather. So if you flash an "incorrect" version, it won't run. It will just sit there. (The straps would be wrong anyway...) Part 1 and part 2 added. SETTINGS.UF2 can be used as other boards.
- 06/06/22 - Silent bugfix. Neopixel brightness adjustment fixed. Added a VOL+ lockout (for kids Switches - only settable with SETTINGS.UF2, or building with Arduino). Changed settings filename convention. Improved SETTINGS.UF2 files. After flashing, UF2 mode will start automatically, for convenience of adding SETTINGS.UF2. If not required, just power down console and reboot to set some default values. All automatic.
- 05/06/22 - OK... All files now updated. Part 1 - Lots of modifications. Part 2 - Same. - SETTINGS.UF2 files introduced.

## Old README and older (basic) versions are [HERE](https://github.com/glitched-nx/FUSEE_SUITE/tree/master/Fusee-Suite/Old)

## Quick upgrade procedure if coming from earlier version...
- Make sure your SD is set up as SDSetup does it... bootloader/update.bin present AT LEAST. Drag and drop fusee.bin to SD root (its in payloads folder) if desired. If you want your own file organisation, you will need to choose your fusee.bin payload(can be anything) and update.bin (again, anything) in the menu of Fusee_UF2.
- Boot your Switch into either OFW or CFW
- Get into UF2 mode, by either flexing back cover to activate reset switch TWICE. So Press... Press... Or if you don't have a RESET button, take back off console and touch RESET to GND. If running a recent-ish version of Fusee_UF2, there are ways how to enter UF2 mode without taking the back off... Look in Old Releases above.
- Ensure Switch screen is sleeping and switched off - DONT REBOOT!
- Plug into PC using USB-C cable. You will get a "Unable to charge" error. This is normal
- Make the screen sleep (if it woken up) by pressing POWER to turn it off and sleep the console
- A UF2 drive should pop up (or mount). Will be called SWITCHBOOT probably
- Drag and drop the new part 1, for your chip. Will probably be a Trinket or a team clone. Drag and drop Part 1... The name will change from SWITCHBOOT to FUSEE. If it isn't FUSEE, something went wrong. Try again.
- UF2 drive should disappear and reopen again a few seconds later. If it doesn't, flex back cover twice again and switch screen off... Should now appear. Check drive is called FUSEE! This is important.
- Choose a Part 2. Long-press, or Multiple-press? You decide. Multiple-press is designed for people without LED. But anyone can use it. Drag and drop. UF2 drive should open again...
- You are finished. You can either power down or flash a SETTINGS.UF2. Console will boot normally or however you have configured it.
- End. If all went well, you should never need to open your console (if you did) to enter UF2 mode again. Most people shouldn't need to strip their console just to reset their chip into UF2 mode.

## Fastest possible bare minimum deployment:
- Use a supported Adafruit board(Recommend Trinket)
- Connect to PC, enter bootloader mode with 2x presses of RESET
- Drag and drop Trinket part 1
- Drag and drop Trinket part 2
- Remove USB port on Trinket with hot air
- Fix Trinket to RAM shielding using Kapton as an insulator and some VHB double-sided tape
- Connect USB D+/D-, 3V, GND and Joycon strap(THIS IS BARE MINIMUM. No permanent CFW boot is possible, as VOL+ strap is not fitted so will ALWAYS be dual-boot
- Insulate with Kapton tape, nice and neat
- Get some decent scissors and cut a slot in the shielding, making a gap for the Trinket
- COMPLETE...

- Fit extra straps if required. If you don't think you will use any of the chips extra features, then you don't need to.
- The extra straps are VOL+ and USB, which are required if you permanently want to boot into CFW

#### Important differences...
- This doesn't look for payload.bin any longer. It looks for fusee.bin (or bootloader/update.bin). You can rename your payload.bin in the Fusee_UF2 menu.
- Want to boot Hekate every time? Easy. Just disable or delete fusee.bin if you have it (or even rename hekate to that if you desire). Hekate / Nyx will boot automatically.
- Hold down BOTH VOL buttons and power on if you want to cold-boot to Hekate / Nyx, rather than fusee.bin(not permanent, this boot only. To make permanent, disable fusee.bin in menu)
## FUSEE UF2

Nintendo Switch internal microcontroller-based payload loader/booter.  

This consists of:  
A Nintendo Switch v1 UNPATCHED CONSOLE  
SAMD21 Device (Adafruit Trinket / Gemma / ItsyBitsy etc)  
Part 1 of this software which is the SWITCHBOOT or FUSEE RCM bootloader that, once the chip is installed in your console, will trigger RCM mode.  
Part 2 which is the actual payload loading software and chip settings...

## Features - Thanks to CTCAer for Hekate base that is partly used in Part 2. Arduino being the other part.
- Fast exploiting and boot
- Fast (approx < 5mS) triggering of RCM
- Built-in SD browsing tools
- Recalibrate battery and fuel gauge (it isn't God though - a knackered battery is still knackered)
- "Correct" boot screen. Either stock black, or red/white
- Change between OFW / CFW / Linux etc etc just by holding down a button at switch-on
- Fast SAFE backup feature
- Software easy to program and update (once you get your head around it)
- Bin the PC launch tools, joycon jigs and battery-killing autoRCM forever
- Many users over 4+ years (went a long time without updates as they aren't essential)
- If your chip is fitted right, will last for a lifetime

## Brief instructions:
- Fit chip
- Flash "part 1"
- Choose a "part 2"... Flash
- Flash optional SETTINGS.UF2
- Set up your SD card at sdsetup.com
- Put fusee.bin in root of SD
- Power on.
- Short press VOL+ boots fusee.bin(or Hekate/Nyx). Long press on VOL+ enters menu
- VOL- AND VOL+ runs Hekate/Nyx(no further config necessary - payload should already be "bootloader/update.bin"
- Press no buttons - chosen payload will launch, or Original Firmware will launch depending on your chip settings

## FITTING A CHIP

Most SAMD21 devices are or can be supported.

Boards supported are:
- Adafruit Trinket M0
- Adafruit QTPY M0
- SEEEDUINO XIAO (testing BETA)
- Rebug SWITCHME
- RCM-X86
- Adafruit Gemma
- Adafruit ItsyBitsy
- Adafruit Feather
- **NEW** Naked chip - if you are REALLY gifted at soldering, fit a QFP chip underneath. No buttons or LEDS needed

Look in the [install diagrams](https://github.com/glitched-nx/FUSEE_SUITE/tree/master/Install%20Diagrams) to see how to fit one. Or fit a 'Naked' chip, without buttons, LED or even PCB.

## USERS WITHOUT RESET BUTTON
To access the UF2 bootloader, either HOLD VOL+ for 20 Seconds or SELECT THE OPTION IN THE CHIP ASSISTANT MENU.
If you have no part 2 flashed, or is corrupt, and you have no access to the RESET pin, you can alternatively power-off your chip,
touch SWDIO to GND and power on. This will get you into the part 1 bootloader... See below...

It is recommended to flash your chip BEFORE FITTING in most cases. This is your decision though. You can access the UF2 bootloader in all circumstances. A new VIRGIN SOLO chip MUST be flashed before fitting, for your own sanity.
	
So...
	
- Flash Part 1 - a Fusee drive will open.
- Flash Part 2 - the software will run immediately.
- OPTIONAL - You will see new "SETTINGS.UF2" files in the Fusee branch on this site. These are universal across all SAMD21 chips. Access UF2 mode and drag/drop to change your chip settings.


## Operation

#### Flash part 1
For "stock" microcontrollers (ie Adafruit), just drag and drop your Part 1 onto your chips UF2 drive. Thats it.

If flashing a NEW SAMD21 chip, you will need to do this with your favourite flasher, or alternatively use my Raspberry Pi / OpenOCD image that is configured, ready to go.
Connect power, GND, SWCLK and SWDIO and flash a BIN file. I recommend using TRINKET version, but any will do. Remember if using the FEATHER version, your chip will
require an external oscillator. Whatever you choose, your virgin chip will be using those pins as in a full board. So you would wire your straps as that chip.

If you are reflashing a bricked chip, same instructions apply.
 
#### Flash part 2
Drag and drop chosen part 2 to FUSEE UF2 drive. Flashing complete.

I will upload 2 identical versions. One with the long-press settings approach, one with multiple press approach. These are identical files with just one 
option "preset" to enable long or multiple-press. You can change this option in the menu or with your VOL+ button. This is for convenience only. The files are exactly
identical. You can also change your settings with a SETTINGS.UF2 file.
	
Long-press - at ANY POINT the console is powered on, you can HOLD VOL+ and and LED will flash. Count these flashes for a setting.
The settings are:
- Flash 1 - Dual-boot / Chip-based RCM toggle or FailsafeRCM (by default, chip RCM is enabled and console will enter RCM every boot if straps are connected)
- Flash 2 - Bootlogo colour toggle - "Stock" black or "Switch" red
- Flash 3 - RGB LED / Dotstar / Neopixel brightness (if fitted to correct pins, stock Adafruit devices are)
- Flash 4 - Long-press / Multiple-press settings toggle
- Flash 5 - Reset all chip options back to defaults(AutoRCM - ChipRCM actually enabled, black / white "stock" bootscreen)
- Flash 6 - UF2 Bootloader access. Activate this when in the Fusee_UF2 program, connect to PC and launch something (OFW / CFW?) and the FUSEE (was SWITCHBOOT) will pop right open. People without LED can still access this by holding VOL+ for 20 seconds

Multiple-press - This mode is only active for 30 seconds from a cold-boot. So if you want to set multiple options, you might need to reboot to reset the countdown.
	The countdown is displayed on the screen. Why have a countdown? So it cannot be accidentally activated. Kids and grownups will multiple-press VOL+ to increase volume
	in normal usage. This could cause settings to get changed. There is a "plus" side to this mode. You can set the options in the Fusee menu. Look at the
	"Chip Setting Assistant". This makes it possible to use a chip completely "blind" and "naked" - IE without LED or reset switch.
	
Options 1 - 6 are the same as above.
	
Enter the Chip Setup Assistant in the menu and quickly press VOL+ to change your desired option. 
	
Why not just have a menu that you can use "normally"?
Limitations.
It isn't possible to talk to the chip once the inbuilt "payload" is running. Or rather, it IS... But USB code would require A LOT of work, to flip from host to device mode,
enumerate from Switch side and communicate via Serial. Adding new wires to implement I2C or something was considered. But this doesn't help old chip users from day 1.
Also there is space. The current size makes it a REAL squeeze to fit onto a SAMD21E17 as it is. Thats why E18 is default (with 256kb flash).
For the options available, it just isn't worth it.
So we are "mirroring" the multiple-presses in software that we are doing in hardware. That is all.
	
Other menu-based features - bare minimum QUICK backup. Not got patience to wait for full rawnand dump? Backup just your BOOT0/1/PRODINFO partitions. Rebuilding a NAND
from scratch is still a faff, but you will have all your certs and calibration data intact. There are some vicious b**tards out there. Do a SAFE backup. Now.

## Summary of works done in this version of the package

UF2 Bootloader modifications

- Updated for QTPY
- (As yet unpublished Raspberry Pi Pico support - this requires testing further, so isn't included at this time)
- Detection code to check dual-boot flag, with new Failsafe option
- Renamed
- Option to remove RST button support for faster booting and units without RST switch - this isn't active. After consideration, it was decided to leave double-press
intact. If you want to disable RESET button for whatever reason, a rebuild from source is required, after editing your "board_config.h" file.
- Part 1 now detects if USB has power before pulling the straps low(if using the Failsafe RCM setting). If it does, the PC is plugged in and no payload can be pushed. This could cause a battery to go flat
and become damaged. The new option (settable in part 2) will not allow this to happen. If this setting is used, if attempting to boot using the chip and USB is plugged in,
a NORMAL OFW BOOT will occur and the chip will switch off until next reboot. This is optional and is in no way required. But it can be handy. It WILL burn fuses - so if you are trying to save fuses,
for whatever reason, (no real need to any longer), do not use this.
- Emergency bootloader access (if you have no RESET pin access or whatever)... Touch SWDIO to GND when pressing PWR to enter UF2 mode.(PWR off, touch SWDIO to GND, power on).
- Adjustable delay for straps(currently 75mS - I've had good results using a strap hold time of 25 mS. If you want to change this, rebuild from source included. Edit "board_config.h" for your board.
- Built using 2019-9-Q4 GCC toolchain. Newer versions result in a slower binary which cannot init fast enough to enter RCM.
- To accomodate the larger init code and fuse settings in SAMD21, the binary has grown substantially for part 1. Its been necessary to remove RGB LED support for PART 1 ONLY. You will only see a single
LED if fitted. RGB LED will work normally once Part 2 is flashed. This applies to Part 1 only. We do not need an RGB LED with Part 1 anyway... Adafruit QTPY is excluded from this - it has no provision for
onboard single LED - so RGB LED is enabled on this.


#### Main program modifications

- Started with Hekate 5.2+ base
- Screen flipped horizontal
- Font changed
- Colours modified
- tui modified - reimp. of status bar. New timeout feature - returns to main screen after so long.
- gfx modified - new font, new batt asset, screen dimming
- File browser - cleaned up. Multiple pages supported. Easy to use "api". Browse / launch / delete any file in any location on SD
- Safe backup added (quick - BOOOT0/1/PRODINFO)
- Repair pack BOOT0/1 (undersize) flash support
- File / folder deletion
- Enable / disable nyx
- Backup and restore from any folder
- Pre-caching / pre-"stat"ing of payloads during bootscreen show for speed
- Chip setup assistant reordered so people without RST or LED and get into bootloader mode
- Chip setup assistant (if multiple-press is used) makes LED not required.
- Now you can fit a "naked" chip to the underside and access all functions without LED or RST switch
- Added more informative chip help screen / about screen


#### Arduino modifications

- Cleanup
- Speedup check / launch / stack collapse. Fusee launching (to Atmosphere logo at least) is 2x faster than stock.
- Neopixel support added
- 20s long-press for "blind" sans-LED UF2 bootloader access.

## ISSUES / FAQ

- I flashed Part 1 - Nothing happened. No drive popped up.

Disconnect from USB if connected, power off and back on again. If still nothing, you need to manually enter RESET. Either touch RESET pin to GND or touch SWDIO to GND while powering on.

- I cannot drag and drop anything to my chip. Nothing happens when I press RESET.

You have a virgin chip? This needs to be flashed initially with OpenOCD / Raspberry Pi / Other flasher. I can do this for price of postage.
If you have a board that is or was working, do a quick check... If fitted to console, turn on while pressing VOL+. Is RCM triggered? Then you just need to enter UF2 mode. Refer to first question.
If nothing, you have incredibly managed to corrupt Part 1. Treat as a virgin chip. Connect SWCLK and SWDIO and flash using OpenOCD.
If you have USB port still fitted to board, try plugging into PC and double-pressing RESET.
	
#### TODO: More indepth guide on flashing and usage
	
#### TODO: Raspberry Pi OpenOCD image link here and brief guide.

## Glossary of terms used in this document

- CFW - Custom firmware
- OFW - Original (standard) firmware
- RCM - Special mode of the Switch to do things, probably in the factory. Not normally accessible to end-users. We just it as the special mode required to launch "payloads"
- AutoRCM - Automatically entering RCM mode needed to begin the process of running CFW on the Switch
- Payload - A piece of software that basically boots and does something on the console, exploiting the unit to run code it shouldn't
- ChipRCM - My version of autoRCM. Instead of controlled corrupting of flash storage like other methods, this uses basically the "official" way to achieve RCM, with a chip
- FailsafeRCM - Same as ChipRCM, but automatically disables itself when it cannot do anything eg when plugged into PC (using Fusee-UF2 via a chip is not possible if USB is plugged into PC, resulting the unit being "trapped" in RCM mode. If left in standard autoRCM or ChipRCM mode, the battery will be ran completely flat and damaged potentially). FailsafeRCM addresses this. You MUST have the USB strap connected to take advantage of this.
- SAFE backup - Essential backup of BOOT0/1 and PRODINFO. These contain certificates and calibration data for your console. They are not interchangeable. Google "Brickachu" for more information
- Strap - A wire or conductor linking an input/output of a chip (our SAMD21 we use for Fusee_UF2) to a point on the Switch motherboard, to perform a function. EG VOL+ strap emulates somebody pressing VOL+ button. We use 3. Joycon, Volume and USB. Only Joycon is essential to running CFW. Vol+ is pressed by hand (can be)
- Drop the straps / Drop a strap - Pull a strap to GND, triggering its action

## Why keep working on such a simple piece of software to do a simple job?

- Because I want it right and as problem-free as possible
- It should be easy to use
- And easy to install

## How?

- It builds the payload on-the-fly in a split-second, based on selected settings. Using code from Me, Usbhost, other people from back in the day and the creator of Hekate, and Arduino. Its a combined effort (or it was)

## Doesn't it wear the chip out keeping writing to it?

- Yes, eventually. Maybe. Atmel quote 10,000 write cycles before the chip starts getting dementia. However, this software uses full wear-levelling, and only individual bits are written only when needed, at once, not rewriting the same data over and over, effectively giving us 10000 ^ 15 (we have 15 pages we use, right at the end of the flash) write cycles. Which is probably more than an SD card... I've been using the same SAMD21 test rig, with same chip, since 2018. Written and in use almost daily. Its still fine. Its not written to all the time. You will probably set your options and never change them

## Disclaimer: You should know exactly what you are doing before attempting this modification. It isn't easy - there are really really small points to solder to. No keys or Nintendo copyrighted works are included in this. This is released as open-source, with no warranty given or implied. YOU ONLY HAVE YOURSELF TO BLAME.


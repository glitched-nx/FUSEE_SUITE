#### Versionen von Fusee_UF2 für die Einstellung per Mehrfachdruck (Multiple-press). Identisch mit den anderen Versionen, lediglich das entsprechende EEPROM-Bit wurde von 00 auf 01 (bzw. umgekehrt) geändert, um die Einstellungen per Langdruck (Long-press) zu aktivieren.

#### Bei diesen Versionen lässt sich die Boot-Priorität auf 3 Arten einstellen:

* Dual-Boot
* ChipRCM
* FailsafeRCM (schlägt der Bootvorgang fehl, startet die OFW)

#### Falls jemand eine Version mit nur 2 Optionen (wie früher) bevorzugt, gebt mir einfach Bescheid – oder kompiliert sie euch selbst, indem ihr `#define TRIPLE_BOOT` im Arduino-Quellcode anpasst.

---
---

## Multiple-press settings versions of Fusee_UF2. Identical to other versions but EEPROM bit changed from 00 to 01(or vise-versa) to enable Long-press settings.

#### These versions have the boot priority toggle able to be set in 3 ways

- Dual-boot
- ChipRCM
- FailsafeRCM (if boot fails, OFW will run)

#### If anyone wants a version with just 2 options (as before, let me know) or build yourself, adjusting #define TRIPLE_BOOT in Arduino source.

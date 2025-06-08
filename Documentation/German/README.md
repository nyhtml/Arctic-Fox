# :fox_face: Arctic Fox
*E*in *N*eu entwickelter *C*omputer, *D*er *C*odierung *V*on *O*S *Xcode* *I*ntegriert

## Inhaltsverzeichnis
* [Die Konfiguration](#die-konfiguration)
  * [BIOS-Einstellungen](#bios-einstellungen)
* [Installationsmedium vorbereiten](#installationsmedium-vorbereiten)
* [Bootloader installieren](#bootloader-installieren)
* [Kernel-Erweiterungen](#kernel-erweiterungen)
  * [Erforderlich](#erforderlich)
  * [Nach der Installation](#nach-der-installation)
  * [Optional](#optional)
* [Installation auf dem Bootlaufwerk](#installation-auf-dem-bootlaufwerk)
  * USB-Stick
  * Bootlaufwerk
* [Versionen](#versionen)
* [Kompatibilität](#kompatibilität)
* [Lizenz](#lizenz)
* [Garantie](#garantie)

## Die Konfiguration
Vollständige [Spezifikationen anzeigen](https://www.dualbootpc.com/systems/desktop/arctic-fox/specs/) unter `http://gixxer.us/2Jslljx`

## BIOS-Einstellungen
Bitte das beigefügte Wiki mit der vollständigen Liste der [BIOS-Einstellungen](/English/BIOS.md) ansehen.
 * [M.I.T.](/English/BIOS.md#fox_face-mit)
 * [System](/English/BIOS.md#fox_face-system)
 * [BIOS](/English/BIOS.md#fox_face-bios)
 * [Peripherie](/English/BIOS.md#fox_face-peripherals)
 * [Chipsatz](/English/BIOS.md#fox_face-chipset)
 * [Stromversorgung](/English/BIOS.md#fox_face-power)
 * [Speichern & Beenden](/English/BIOS.md#fox_face-save--exit)

## Installationsmedium vorbereiten
1. Lade das Installationsprogramm für [macOS Sierra](https://www.dualbootpc.com/software/system/macos/sierra/) aus dem Mac App Store herunter.
2. Öffne das Terminal und formatiere das 16 GB [USB-Laufwerk](https://www.dualbootpc.com/hardware/usb/) mit folgendem Befehl:

    `diskutil partitionDisk /dev/{DISK_ID} GPT JHFS+ "SierraUSB" 100%` 
    
3. Partitioniere das [USB-Laufwerk](https://www.dualbootpc.com/hardware/usb/), gib **SierraUSB** 12 GB und **Post Installation** 4 GB.
4. [Erstelle den bootfähigen macOS-Installer](https://www.dualbootpc.com/guide/creating-a-usb-installer/): Anleitungen funktionieren für [OS X Mavericks](https://www.dualbootpc.com/software/system/macos/mavericks/) bis [macOS Monterey](https://www.dualbootpc.com/software/system/macos/monterey/).

    `sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/SierraUSB --applicationpath /Applications/Install\ macOS\ Sierra.app`

5. Nach Abschluss wird dein [USB-Laufwerk](https://www.dualbootpc.com/hardware/usb/) wie folgt benannt:

    `Install macOS Sierra`

## Bootloader installieren
**USB-Stick**
* Lade den [Clover](https://www.dualbootpc.com/software/bootloader/clover/) 2.4k r4934 Installer von [Release v0.1.0](https://github.com/nyhtml/Arctic-Fox/releases/tag/0.1.0) herunter
* Installiere Clover 2.4k r4934 auf dein 16 GB [USB-Laufwerk](https://www.dualbootpc.com/hardware/usb/) mit folgenden Optionen:
  * Clover nur für UEFI-Boot
  * Clover in der ESP installieren
  * UEFI-Treiber:
    * Erforderliche Treiber:
      * ApfsDriverLoader-64.efi
      * AptioMemoryFix-64.efi
      * HFSPlus.efi
    * Empfohlene Treiber:
      * AudioDxe-64.efi (Aktiviert Bootsound bei kompatiblen Themes)
      * NvmExpress-64.efi (Aktiviert NVMe-Erkennung)

**Bootlaufwerk**
* Exportiere **BOOT** und **CLOVER** vom EFI-Ordner des USB-Sticks und importiere sie in den EFI-Ordner des Bootlaufwerks.
* Installiere [Clover 2.5k r5119](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.6.4) auf dem Bootlaufwerk mit den **zusätzlichen Optionen**:
  * RC-Skripte auf Zielvolume installieren
  * Clover-Einstellungsfenster installieren (bei Nachinstallation auswählen)
* Werfe alle USB-Laufwerke aus und starte das BIOS.
* Setze das Bootlaufwerk mit Clover als primäres Gerät und verlasse das BIOS.

## Kernel-Erweiterungen
### [Erforderlich](https://github.com/nyhtml/Arctic-Fox/releases/tag/0.1.0)
  * FakeSMC.kext (Wird in [Release v1.5.0](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.5.0) ersetzt für Big Sur Support)
  * Lili.kext
  * WhateverGreen.kext

### [Nach der Installation](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.1.0)
  * AppleALC.kext
  * IntelMausiEthernet.kext (Wird in [Release v1.5.1](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.5.1) ersetzt)
  * USBInjectAll.kext
  * XHCI-200-series-injector.kext

### [Optional](https://github.com/nyhtml/KEANU)
  * CPUFriend.kext
  * RealtekRTL8111.kext (PCI-e Wi-Fi)
  * RtWlanU.kext (USB Wi-Fi)
  * RtWlanU1827.kext (USB Wi-Fi)

Liste der verfügbaren [kexts](https://www.dualbootpc.com/software/kexts/) auf GixxerPC: `http://gixxer.us/3aS5d6m`

## Installation auf dem Bootlaufwerk
1. Mit [Release v1.5.0](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.5.0) oder älter auf dem 16 GB [USB-Laufwerk](https://www.dualbootpc.com/hardware/usb/), USB-Stick in USB 2.0-Port einstecken und im BIOS als ERSTES/PRIMÄRES Bootlaufwerk festlegen.

2. Vor dem Beenden das Systemdatum auf das [Veröffentlichungsdatum](https://www.dualbootpc.com/guide/release-date/) des entsprechenden macOS setzen.

## Versionen
Sieh dir die aktuellen [Veröffentlichungen](https://github.com/nyhtml/Arctic-Fox/releases) des Projekts an.

## Kompatibilität
* macOS
  * [macOS Big Sur](https://www.dualbootpc.com/software/system/macos/big-sur/)
  * [macOS Catalina](https://www.dualbootpc.com/software/system/macos/mojave/)
  * [macOS Mojave](https://www.dualbootpc.com/software/system/macos/mojave/)
  * [macOS High Sierra](https://www.dualbootpc.com/software/system/macos/high-sierra/)
  * [macOS Sierra](https://www.dualbootpc.com/software/system/macos/sierra/)
* Ubuntu
  * [Ubuntu Desktop](https://www.dualbootpc.com/software/system/ubuntu/desktop/)
* Windows
  * [Windows 11](https://www.dualbootpc.com/software/system/windows/eleven/)
  * [Windows 10](https://www.dualbootpc.com/software/system/windows/ten/)
  * [Windows 8](https://www.dualbootpc.com/software/system/windows/eight/)
  * [Windows 7](https://www.dualbootpc.com/software/system/windows/seven/)

## Lizenz
Details in der veröffentlichten [MIT-Lizenz](https://github.com/nyhtml/Arctic-Fox/blob/main/LICENSE) nachlesen.

## Garantie
DIESES [ARCTIC FOX](https://github.com/nyhtml/Arctic-Fox/) REPOSITORY WIRD "WIE BESEHEN" BEREITGESTELLT, OHNE JEGLICHE GEWÄHRLEISTUNG, WEDER AUSDRÜCKLICH NOCH<br>
STILLSCHWEIGEND, EINSCHLIESSLICH, ABER NICHT BESCHRÄNKT AUF GARANTIEN DER MARKTGÄNGIGKEIT,<br>
EIGNUNG FÜR EINEN BESTIMMTEN ZWECK UND NICHTVERLETZUNG. IN KEINEM FALL SIND DIE<br>
AUTOREN ODER COPYRIGHTINHABER FÜR ANSPRÜCHE, SCHÄDEN ODER SONSTIGE<br>
HAFTUNGEN VERANTWORTLICH, OB IN EINEM VERTRAG, DURCH FAHRLÄSSIGKEIT ODER<br>
ANDERWEITIG, DIE AUS DER VERWENDUNG DER SOFTWARE ENTSTEHEN.

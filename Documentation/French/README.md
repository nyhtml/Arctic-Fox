# :fox_face: Arctic Fox
*U*n *R*é-ordinateur *C*onçu *T*out-en-un *I*ncorporant *C*odage *F*rom *O*S *Xcode*

## Table des Matières
* [La Configuration](#la-configuration)
  * [Paramètres du BIOS](#paramètres-du-bios)
* [Préparer le Support d’Installation](#préparer-le-support-dinstallation)
* [Installer le Bootloader](#installer-le-bootloader)
* [Extensions du Kernel](#extensions-du-kernel)
  * [Obligatoire](#obligatoire)
  * [Post Installation](#post-installation)
  * [Optionnel](#optionnel)
* [Installation sur le Disque de Démarrage](#installation-sur-le-disque-de-démarrage)
  * Clé USB
  * Disque de Démarrage
* [Versions](#versions)
* [Compatibilité](#compatibilité)
* [Licence](#licence)
* [Garantie](#garantie)

## La Configuration
Voir les [spécifications complètes](https://www.dualbootpc.com/systems/desktop/arctic-fox/specs/) : `http://gixxer.us/2Jslljx`

## Paramètres du BIOS
Consultez le wiki pour une liste complète des [paramètres BIOS](/English/BIOS.md).
 * [M.I.T.](/English/BIOS.md#fox_face-mit)
 * [Système](/English/BIOS.md#fox_face-system)
 * [BIOS](/English/BIOS.md#fox_face-bios)
 * [Périphériques](/English/BIOS.md#fox_face-peripherals)
 * [Chipset](/English/BIOS.md#fox_face-chipset)
 * [Alimentation](/English/BIOS.md#fox_face-power)
 * [Enregistrer & Quitter](/English/BIOS.md#fox_face-save--exit)

## Préparer le Support d’Installation
1. Télécharger l’installeur pour [macOS Sierra](https://www.dualbootpc.com/software/system/macos/sierra/) depuis le Mac App Store.
2. Ouvrir Terminal et formater la [clé USB](https://www.dualbootpc.com/hardware/usb/) 16 Go avec la commande suivante :

    `diskutil partitionDisk /dev/{DISK_ID} GPT JHFS+ "SierraUSB" 100%` 

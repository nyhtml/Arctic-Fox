# :fox_face: Arctic Fox  
*O*tro *R*e-diseñado *C*omputador que *I*ncorpora *C*ódigo de *F*uente de *Xcode*  

## Tabla de Contenidos  
* [La Construcción](#la-construcción)  
  * [Configuraciones de BIOS](#configuraciones-de-bios)  
* [Preparar el Medio de Instalación](#preparar-el-medio-de-instalación)  
* [Instalar el Gestor de Arranque](#instalar-el-gestor-de-arranque)  
* [Extensiones del Kernel](#extensiones-del-kernel)  
  * [Obligatorias](#obligatorias)  
  * [Post-instalación](#post-instalación)  
  * [Opcionales](#opcionales)  
* [Instalar en la Unidad de Arranque](#instalar-en-la-unidad-de-arranque)  
  * Unidad USB  
  * Unidad de Arranque  
* [Versiones](#versiones)  
* [Compatibilidad](#compatibilidad)  
* [Licencia](#licencia)  
* [Garantía](#garantía)

## La Construcción  
Consulta las [especificaciones completas](https://www.dualbootpc.com/systems/desktop/arctic-fox/specs/) en `http://gixxer.us/2Jslljx`

## Configuraciones de BIOS  
Consulta la wiki adjunta para ver la lista completa de [configuraciones de BIOS](/English/BIOS.md).  
 * [M.I.T.](/English/BIOS.md#fox_face-mit)  
 * [Sistema](/English/BIOS.md#fox_face-system)  
 * [BIOS](/English/BIOS.md#fox_face-bios)  
 * [Periféricos](/English/BIOS.md#fox_face-peripherals)  
 * [Chipset](/English/BIOS.md#fox_face-chipset)  
 * [Energía](/English/BIOS.md#fox_face-power)  
 * [Guardar y Salir](/English/BIOS.md#fox_face-save--exit)

## Preparar el Medio de Instalación  
1. Descarga el instalador de [macOS Sierra](https://www.dualbootpc.com/software/system/macos/sierra/) desde la Mac App Store.  
2. Abre la Terminal y formatea la [unidad USB](https://www.dualbootpc.com/hardware/usb/) de 16 GB con este comando:  

    `diskutil partitionDisk /dev/{DISK_ID} GPT JHFS+ "SierraUSB" 100%`  

3. Divide la unidad USB: 12 GB para **SierraUSB** y 4 GB para **Post Installation**.  
4. [Crea el instalador USB de macOS](https://www.dualbootpc.com/guide/creating-a-usb-installer/): Funciona desde [OS X Mavericks](https://www.dualbootpc.com/software/system/macos/mavericks/) hasta [macOS Monterey](https://www.dualbootpc.com/software/system/macos/monterey/).  

    `sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/SierraUSB --applicationpath /Applications/Install\ macOS\ Sierra.app`  

5. Una vez finalizado, la unidad USB se llamará:  

    `Install macOS Sierra`  

## Instalar el Gestor de Arranque  

**Unidad USB**  
* Descarga el instalador de [Clover 2.4k r4934](https://www.dualbootpc.com/software/bootloader/clover/) desde [Release v0.1.0](https://github.com/nyhtml/Arctic-Fox/releases/tag/0.1.0)  
* Instala Clover 2.4k r4934 en tu unidad USB de 16 GB con las siguientes opciones:  
  * Clover solo para arranque UEFI  
  * Instalar Clover en ESP  
  * Controladores UEFI  
    * Obligatorios  
      * ApfsDriverLoader-64.efi  
      * AptioMemoryFix-64.efi  
      * HFSPlus.efi  
    * Recomendados  
      * AudioDxe-64.efi (Activa sonido en el arranque si el tema lo permite)  
      * NvmExpress-64.efi (Permite detección de unidad NVMe)  

**Unidad de Arranque**  
* Copia **BOOT** y **CLOVER** desde la carpeta EFI de la unidad USB y pégalos en la carpeta EFI de la unidad de arranque.  
* Instala [Clover 2.5k r5119](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.6.4) en la unidad de arranque con las siguientes opciones **adicionales**:  
  * Instalar scripts RC en volumen objetivo  
  * Instalar panel de preferencias de Clover (selecciónalo durante la post-instalación)  
* Expulsa todas las unidades USB y reinicia al BIOS  
* Establece la unidad de arranque con Clover como primaria y guarda  

## Extensiones del Kernel  
### [Obligatorias](https://github.com/nyhtml/Arctic-Fox/releases/tag/0.1.0)  
  * FakeSMC.kext (Será reemplazado en [v1.5.0](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.5.0) para soporte futuro de Big Sur)  
  * Lili.kext  
  * WhateverGreen.kext  

### [Post-instalación](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.1.0)  
  * AppleALC.kext  
  * IntelMausiEthernet.kext (Será reemplazado en [v1.5.1](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.5.1) para Big Sur)  
  * USBInjectAll.kext  
  * XHCI-200-series-injector.kext  

### [Opcionales](https://github.com/nyhtml/KEANU)  
  * CPUFriend.kext  
  * RealtekRTL8111.kext (Wi-Fi PCI-e)  
  * RtWlanU.kext (Wi-Fi USB)  
  * RtWlanU1827.kext (Wi-Fi USB)  

Consulta la lista de [kexts disponibles](https://www.dualbootpc.com/software/kexts/) en GixxerPC: `http://gixxer.us/3aS5d6m`

## Instalar en la Unidad de Arranque  
1. Con [v1.5.0](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.5.0) o anteriores ya aplicadas a la unidad USB, insértala en un puerto USB 2.0 y selecciónala como primaria en el BIOS.  
2. Antes de salir, cambia la fecha del sistema para coincidir con la [fecha de lanzamiento de macOS](https://www.dualbootpc.com/guide/release-date/)

## Versiones  
Consulta las [últimas versiones](https://github.com/nyhtml/Arctic-Fox/releases) del proyecto.

## Compatibilidad  
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

## Licencia  
Consulta la [Licencia MIT](https://github.com/nyhtml/Arctic-Fox/blob/main/LICENSE) para más detalles.

## Garantía  
Este repositorio de [Arctic Fox](https://github.com/nyhtml/Arctic-Fox/) se proporciona "TAL CUAL", SIN GARANTÍA DE NINGÚN TIPO,  
EXPRESA O IMPLÍCITA, INCLUYENDO PERO NO LIMITADA A GARANTÍAS DE COMERCIABILIDAD,  
ADECUACIÓN A UN PROPÓSITO PARTICULAR Y NO INFRACCIÓN. EN NINGÚN CASO LOS  
AUTORES O TITULARES DE LOS DERECHOS DE AUTOR SERÁN RESPONSABLES DE NINGÚN RECLAMO,  
DAÑO U OTRA RESPONSABILIDAD, YA SEA EN UNA ACCIÓN CONTRACTUAL,  
POR AGRAVIO O DE OTRO TIPO, QUE SURJA DE, FUERA DE O EN RELACIÓN CON  
EL SOFTWARE O EL USO U OTRO TIPO DE ACCIÓN EN EL SOFTWARE.

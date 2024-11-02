#  :fox_face: Arctic Fox
*A*nother *R*e-engineered *C*omputer *T*hat *I*ncorporates *C*oding *F*rom *O*S *Xcode*

## Table of Contents
* [The Build](#the-build)
  * [BIOS Settings](#bios-settings)
* [Prepare Install Media](#prepare-install-media)
* [Install the Bootloader](#install-the-bootloader)
* [Kernel Extensions](#kernel-extensions)
  * [Mandatory](#mandatory)
  * [Post Installation](#post-installation)
  * [Optional](#optional)
* [Install to Boot Drive](#install-to-boot-drive)
  * USB Flash Drive
  * Boot Drive
* [Releases](#releases)
* [Compatibility](#compatibility)
* [License](#license)
* [Warranty](#warranty)

## The Build
View the complete [specs](https://www.dualbootpc.com/systems/desktop/arctic-fox/specs/) at `http://gixxer.us/2Jslljx`

## BIOS Settings
Please look at the wiki I've attached for a complete list of [BIOS Settings](/BIOS.md).
 * [M.I.T.](/BIOS.md#fox_face-mit)
 * [System](/BIOS.md#fox_face-system)
 * [BIOS](/BIOS.md#fox_face-bios)
 * [Peripherals](/BIOS.md#fox_face-peripherals)
 * [Chipset](/BIOS.md#fox_face-chipset)
 * [Power](/BIOS.md#fox_face-power)
 * [Save & Exit](/BIOS.md#fox_face-save--exit)

## Prepare Install Media
1. Download the installer for [macOS Sierra](https://www.dualbootpc.com/software/system/macos/sierra/) from the Mac App Store.
2. Open Terminal and format the target 16 GB [USB drive](https://www.dualbootpc.com/hardware/usb/) with the following command:

    `diskutil partitionDisk /dev/{DISK_ID} GPT JHFS+ "SierraUSB" 100%` 
    
3. Partition the 16 GB [USB drive](https://www.dualbootpc.com/hardware/usb/) and give 12 GB to the **SierraUSB** and 4 GB to **Post Installation**.
4. [Create the bootable macOS installer](https://www.dualbootpc.com/guide/creating-a-usb-installer/): Instructions works for [OS X Mavericks](https://www.dualbootpc.com/software/system/macos/mavericks/) through [macOS Monterey](https://www.dualbootpc.com/software/system/macos/monterey/).

    `sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/SierraUSB --applicationpath /Applications/Install\ macOS\ Sierra.app`
5. Once the program finishes in the Terminal, your [USB drive](https://www.dualbootpc.com/hardware/usb/) will be called the following:

    `Install macOS Sierra`
    
## Install the Bootloader
**USB Flash Drive**
* Download the included [Clover](https://www.dualbootpc.com/software/bootloader/clover/) 2.4k r4934 installer from [Release v0.1.0](https://github.com/Sipylus/Arctic-Fox/releases/tag/0.1.0)
* Install Clover 2.4k r4934 to your 16 GB [USB drive](https://www.dualbootpc.com/hardware/usb/) device and customize with the following options:
  * Clover for UEFI booting only
  * Install Clover in the ESP
  * UEFI Drivers
    * Mandatory drivers
      * ApfsDriverLoader-64.efi
      * AptioMemoryFix-64.efi
      * HFSPlus.efi
    * Recommended drivers
      * AudioDxe-64.efi (Enables Boot Sound in compatible themes)
      * NvmExpress-64.efi (Enabled The Detection of the NVMe drive)

**Boot Drive**
* Export the **BOOT** and the **CLOVER** from the EFI Folder on the USB Flash Drive and import to the EFI Folder on the boot drive.
* Install [Clover 2.5k r5119](https://github.com/Sipylus/Arctic-Fox/releases/tag/1.6.4) to your boot drive and customize with the **additional** options:
  * Install RC Scripts in target volume
  * Install Clover Preference Pane (Select during Post Installation)
* Eject all USB Flash Drives and restart to the BIOS.
* Set the boot drive with Clover as the Primary and exit.
      
## Kernel Extensions
### [Mandatory](https://github.com/Sipylus/Arctic-Fox/releases/tag/0.1.0)
  * FakeSMC.kext (This will be swapped in [Release v1.5.0](https://github.com/Sipylus/Arctic-Fox/releases/tag/1.5.0) for future support of macOS Big Sur.)
  * Lili.kext
  * WhateverGreen.kext

### [Post Installation](https://github.com/Sipylus/Arctic-Fox/releases/tag/1.1.0)
  * AppleALC.kext
  * IntelMausiEthernet.kext (This will be swapped in [Release v1.5.1](https://github.com/Sipylus/Arctic-Fox/releases/tag/1.5.1) for future support of macOS Big Sur.)
  * USBInjectAll.kext
  * XHCI-200-series-injector.kext

### [Optional](https://github.com/nyhtml/KEANU)
  * CPUFriend.kext
  * RealtekRTL8111.kext (PCI-e Wi-Fi)
  * RtWlanU.kext (USB Wi-Fi)
  * RtWlanU1827.kext (USB Wi-Fi)

View the list of [kexts](https://www.dualbootpc.com/software/kexts/) available on GixxerPC: `http://gixxer.us/3aS5d6m`

## Install to Boot Drive
1. With [Release v1.5.0](https://github.com/Sipylus/Arctic-Fox/releases/tag/1.5.0) and earlier applied to the 16GB [USB drive](https://www.dualbootpc.com/hardware/usb/), insert into a USB 2.0 and set as FIRST/PRIMARY in the BIOS settings.

2. Before exiting, change the system date to match the macOS [release date](https://www.dualbootpc.com/guide/release-date/) on the workaround list.

## Releases
See the latest [releases](https://github.com/Sipylus/Arctic-Fox/releases) for the project.

## Compatibility
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

## License
See the posted [MIT License](https://github.com/Sipylus/Arctic-Fox/blob/main/LICENSE) for details.
  
## Warranty
THIS [ARCTIC FOX](https://github.com/Sipylus/Arctic-Fox/) REPO IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR<br>
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,<br>
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE<br>
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER<br>
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,<br>
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE<br>
SOFTWARE.

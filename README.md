# Arctic Fox
*A*nother *R*e-engineered *C*omputer *T*hat *I*ncorporates *C*oding *F*rom *O*S *Xcode*

## Table of Contents

* [The Build](#the-build)
* [Prepare Install Media](#prepare-install-media)
* [Install the Bootloader](#install-the-bootloader)
* [Kernel Extensions](#kernel-extensions)
* [Install to Boot Drive](#install-to-boot-drive)

* [Releases](#releases)
* [License](#license)


## The Build

View the complete [build](https://www.dualbootpc.com/systems/desktop/arctic-fox/specs/) on GixxerPC: http://gixxer.us/2Jslljx

## Prepare Install Media

1. Download the installer for [macOS Sierra](https://www.dualbootpc.com/software/system/macos/sierra/) from the Mac App Store.
2. Open Terminal and format the target 16GB [USB drive](https://www.dualbootpc.com/hardware/usb/) with the following command:

    `diskutil partitionDisk /dev/{DISK_ID} GPT JHFS+ "GixxerUSB" 100%` 
    
3. Partition the 16GB [USB drive](https://www.dualbootpc.com/hardware/usb/) and give 12 GB to the GixxerUSB and 4GB to Post Installation.
4. [Create the bootable macOS installer](https://www.dualbootpc.com/guide/creating-a-usb-installer/): Works for [OS X Mavericks](https://www.dualbootpc.com/software/system/macos/mavericks/) through [macOS Big Sur](https://www.dualbootpc.com/software/system/macos/big-sur/).

    `sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/GixxerUSB /Applications/Install\ macOS\ Sierra.app`
5. Once the program finishes, your [USB drive](https://www.dualbootpc.com/hardware/usb/) should now be called the following:

    `Install macOS Sierra`
    
## Install the Bootloader

Configure Clover *Clobber Edition*

* Download the included [Clover](https://www.dualbootpc.com/software/bootloader/clover/) 2.4k r4934 installer from [Release v0.1.0](https://github.com/Sipylus/Arctic-Fox/releases/tag/0.1.0)
* Install Clover 2.4k r4934 to your 16GB [USB drive](https://www.dualbootpc.com/hardware/usb/) device and customize with the following options:
  * Clover for UEFI booting only
  * Install Clover in the ESP
  * UEFI Drivers
    * Recommended drivers
      * ApfsDriverLoader-64.efi
      * HFSPlus.efi
      * OsxAptioFix3Drv-64.efi
    * Optional drivers
      * AudioDxe-64.efi (Enables Boot Sound in compatible themes)
  * Install RC Scripts in target volume
  * Install Clover Preference Pane
      
## Kernel Extensions

* Mandatory from [Release v.0.1.0](https://github.com/Sipylus/Arctic-Fox/releases/tag/0.1.0)
  * FakeSMC.kext (This will be swapped in [Release v1.5.0](https://github.com/Sipylus/Arctic-Fox/releases/tag/1.5.0) for future support of macOS Big Sur.)
  * Lili.kext
  * WhateverGreen.kext

* Post Installation from [Release v.1.1.0](https://github.com/Sipylus/Arctic-Fox/releases/tag/1.1.0)
  * AppleALC.kext
  * IntelMausiEthernet.kext
  * USBInjectAll.kext
  * XHCI-200-series-injector.kext

View the list of [kexts](https://www.dualbootpc.com/software/kexts/) available on GixxerPC: http://gixxer.us/3aS5d6m

## Install to Boot Drive

1. With [Release v1.5.0](https://github.com/Sipylus/Arctic-Fox/releases/tag/1.5.0) and earlier applied to the 16GB [USB drive](https://www.dualbootpc.com/hardware/usb/), insert into a USB 2.0 and set as FIRST/PRIMARY in the BIOS settings.

2. Before exiting the BIOS, change the system date to match the [release date](https://www.dualbootpc.com/guide/release-date/) on workaround list.

## BIOS Settings

<details><summary>M.I.T.</summary>

</details>
<details><summary>System</summary>

</details>
<details><summary>BIOS</summary>

</details>
<details><summary>Peripherals</summary>

</details>
<details><summary>Chipset</summary>

</details>
<details><summary>Power</summary>

</details>
<details><summary>Save &amp; Exit</summary>

</details>

## Releases

See the latest [releases](https://github.com/Sipylus/Arctic-Fox/releases) for the project.

## Compatibility

Up to [macOS Big Sur 11.1] on its own boot drive.
  
## License
  
See the posted [MIT License](https://github.com/Sipylus/Arctic-Fox/blob/main/LICENSE) for details.
  
## Warranty
  
THIS [ARCTIC FOX](https://github.com/Sipylus/Arctic-Fox/)  REPO IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR<br>
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,<br>
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE<br>
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER<br>
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,<br>
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE<br>
SOFTWARE.

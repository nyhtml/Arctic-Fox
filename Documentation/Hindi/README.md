# :fox_face: आर्कटिक फॉक्स  
*E*k *N*या *C*omputer *J*ो *Xcode* से *Coding* *I*ntegrate करता है  

## सामग्री सूची  
* [निर्माण विवरण](#निर्माण-विवरण)  
  * [BIOS सेटिंग्स](#bios-सेटिंग्स)  
* [इंस्टॉलेशन मीडिया तैयार करें](#इंस्टॉलेशन-मीडिया-तैयार-करें)  
* [बूटलोडर इंस्टॉल करें](#बूटलोडर-इंस्टॉल-करें)  
* [कर्नेल एक्सटेंशन्स](#कर्नेल-एक्सटेंशन्स)  
  * [अनिवार्य](#अनिवार्य)  
  * [इंस्टॉलेशन के बाद](#इंस्टॉलेशन-के-बाद)  
  * [वैकल्पिक](#वैकल्पिक)  
* [बूट ड्राइव पर इंस्टॉल करें](#बूट-ड्राइव-पर-इंस्टॉल-करें)  
  * USB फ्लैश ड्राइव  
  * बूट ड्राइव  
* [रिलीज़](#रिलीज़)  
* [संगतता](#संगतता)  
* [लाइसेंस](#लाइसेंस)  
* [वारंटी](#वारंटी)

## निर्माण विवरण  
[स्पेसिफिकेशन देखें](https://www.dualbootpc.com/systems/desktop/arctic-fox/specs/) — `http://gixxer.us/2Jslljx`

## BIOS सेटिंग्स  
[BIOS सेटिंग्स की पूरी सूची](/English/BIOS.md) के लिए संलग्न विकी देखें।  
 * [M.I.T.](/English/BIOS.md#fox_face-mit)  
 * [System](/English/BIOS.md#fox_face-system)  
 * [BIOS](/English/BIOS.md#fox_face-bios)  
 * [Peripherals](/English/BIOS.md#fox_face-peripherals)  
 * [Chipset](/English/BIOS.md#fox_face-chipset)  
 * [Power](/English/BIOS.md#fox_face-power)  
 * [Save & Exit](/English/BIOS.md#fox_face-save--exit)

## इंस्टॉलेशन मीडिया तैयार करें  
1. [macOS Sierra](https://www.dualbootpc.com/software/system/macos/sierra/) को मैक ऐप स्टोर से डाउनलोड करें।  
2. टर्मिनल खोलें और नीचे दिए गए कमांड से 16GB [USB ड्राइव](https://www.dualbootpc.com/hardware/usb/) को फॉर्मेट करें:  
    `diskutil partitionDisk /dev/{DISK_ID} GPT JHFS+ "SierraUSB" 100%`  
3. 12GB को **SierraUSB** और 4GB को **Post Installation** के लिए विभाजित करें।  
4. [बूटेबल macOS इंस्टॉलर बनाएं](https://www.dualbootpc.com/guide/creating-a-usb-installer/): यह Mavericks से Monterey तक कार्य करता है।  
    `sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/SierraUSB --applicationpath /Applications/Install\ macOS\ Sierra.app`  
5. टर्मिनल में प्रोसेस पूरी होने पर, आपका [USB ड्राइव](https://www.dualbootpc.com/hardware/usb/) इस नाम से दिखाई देगा:  
    `Install macOS Sierra`

## बूटलोडर इंस्टॉल करें  

**USB फ्लैश ड्राइव**  
* [Clover 2.4k r4934](https://www.dualbootpc.com/software/bootloader/clover/) को [Release v0.1.0](https://github.com/nyhtml/Arctic-Fox/releases/tag/0.1.0) से डाउनलोड करें  
* इसे अपने 16GB [USB ड्राइव](https://www.dualbootpc.com/hardware/usb/) पर नीचे दी गई सेटिंग्स के साथ इंस्टॉल करें:  
  * केवल UEFI बूट के लिए Clover  
  * ESP में Clover इंस्टॉल करें  
  * आवश्यक UEFI ड्राइवर:  
    * ApfsDriverLoader-64.efi  
    * AptioMemoryFix-64.efi  
    * HFSPlus.efi  
  * अनुशंसित ड्राइवर:  
    * AudioDxe-64.efi  
    * NvmExpress-64.efi  

**बूट ड्राइव**  
* USB से EFI फोल्डर से **BOOT** और **CLOVER** को एक्सपोर्ट करें और बूट ड्राइव के EFI फोल्डर में इंपोर्ट करें।  
* [Clover 2.5k r5119](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.6.4) को इंस्टॉल करें और निम्न अतिरिक्त विकल्प चुनें:  
  * RC स्क्रिप्ट्स को टारगेट वॉल्यूम पर इंस्टॉल करें  
  * Clover प्रेफरेंस पैन इंस्टॉल करें (Post Installation के दौरान चुनें)  
* सभी USB ड्राइव्स को हटाएं और BIOS में जाएं  
* Clover वाले बूट ड्राइव को प्राथमिक बूट स्रोत सेट करें  

## कर्नेल एक्सटेंशन्स  
### [अनिवार्य](https://github.com/nyhtml/Arctic-Fox/releases/tag/0.1.0)  
  * FakeSMC.kext  
  * Lili.kext  
  * WhateverGreen.kext  

### [इंस्टॉलेशन के बाद](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.1.0)  
  * AppleALC.kext  
  * IntelMausiEthernet.kext  
  * USBInjectAll.kext  
  * XHCI-200-series-injector.kext  

### [वैकल्पिक](https://github.com/nyhtml/KEANU)  
  * CPUFriend.kext  
  * RealtekRTL8111.kext  
  * RtWlanU.kext  
  * RtWlanU1827.kext  

GixxerPC पर उपलब्ध [kexts की सूची](https://www.dualbootpc.com/software/kexts/): `http://gixxer.us/3aS5d6m`

## बूट ड्राइव पर इंस्टॉल करें  
1. [v1.5.0](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.5.0) या उससे पहले की रिलीज को USB ड्राइव पर लागू करें, USB 2.0 पोर्ट में डालें, और BIOS में इसे प्राथमिकता दें।  
2. BIOS छोड़ने से पहले, सिस्टम दिनांक को macOS के [रिलीज डेट](https://www.dualbootpc.com/guide/release-date/) से मिलाएं।

## रिलीज़  
[नवीनतम रिलीज़ देखें](https://github.com/nyhtml/Arctic-Fox/releases)

## संगतता  
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

## लाइसेंस  
[MIT लाइसेंस](https://github.com/nyhtml/Arctic-Fox/blob/main/LICENSE) देखें

## वारंटी  
यह [Arctic Fox](https://github.com/nyhtml/Arctic-Fox/) रिपोज़िटरी "जैसा है" आधार पर दी जाती है, **बिना किसी प्रकार की वारंटी के**,  
**न तो व्यक्त की गई और न ही निहित**, जिनमें बाज़ार में बिक्री योग्य होने,  
विशेष प्रयोजन के लिए उपयुक्तता और उल्लंघन से मुक्त होने की वारंटी शामिल हैं।  
किसी भी स्थिति में लेखक या कॉपीराइट धारक किसी दावे, नुकसान या अन्य  
दायित्व के लिए जिम्मेदार नहीं होंगे, चाहे वह अनुबंध, क्षति या अन्य तरीके से  
उत्पन्न हुआ हो, सॉफ़्टवेयर या उसके उपयोग या अन्य लेन-देन से संबंधित हो।

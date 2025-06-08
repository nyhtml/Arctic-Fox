# :fox_face: Arctic Fox  
*Xcode* からの *コード* を *組み込んだ*、もう一つの *再設計されたコンピュータ*

## 目次
* [構成](#構成)  
  * [BIOS 設定](#bios-設定)  
* [インストールメディアの準備](#インストールメディアの準備)  
* [ブートローダーのインストール](#ブートローダーのインストール)  
* [カーネル拡張](#カーネル拡張)  
  * [必須](#必須)  
  * [ポストインストール](#ポストインストール)  
  * [オプション](#オプション)  
* [ブートドライブへのインストール](#ブートドライブへのインストール)  
  * USB フラッシュドライブ  
  * ブートドライブ  
* [リリース](#リリース)  
* [互換性](#互換性)  
* [ライセンス](#ライセンス)  
* [保証](#保証)

## 構成
[完全な仕様](https://www.dualbootpc.com/systems/desktop/arctic-fox/specs/) をご覧ください: `http://gixxer.us/2Jslljx`

## BIOS 設定
[BIOS 設定の詳細](/English/BIOS.md) は Wiki をご参照ください。  
 * [M.I.T.](/English/BIOS.md#fox_face-mit)  
 * [システム](/English/BIOS.md#fox_face-system)  
 * [BIOS](/English/BIOS.md#fox_face-bios)  
 * [周辺機器](/English/BIOS.md#fox_face-peripherals)  
 * [チップセット](/English/BIOS.md#fox_face-chipset)  
 * [電源](/English/BIOS.md#fox_face-power)  
 * [保存して終了](/English/BIOS.md#fox_face-save--exit)

## インストールメディアの準備
1. Mac App Store から [macOS Sierra](https://www.dualbootpc.com/software/system/macos/sierra/) をダウンロードしてください。  
2. ターミナルを開き、以下のコマンドで16GBの[USBドライブ](https://www.dualbootpc.com/hardware/usb/)をフォーマット：  
   `diskutil partitionDisk /dev/{DISK_ID} GPT JHFS+ "SierraUSB" 100%`

3. **SierraUSB** に 12GB、**Post Installation** に 4GB を割り当ててパーティション分割  
4. [macOS ブータブルインストーラを作成](https://www.dualbootpc.com/guide/creating-a-usb-installer/)  
   `sudo /Applications/Install\ macOS\ Sierra.app/Contents/Resources/createinstallmedia --volume /Volumes/SierraUSB --applicationpath /Applications/Install\ macOS\ Sierra.app`  
5. 実行後、USBドライブは次のように表示されます：  
   `Install macOS Sierra`

## ブートローダーのインストール
**USB フラッシュドライブ**  
* [Clover 2.4k r4934](https://www.dualbootpc.com/software/bootloader/clover/) を [v0.1.0 リリース](https://github.com/nyhtml/Arctic-Fox/releases/tag/0.1.0) からダウンロード  
* 以下のオプションで Clover を USB にインストール：  
  * UEFIブート専用  
  * ESPにインストール  
  * UEFIドライバ  
    * 必須ドライバ：ApfsDriverLoader, AptioMemoryFix, HFSPlus  
    * 推奨ドライバ：AudioDxe, NvmExpress  

**ブートドライブ**  
* USB の EFI フォルダから **BOOT** と **CLOVER** をコピーし、ブートドライブの EFI フォルダに貼り付け  
* [Clover 2.5k r5119](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.6.4) をブートドライブにインストールし、以下の追加オプションを選択：  
  * RC スクリプトをインストール  
  * Clover 設定パネルをインストール  
* USB を取り外し、BIOS へ再起動  
* Clover を使ったドライブを優先起動に設定し保存して終了

## カーネル拡張
### [必須](https://github.com/nyhtml/Arctic-Fox/releases/tag/0.1.0)  
  * FakeSMC.kext  
  * Lili.kext  
  * WhateverGreen.kext  

### [ポストインストール](https://github.com/nyhtml/Arctic-Fox/releases/tag/1.1.0)  
  * AppleALC.kext  
  * IntelMausiEthernet.kext  
  * USBInjectAll.kext  
  * XHCI-200-series-injector.kext  

### [オプション](https://github.com/nyhtml/KEANU)  
  * CPUFriend.kext  
  * RealtekRTL8111.kext  
  * RtWlanU.kext  
  * RtWlanU1827.kext  

## ブートドライブへのインストール
1. v1.5.0 を適用した USB を USB2.0 に挿入し、BIOS 設定で最初のブートに設定  
2. macOS の[リリース日](https://www.dualbootpc.com/guide/release-date/)に一致するよう、日付を設定

## リリース
[リリース一覧](https://github.com/nyhtml/Arctic-Fox/releases) を参照

## 互換性
* macOS（Big Sur, Catalina, Mojave, High Sierra, Sierra）  
* Ubuntu Desktop  
* Windows 11, 10, 8, 7

## ライセンス
[MIT ライセンス](https://github.com/nyhtml/Arctic-Fox/blob/main/LICENSE) を参照

## 保証
この [Arctic Fox](https://github.com/nyhtml/Arctic-Fox/) リポジトリは、「現状のまま」提供され、いかなる保証もありません。  
明示的または黙示的な商業適合性、特定目的への適合性、非侵害に関しても同様です。

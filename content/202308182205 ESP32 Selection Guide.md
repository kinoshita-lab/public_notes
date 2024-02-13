# 202308182205 ESP32 Selection Guide


#ESP32 #electronics #電子工作

[[202309031354 ESP32]]
## 202309115時点での結論

- WROOM, WROVERとも、末尾のアルファベットが後半の方が、リビジョンが上。チップバグなど修正されているので、そちらを採用。
- 基本的には、 WROOM32Eを使う。
- PSRAMが必要なら、 WROVERを使う。
- RISC-V気になるが、Xtensa Coreを選ぶのが良さそう。

cf.
<https://lang-ship.com/blog/work/esp32-series/>


## WROOM-32 WROOM-32D WROOM-32E

<https://tech.144lab.com/entry/esp32-wroom32-nrnd>
32, 32Dは NRND Not Recommended for New Designs
32Eを使おう

32、32Dとの違い
<https://tech.144lab.com/entry/esp32-wroom32-nrnd>
> 未接続になったピンはSDカードがつながる6つのピンで、すでに内部でSPI Flashがつながっているため、32の時から外部で何かに使うのが非推奨になっていました。

## WROOMとWROVERは何が違う？

WROVERには[[20230915 PSRAM]](疑似SRAM)というものが乗っている。

## WROOVER-B WROOVER-E

<https://esp32.com/viewtopic.php?t=15904>
E are newer with rev 3 chips

## その他気になること

USB-Serialのオプション

- CH340C
- CP2102

## 秋月で買えそうなやつ

### ESP32-DevKitC-32E ESP32-WROOM-32E開発ボード 4MB

推奨。 32Eだし。
いわゆるESP32、4MB Dual
![](2023-08-18-22-17-38.png)
<https://akizukidenshi.com/catalog/g/gM-15673/>

MCU
• ESP32-D0WD-V3 embedded, Xtensa® dual-core 32-bit LX6 microprocessor, up to 240 MHz
• 448 KB ROM for booting and core functions
• 520 KB SRAM for data and instructions
• 16 KB SRAM in RT

## ESP32-DevKitC-VE ESP32-WROVER-E開発ボード 8MB

![](2023-08-18-22-16-31.png)
<https://akizukidenshi.com/catalog/g/gM-15674/>

## ESP-WROOM-32D開発ボード

![](2023-08-18-22-15-52.png)
<https://akizukidenshi.com/catalog/g/gM-13628/>
テクノよしださんはこれを使っているとのこと。

ESP32-WROOM-32とESP32-WROOM-32Dの違いを教えてください。
<https://akizukidenshi.com/catalog/faq/goodsfaq.aspx?goods=M-13628>

> ESP32-WROOM-32[M-11647]とESP32-WROOM-32D[M-13318]では、 電気的、ソフトウェア的、ファームウェア的、無線プロファイル的な技術仕様に変更はありません。 変更点は、下記4点です。
>
> ① SoC(ESP32チップ)のパッケージサイズが変更になりました。
>　ESP32-WROOM-32: QFN 6x6
>　ESP32-WROOM-32D: QFN 5x5
> ② 面実装部品(抵抗とコンデンサ)のパッケージサイズが変更になりました。
>　ESP32-WROOM-32Dでは、小型サイズの部品が使用されています。
> ③ アンテナパターンが変更されました。
>　ESP32-WROOM-32Dでは、パターンが太くなっています。
> ④ 工事設計認証（技適）番号が変更になりました。
>　ESP32-WROOM-32: 211-161007
>　ESP32-WROOM-32D: 211-171102

ESP32-S3-DevKitC-1
![](2023-08-18-22-15-01.png)
<https://akizukidenshi.com/catalog/g/gM-17073/>

ESP32-C6-DevKitC-1。
![](2023-08-18-22-14-24.png)![](2023-08-18-22-14-27.png)
<https://akizukidenshi.com/catalog/g/gM-17846/>
入手性はあまりよくなさそう。
<https://docs.espressif.com/projects/espressif-esp-dev-kits/en/latest/esp32c6/esp32-c6-devkitc-1/index.html>

## Ali

### 1個38ピンタイプ-cesp32 ESP-WROOM-32 cp2102開発ボード2.4ghzデュアルコア

NRND(Not Recommended for New Designs)
<https://ja.aliexpress.com/item/1005005455717981.html?spm=a2g0o.order_list.order_list_main.11.21ef585agpnRvr&gatewayAdapt=glo2jpn>

## Platform IO

wroom32の各リビジョン、wroover、どれでも下記でいけるのではないか？(要検証)

```.ini
[env:esp32dev]
platform = espressif32
board = esp32dev
framework = arduino
```

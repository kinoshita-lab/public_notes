# 20240204221948 raspberry piをSSD bootに設定
#raspi #ssd
色々と情報を見たが、一番簡単で確実な方法は、
- microSDにRaspberry Pi Imagerで必要なOSを書きこむ
- SSDをRaspberry Pi Imagerで必要なOSを書きこむ 20240204 時点ではraspi-cloneではうまくいかなかった。
- microSDでブート、bootloaderを最新にする
- raspi-configで起動をSSDに設定
という手順が確実そう。

#### SSDのフォーマット
SSDをUSBで接続。認識されると、こんな感じになる。

```
$ dmesg
[ 2371.382886] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2555.521771] usb 2-2: USB disconnect, device number 3
[ 2555.565777] sd 0:0:0:0: [sda] Synchronizing SCSI cache
[ 2555.801704] sd 0:0:0:0: [sda] Synchronize Cache(10) failed: Result: hostbyte=0x07 driverbyte=DRIVER_OK
[ 2627.619831] usb 2-2: new SuperSpeed USB device number 4 using xhci_hcd
[ 2627.652398] usb 2-2: New USB device found, idVendor=0bda, idProduct=9210, bcdDevice=f0.01
[ 2627.652420] usb 2-2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2627.652433] usb 2-2: Product: RTL9210
[ 2627.652442] usb 2-2: Manufacturer: Realtek
[ 2627.652451] usb 2-2: SerialNumber: 012345678905
[ 2627.684644] usb 2-2: Enable of device-initiated U1 failed.
[ 2627.685583] usb 2-2: Enable of device-initiated U2 failed.
[ 2627.714973] usb 2-2: Enable of device-initiated U1 failed.
[ 2627.716024] usb 2-2: Enable of device-initiated U2 failed.
[ 2627.720692] scsi host0: uas
[ 2628.284123] scsi 0:0:0:0: Direct-Access     Realtek  RTL9210 NVME     1.00 PQ: 0 ANSI: 6
[ 2628.302746] sd 0:0:0:0: Attached scsi generic sg0 type 0
[ 2628.306857] sd 0:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[ 2628.308244] sd 0:0:0:0: [sda] Write Protect is off
[ 2628.308260] sd 0:0:0:0: [sda] Mode Sense: 37 00 00 08
[ 2628.310966] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2628.312278] sd 0:0:0:0: [sda] Preferred minimum I/O size 512 bytes
[ 2628.312300] sd 0:0:0:0: [sda] Optimal transfer size 33553920 bytes
[ 2628.324088]  sda: sda1 sda2
[ 2628.324372] sd 0:0:0:0: [sda] Attached SCSI disk
[ 2753.358307]  sda: sda1 sda2
```

fdiskで全部のパーティーションを削除。状況によって異なるので割愛。
#### bootloaderのバージョン確認
```
$ vcgencmd bootloader_version
2023/01/11 17:40:52
version 8ba17717fbcedd4c3b6d4bce7e50c7af4155cba9 (release)
timestamp 1673458852
update-time 0
capabilities 0x0000007f
```

`sudo raspi-config`

A7 Boot ROM Versionを最新に。
`E1 Latest Use the latest version boot ROM software` を選択して再起動。

```
$ vcgencmd bootloader_version
2024/01/22 10:41:21
version 51ed67b03b3dde4e76b345370f312d07aabf45b8 (release)
timestamp 1705920081
update-time 1707048097
capabilities 0x0000007f
```

ここまでできたら、USBブートにする。最初の手順で作ったSSDをraspi4に接続。microSDは外して起動。

どのくらい速度違うか、簡単に調べてみた。
```
$ sudo hdparm -tT /dev/mmcblk0 # マイクロSD

/dev/mmcblk0:
 Timing cached reads:   2048 MB in  2.00 seconds = 1024.23 MB/sec
 Timing buffered disk reads: 132 MB in  3.02 seconds =  43.70 MB/sec

$ sudo hdparm -tT /dev/sda # SSD
/dev/sda:
 Timing cached reads:   2034 MB in  2.00 seconds = 1017.23 MB/sec
 Timing buffered disk reads: 1020 MB in  3.06 seconds = 333.44 MB/sec
```
約 7.6倍くらい高速になっている。素晴しい

cf.
- [ラズパイ4をUSB接続のSSDから起動する方法(USBブート) | ラズパイダ](https://raspida.com/rpi4-ssd-usb-boot)
- [Raspberry PiのバックアップをCLIから作成する | Vogelbarsch](https://vogelbarsch.com/2020-08-27-140104/)
- [Rasberry Piでrpi-cloneを使ってバックアップ | TomoSoft](https://tomosoft.jp/design/?p=8721)
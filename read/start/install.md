---
title: 如何安裝「Ventoy」到「USB隨身碟」
nav_order: 1020
has_children: false
parent: 入門
---


# 如何安裝「Ventoy」到「USB隨身碟」


延續前面[如何下載「Ventoy」](download)，

接下來要安裝「Ventoy」到「隨身碟」。

## 隨身碟資訊

在安裝前，先來了解，我準備的隨身碟資訊

我的隨身碟是位在「/dev/sdc」。

執行下面指令

``` sh
sudo lsblk | grep sdc
```

顯示

```
sdc      8:32   1 115.2G  0 disk
```

執行下面指令

``` sh
sudo blkid /dev/sdc
```

顯示

```
/dev/sdc: PTUUID="039f6e6d" PTTYPE="dos"
```

執行下面指令

``` sh
sudo fdisk -l /dev/sdc
```

顯示

```
Disk /dev/sdc: 115.24 GiB, 123730388992 bytes, 241660916 sectors
Disk model: DataTraveler 3.0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x039f6e6d
```

執行

``` sh
sudo parted /dev/sdc print
```

顯示

```
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start  End  Size  Type  File system  Flags
```

## 操作步驟


執行下面指令，切換到「ventoy-1.0.71」這個資料夾。

``` sh
cd ventoy-1.0.71
```

執行

``` sh
sudo ./Ventoy2Disk.sh -h
```

或是執行

``` sh
sudo sh Ventoy2Disk.sh -h
```

顯示

```

**********************************************
      Ventoy: 1.0.71  x86_64
      longpanda admin@ventoy.net
      https://www.ventoy.net
**********************************************

Usage:  Ventoy2Disk.sh CMD [ OPTION ] /dev/sdX
  CMD:
   -i  install Ventoy to sdX (fails if disk already installed with Ventoy)
   -I  force install Ventoy to sdX (no matter installed or not)
   -u  update Ventoy in sdX
   -l  list Ventoy information in sdX

  OPTION: (optional)
   -r SIZE_MB  preserve some space at the bottom of the disk (only for install)
   -s/-S       enable/disable secure boot support (default is disabled)
   -g          use GPT partition style, default is MBR (only for install)
   -L          Label of the 1st exfat partition (default is Ventoy)
   -n          try non-destructive installation (only for install)

```

執行下面指令，安裝「Ventoy」到「隨身碟」的操作步驟。

執行

``` sh
sudo ./Ventoy2Disk.sh -i /dev/sdc
```

或是執行

``` sh
sudo sh Ventoy2Disk.sh -i /dev/sdc
```

會先顯示

```

**********************************************
      Ventoy: 1.0.71  x86_64
      longpanda admin@ventoy.net
      https://www.ventoy.net
**********************************************

Disk : /dev/sdc
Model: Kingston DataTraveler 3.0 (scsi)
Size : 115 GB
Style: MBR


Attention:
You will install Ventoy to /dev/sdc.
All the data on the disk /dev/sdc will be lost!!!

Continue? (y/n)
```

這時候輸入「y」，並且按下「Enter」。

接著會在顯示下面訊息

```
All the data on the disk /dev/sdc will be lost!!!
Double-check. Continue? (y/n)
```

這時候一樣輸入「y」，並且按下「Enter」。

接著會顯示

```

Create partitions on /dev/sdc by parted in MBR style ...
Done
Wait for partitions ...
partition exist OK
create efi fat fs /dev/sdc2 ...
mkfs.fat 4.1 (2017-01-24)
success
Wait for partitions ...
/dev/sdc1 exist OK
/dev/sdc2 exist OK
partition exist OK
Format partition 1 /dev/sdc1 ...
mkexfatfs 1.3.0
Creating... done.
Flushing... done.
File system created successfully.
mkexfatfs success
writing data to disk ...
sync data ...
esp partition processing ...
Open ventoy efi file 0x610ac0
ventoy x64 efi file size 1785856 ...
Open bootx64 efi file 0x610ac0
Open ventoy ia32 efi file 0x610f10
ventoy efi file size 1204224 ...
Open bootia32 efi file 0x610ac0

Install Ventoy to /dev/sdc successfully finished.

```

這時候就已經安裝完成了。

接下來只是觀看安裝好後，隨身碟相關的資訊。

執行下面指令

``` sh
sudo fdisk /dev/sdc -l
```

顯示

```
Disk /dev/sdc: 115.24 GiB, 123730388992 bytes, 241660916 sectors
Disk model: DataTraveler 3.0
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x83fed5be

Device     Boot     Start       End   Sectors   Size Id Type
/dev/sdc1  *         2048 241595375 241593328 115.2G  7 HPFS/NTFS/exFAT
/dev/sdc2       241595376 241660911     65536    32M ef EFI (FAT-12/16/32)
```

執行下面指令

``` sh
sudo parted /dev/sdc print
```

顯示

```
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End    Size    Type     File system  Flags
 1      1049kB  124GB  124GB   primary               boot
 2      124GB   124GB  33.6MB  primary  fat16        esp
```

執行下面指令

``` sh
sudo lsblk | grep sdc
```

顯示

```
sdc      8:32   1 115.2G  0 disk
├─sdc1   8:33   1 115.2G  0 part
└─sdc2   8:34   1    32M  0 part
```

執行下面指令

``` sh
sudo blkid /dev/sdc
```

顯示

```
/dev/sdc: PTUUID="83fed5be" PTTYPE="dos"
```

執行下面指令

``` sh
sudo blkid /dev/sdc1
```

顯示

```
/dev/sdc1: LABEL="Ventoy" UUID="758B-CE47" TYPE="exfat" PTTYPE="dos" PARTUUID="83fed5be-01"
```

執行下面指令

``` sh
sudo blkid /dev/sdc2
```

顯示

```
/dev/sdc2: SEC_TYPE="msdos" LABEL_FATBOOT="VTOYEFI" LABEL="VTOYEFI" UUID="DE2E-30BF" TYPE="vfat" PARTUUID="83fed5be-02"
```

接下來，可以使用「pcmanfm-qt」或是「thunar」等掛載剛剛的隨身碟，或是將隨身碟拔出再插入，就會自動掛載。


執行下面指令

``` sh
sudo lsblk | grep sdc
```

顯示

```
sdc      8:32   1 115.2G  0 disk
├─sdc1   8:33   1 115.2G  0 part /media/sam/Ventoy
└─sdc2   8:34   1    32M  0 part
```

就會掛載在「/media/sam/Ventoy」這個資料夾

> 因為我的登入帳號是「sam」

執行

``` sh
id -un
```

顯示

```
sam
```

所以要在您的環境，找到類似「/media/sam/Ventoy」這個路徑

可以執行下面指令，

``` sh
echo /media/$(id -un)/Ventoy
```

顯示

```
/media/sam/Ventoy
```

執行

``` sh
ls /media/$(id -un)/Ventoy
```


## 下載ISO檔案

執行下面指令，切換到「/media/sam/Ventoy」這個資料夾


``` sh
cd /media/$(id -un)/Ventoy
```

執行下面指令，下載測試的「ISO檔案」到「/media/sam/Ventoy」這個資料夾

``` sh
wget -c https://cdimage.ubuntu.com/xubuntu/releases/20.04/release/xubuntu-20.04.4-desktop-amd64.iso
wget -c https://cdimage.debian.org/debian-cd/current-live/amd64/iso-hybrid/debian-live-11.2.0-amd64-xfce.iso
wget -c https://download.manjaro.org/xfce/21.2.5/manjaro-xfce-21.2.5-220314-linux515.iso
wget -c https://free.nchc.org.tw/arch/iso/2022.01.01/archlinux-2022.01.01-x86_64.iso
```

下載完畢後，接著重新開機，在「BIOS」選擇「隨身碟」開機，就會出現「GRUB開機選單」，

就會有剛剛下載的四個ISO開機選項可供選擇。

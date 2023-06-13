---
title: 如何安裝「Ventoy」到「USB隨身碟」，並且預留「額外硬碟空間」
nav_order: 1040
has_children: false
parent: 入門
---


# 如何安裝「Ventoy」到「USB隨身碟」，並且預留「額外硬碟空間」


## 前提

延續[如何安裝「Ventoy」到「USB隨身碟」](https://samwhelp.github.io/note-about-ventoy/read/start/install.html)，接下來介紹「如何在安裝時，預留額外硬碟空間」。

其中有一個選項

```
   -r SIZE_MB  preserve some space at the bottom of the disk (only for install)
```

以下範例，假設要預留「30GB」，也就是「30x1024=30720MB」。


## 操作步驟

* [安裝](#安裝)
* [確認](#確認)
* [預留硬碟空間建立分割區](#預留硬碟空間建立分割區)
* [格式化分割區](#格式化分割區)
* [再次確認](#再次確認)


## 安裝

第一次安裝，執行下面指令

``` sh
sudo ./Ventoy2Disk.sh -i /dev/sdc -r 30720
```


重新安裝，則是執行下面指令

``` sh
sudo ./Ventoy2Disk.sh -I /dev/sdc -r 30720
```


## 確認

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

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  91.7GB  91.7GB  primary               boot
 2      91.7GB  91.8GB  33.6MB  primary  fat16        esp
```

執行下面指令

``` sh
sudo parted /dev/sdc print free
```

顯示

```
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
        1024B   1049kB  1048kB           Free Space
 1      1049kB  91.7GB  91.7GB  primary               boot
 2      91.7GB  91.8GB  33.6MB  primary  fat16        esp
        91.8GB  124GB   32.2GB           Free Space

```

或是也可以執行下面指令

``` sh
sudo cfdisk /dev/sdc
```

會看到其中有如下的資訊

```

    Device      Boot       Start         End     Sectors    Size   Id Type
>>  /dev/sdc1   *           2048   179175423   179173376   85.4G    7 HPFS/NTFS/exFAT
    /dev/sdc2          179175424   179240959       65536     32M   ef EFI (FAT-12/16/32)
    Free space         179240960   242155520    62914561     30G

```

## 預留硬碟空間建立分割區

> 將「額外預留硬碟空間」，建立「分割區」

``` sh
sudo parted --script /dev/sdc -- \
    mkpart primary 91.8GB '-1' \
    print
```

> 關於「91.8GB」可以從上面「Free Space」的「Start」找到

> 關於「'-1'」指的是「End」到「最後」。

> 關於「--」，是因為要下「'-1'」，這樣才不會出錯。可以參考「man bash」找到「--」的用法。

完成後會顯示

```
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  91.7GB  91.7GB  primary               boot
 2      91.7GB  91.8GB  33.6MB  primary  fat16        esp
 3      91.8GB  124GB   32.2GB  primary
```


## 格式化分割區

執行下面指令，將「/dev/sdc3」格式化

``` sh
sudo mkfs.ext4 -F /dev/sdc3
```


## 再次確認

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

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  91.7GB  91.7GB  primary               boot
 2      91.7GB  91.8GB  33.6MB  primary  fat16        esp
 3      91.8GB  124GB   32.2GB  primary  ext4

```

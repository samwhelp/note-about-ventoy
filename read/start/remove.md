---
title: 如何移除「Ventoy」
nav_order: 1050
has_children: false
parent: 入門
---


# 如何移除「Ventoy」


## 方式一

> 執行下面指令，建立新的「磁碟分割表」，不建立「分割區」。

``` sh
sudo parted --script -- "/dev/sdc" \
	mktable gpt \
	print free
```

顯示

```
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size   File system  Name  Flags
        17.4kB  124GB  124GB  Free Space
```


## 方式二

> 執行下面指令，建立新的「磁碟分割表」，並建立「一個分割區」。

``` sh
sudo parted --script -- "/dev/sdc" \
	mktable gpt \
	mkpart primary 1M '-1' \
	print
```

或是執行下面的指令 (上面「-1」改成「100%」，同等效用)

``` sh
sudo parted --script -- "/dev/sdc" \
	mktable gpt \
	mkpart primary 1M '100%' \
	print
```


顯示

```
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size   File system  Name     Flags
 1      1049kB  124GB  124GB               primary
```

若是要將剛剛建立的分割區「/dev/sdc1」，格式化成「ext4」的格式，執行下面指令

``` sh
sudo mkfs.ext4 -F /dev/sdc1
```

若是要將剛剛建立的分割區「/dev/sdc1」，格式化成「fat32」的格式，執行下面指令

``` sh
sudo mkfs.fat -F32 /dev/sdc1
```

格式化完成後，可以執行下面指令確認

``` sh
sudo parted /dev/sdc print
```

若是「ext4」，顯示如下

```
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size   File system  Name     Flags
 1      1049kB  124GB  124GB  ext4         primary
```

若是「fat32」，顯示如下

```
Model: Kingston DataTraveler 3.0 (scsi)
Disk /dev/sdc: 124GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags:

Number  Start   End    Size   File system  Name     Flags
 1      1049kB  124GB  124GB  fat32        primary
```


也可以執行下面指令，連同「Free Space」的部份顯示出來。

``` sh
sudo parted /dev/sdc print free
```


## 其他分割法的參考指令

> 以下「'-1'」，可以改成「'100%'」，同等效用。

執行下面指令

``` sh
sudo parted --script -- "/dev/sdc" \
	mktable gpt \
	mkpart primary 1M '50%' \
	mkpart primary '50%' '-1' \
	print
```

或是執行下面指令

``` sh
sudo parted --script -- "/dev/sdc" \
	mktable gpt \
	mkpart primary 1M '50%' \
	mkpart primary '50%' '100%' \
	print
```

執行下面指令

``` sh
sudo parted --script -- "/dev/sdc" \
	mktable gpt \
	mkpart primary 1M 2M \
	mkpart primary 2M '-1' \
	set 1 bios_grub on \
	print
```

執行下面指令

``` sh
sudo parted --script -- "/dev/sdc" \
	mktable gpt \
	mkpart primary 1M 2M \
	mkpart primary 2M '50%' \
	mkpart primary '50%' '-1' \
	set 1 bios_grub on \
	print
```

執行下面指令

``` sh
sudo parted --script -- "/dev/sdc" \
	mktable gpt \
	mkpart primary 1M 2M \
	mkpart primary 2M '30%' \
	mkpart primary '30%' '60%' \
	mkpart primary '60%' '-1' \
	set 1 bios_grub on \
	print
```

執行下面指令

``` sh
sudo parted --script -- "/dev/sdc" \
	mktable gpt \
	mkpart primary 1M 2M \
	mkpart primary 2M '33%' \
	mkpart primary '33%' '66%' \
	mkpart primary '66%' '-1' \
	set 1 bios_grub on \
	print
```


## Manpage

* man [parted](https://man.archlinux.org/man/parted.8.en)


## Help

執行

``` sh
sudo parted /dev/sdc help
```

執行

``` sh
sudo parted /dev/sdc help help
```

執行

``` sh
sudo parted /dev/sdc help mktable
```

執行

``` sh
sudo parted /dev/sdc help mkpart
```

執行

``` sh
sudo parted /dev/sdc help print
```


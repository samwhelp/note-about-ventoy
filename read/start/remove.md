---
title: 如何移除「Ventoy」
nav_order: 1050
has_children: false
parent: 入門
---


# 如何移除「Ventoy」


## 方式一

執行下面指令，建立新的「分割表」，不建立「分割區」。

``` sh
sudo parted --script "/dev/sdc" -- \
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


執行下面指令，建立新的「分割表」，並建立「一個分割區」。

``` sh
sudo parted --script "/dev/sdc" -- \
	mktable gpt \
	mkpart primary 1M '-1' \
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

或是也可以執行下面指令

``` sh
sudo parted --script "/dev/sdc" -- \
	mktable gpt \
	mkpart primary ext4 1M '-1' \
	print
```

執行下面指令，格式化剛剛建立的分割區

``` sh
sudo mkfs.ext4 -F /dev/sdc1
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


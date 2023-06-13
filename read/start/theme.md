---
title: 如何更改「Ventoy」的「佈景主題」
nav_order: 1030
has_children: false
parent: 入門
---


# 如何更改「Ventoy」的「佈景主題」

延續前面[如何安裝「Ventoy」到「USB隨身碟」](install)，

接下來紀錄，如何更換開機選單的佈景主題，

## 執行步驟

* [下載](#下載)
* [安裝](#安裝)
* [概覽](#概覽)

## BigSur GRUB Theme

* [BigSur GRUB Theme](https://www.gnome-look.org/p/1443844/) ([GitHub](https://github.com/Teraskull/bigsur-grub2-theme))

## 下載

執行下面指令

``` sh
git clone https://github.com/Teraskull/bigsur-grub2-theme.git
```

## 安裝

執行下面指令

``` sh
cp -rf bigsur-grub2-theme/ventoy/. /run/media/$(id -un)/Ventoy/ventoy
```

或是

``` sh
cp -rf bigsur-grub2-theme/ventoy/. /var/run/media/$(id -un)/Ventoy/ventoy
```

> 操作步驟到此就更換完成了，就可以直接重新開機，選擇裝有「Ventoy」的「隨身碟」來觀看結果。


## 概覽

以下是觀看相關的資訊。

執行

``` sh
ls -1 /run/media/$(id -un)/Ventoy/ventoy
```

顯示

```
themes
ventoy.json
```

執行

``` sh
tree /run/media/$(id -un)/Ventoy/ventoy
```

顯示

```
/run/media/sam/Ventoy/ventoy
├── themes
│   └── bigsur
│       ├── background.png
│       ├── boot_menu_c.png
│       ├── boot_menu_e.png
│       ├── boot_menu_ne.png
│       ├── boot_menu_n.png
│       ├── boot_menu_nw.png
│       ├── boot_menu_se.png
│       ├── boot_menu_s.png
│       ├── boot_menu_sw.png
│       ├── boot_menu_w.png
│       ├── DejaVuSans-48.pf2
│       ├── DejaVuSans-Regular-14.pf2
│       ├── icons
│       │   ├── antergos.png
│       │   ├── archlinux.png
│       │   ├── arch.png
│       │   ├── arcolinux.png
│       │   ├── bsd.png
│       │   ├── cancel.png
│       │   ├── chakra.png
│       │   ├── clonezilla.png
│       │   ├── crunchbang.png
│       │   ├── debian.png
│       │   ├── deepin.png
│       │   ├── devuan.png
│       │   ├── driver.png
│       │   ├── edit.png
│       │   ├── edubuntu.png
│       │   ├── efi.png
│       │   ├── elementary.png
│       │   ├── endeavouros.png
│       │   ├── fedora.png
│       │   ├── find.efi.png
│       │   ├── find.none.png
│       │   ├── frugalware.png
│       │   ├── gentoo.png
│       │   ├── gnu-linux.png
│       │   ├── help.png
│       │   ├── iso.png
│       │   ├── kali.png
│       │   ├── kaos.png
│       │   ├── kbd.png
│       │   ├── korora.png
│       │   ├── kubuntu.png
│       │   ├── lang.png
│       │   ├── lfs.png
│       │   ├── linuxmint.png
│       │   ├── linux.png
│       │   ├── lubuntu.png
│       │   ├── macosx.png
│       │   ├── mageia.png
│       │   ├── Manjaro.i686.png
│       │   ├── manjaro.png
│       │   ├── Manjaro.x86_64.png
│       │   ├── memtest.png
│       │   ├── opensuse.png
│       │   ├── pop-os.png
│       │   ├── recovery.png
│       │   ├── restart.png
│       │   ├── sabayon.png
│       │   ├── shutdown.png
│       │   ├── siduction.png
│       │   ├── solus.png
│       │   ├── steamos.png
│       │   ├── type.png
│       │   ├── tz.png
│       │   ├── ubuntu.png
│       │   ├── unknown.png
│       │   ├── unset.png
│       │   ├── void.png
│       │   ├── win11.png
│       │   ├── windows.png
│       │   ├── winvista.png
│       │   ├── winxp.png
│       │   ├── xubuntu.png
│       │   └── zorin-os.png
│       ├── item_c.png
│       ├── item_e.png
│       ├── item_ne.png
│       ├── item_n.png
│       ├── item_nw.png
│       ├── item_se.png
│       ├── item_s.png
│       ├── item_sw.png
│       ├── item_w.png
│       ├── password_field.png
│       ├── select_c.png
│       ├── select_e.png
│       ├── select_ne.png
│       ├── select_n.png
│       ├── select_nw.png
│       ├── select_se.png
│       ├── select_s.png
│       ├── select_sw.png
│       ├── select_w.png
│       ├── slider_c.png
│       ├── slider_n.png
│       ├── slider_s.png
│       ├── terminal_c.png
│       ├── terminal_e.png
│       ├── terminal_ne.png
│       ├── terminal_n.png
│       ├── terminal_nw.png
│       ├── terminal_se.png
│       ├── terminal_s.png
│       ├── terminal_sw.png
│       ├── terminal_w.png
│       ├── terminus-12.pf2
│       ├── terminus-14.pf2
│       ├── terminus-16.pf2
│       └── theme.txt
└── ventoy.json

4 directories, 111 files
```

執行下面指令，觀看「[Ventoy/ventoy/ventoy.json](https://github.com/Teraskull/bigsur-grub2-theme/blob/master/ventoy/ventoy.json)」的內容

``` sh
cat /run/media/$(id -un)/Ventoy/ventoy/ventoy.json
```

顯示

```
{
    "theme": {
        "file": "/ventoy/themes/bigsur/theme.txt",
        "gfxmode": "1920x1080",
        "display_mode": "GUI",
        "serial_param": "--unit=0 --speed=9600",
        "ventoy_left": "5%",
        "ventoy_top": "95%",
        "ventoy_color": "#eff0f1",
        "fonts": [
            "/ventoy/themes/bigsur/terminus-12.pf2",
            "/ventoy/themes/bigsur/terminus-14.pf2",
            "/ventoy/themes/bigsur/terminus-16.pf2",
            "/ventoy/themes/bigsur/DejaVuSans-48.pf2",
            "/ventoy/themes/bigsur/DejaVuSans-Regular-14.pf2"
        ]
    },
    "menu_class": [
        {
            "key": "kubuntu",
            "class": "kubuntu"
        },
        {
            "key": "ubuntu",
            "class": "ubuntu"
        },
        {
            "key": "pop-os",
            "class": "pop-os"
        },
        {
            "key": "arch",
            "class": "arch"
        },
        {
            "key": "linuxmint",
            "class": "linuxmint"
        },
        {
            "key": "opensuse",
            "class": "opensuse"
        },
        {
            "key": "elementary",
            "class": "elementary"
        },
        {
            "key": "manjaro",
            "class": "manjaro"
        },
        {
            "key": "debian",
            "class": "debian"
        },
        {
            "key": "deepin",
            "class": "deepin"
        },
        {
            "key": "solus",
            "class": "solus"
        },
        {
            "key": "zorin-os",
            "class": "zorin-os"
        },
        {
            "key": "antergos",
            "class": "antergos"
        },
        {
            "key": "archlinux",
            "class": "archlinux"
        },
        {
            "key": "arcolinux",
            "class": "arcolinux"
        },
        {
            "key": "chakra",
            "class": "chakra"
        },
        {
            "key": "crunchbang",
            "class": "crunchbang"
        },
        {
            "key": "devuan",
            "class": "devuan"
        },
        {
            "key": "edubuntu",
            "class": "edubuntu"
        },
        {
            "key": "endeavouros",
            "class": "endeavouros"
        },
        {
            "key": "fedora",
            "class": "fedora"
        },
        {
            "key": "frugalware",
            "class": "frugalware"
        },
        {
            "key": "gentoo",
            "class": "gentoo"
        },
        {
            "key": "gnu-linux",
            "class": "gnu-linux"
        },
        {
            "key": "kali",
            "class": "kali"
        },
        {
            "key": "kaos",
            "class": "kaos"
        },
        {
            "key": "korora",
            "class": "korora"
        },
        {
            "key": "lubuntu",
            "class": "lubuntu"
        },
        {
            "key": "macosx",
            "class": "macosx"
        },
        {
            "key": "mageia",
            "class": "mageia"
        },
        {
            "key": "Manjaro.i686",
            "class": "Manjaro.i686"
        },
        {
            "key": "manjaro",
            "class": "manjaro"
        },
        {
            "key": "Manjaro.x86_64",
            "class": "Manjaro.x86_64"
        },
        {
            "key": "Manjaro.x86_64",
            "class": "Manjaro.x86_64"
        },
        {
            "key": "sabayon",
            "class": "sabayon"
        },
        {
            "key": "siduction",
            "class": "siduction"
        },
        {
            "key": "steamos",
            "class": "steamos"
        },
        {
            "key": "void",
            "class": "void"
        },
        {
            "key": "xubuntu",
            "class": "xubuntu"
        },
        {
            "key": "win11",
            "class": "win11"
        },
        {
            "key": "winxp",
            "class": "winxp"
        },
        {
            "key": "winvista",
            "class": "winvista"
        },
        {
            "key": "windows",
            "class": "windows"
        },
        {
            "key": "hirens",
            "class": "windows"
        },
        {
            "key": "memtest",
            "class": "memtest"
        },
        {
            "key": "bsd",
            "class": "bsd"
        },
        {
            "key": "driver",
            "class": "driver"
        },
        {
            "key": "efi",
            "class": "efi"
        },
        {
            "key": "clonezilla",
            "class": "clonezilla"
        },
        {
            "key": "iso",
            "class": "iso"
        }
    ]
}
```

## 參考文章

* [[教學] 多重開機隨身碟製作工具 – Ventoy (1.0.14)](https://izaka.tw/ventoy-bootable-usb-solution-user-guide/)
* [要如何套用 Ventoy 多重開機系統選單主題 (2020.7)](https://izaka.tw/ventoy-theme-apply-guide/)
* [Ventoy 教學，新世代USB重灌工具，支援WinPE/Linux](https://www.gdaily.org/23174/ventoy-iso)
* Ventoy / Docs / [Ventoy Theme Plugin](https://www.ventoy.net/en/plugin_theme.html) ([中文](https://www.ventoy.net/cn/plugin_theme.html))

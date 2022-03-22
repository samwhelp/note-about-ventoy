---
title: 如何更改「Ventoy」的「佈景主題」
nav_order: 1030
has_children: false
parent: 入門
---


# 如何更改「Ventoy」的「佈景主題」

延續前面[如何安裝「Ventoy」到「USB隨身碟」](install)，

接下來紀錄，如何更換開機選單的佈景主題，


## BigSur GRUB Theme

* [BigSur GRUB Theme](https://www.gnome-look.org/p/1443844/) ([GitHub](https://github.com/Teraskull/bigsur-grub2-theme))

執行下面指令

``` sh
git clone https://github.com/Teraskull/bigsur-grub2-theme.git
```

執行下面指令

``` sh
cp bigsur-grub2-theme/ventoy /media/$(id -un)/Ventoy -a
```

就更換完成了，可以重開機

以下是觀看相關的資訊。

執行

``` sh
ls /media/$(id -un)/Ventoy/ventoy -1
```

顯示

```
themes
ventoy.json
```

執行

``` sh
tree /media/$(id -un)/Ventoy/ventoy
```

顯示

```
/media/sam/Ventoy/ventoy
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
│       │   ├── windows.png
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

3 directories, 107 files
```

執行下面指令，觀看「[Ventoy/ventoy/ventoy.json](https://github.com/Teraskull/bigsur-grub2-theme/blob/master/ventoy/ventoy.json)」的內容

``` sh
cat /media/$(id -un)/Ventoy/ventoy/ventoy.json
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
            "key": "windows",
            "class": "windows"
        },
        {
            "key": "hirens",
            "class": "windows"
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

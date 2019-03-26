---
layout: post
title: arch心路历程（一）
key: 20181210
tags: arch
---

## 安装arch
这个比较简单，这儿介绍EFI引导+GPT分区表，首先查看下自己是不是这种方式：
```bash
ls /sys/firmware/efi/efivars
```
回车后有内容可以access那就是EFI方式引导的了。然后既然是GPT的话全新的硬盘我当时fdisk时分区EFI引导区需要输入g创建一个全新的gpt分区表。

<!--more-->

安装完成后桌面选择有很多种，因为我发现很多桌面都会基于gnome，所以后来就装的gnome，装的比较主流的桌面，安装gnome时也可以选择性安装它自带的一些软件，我选择性安装了一些最基本的，gnome-extra就只安装了Tweaks。

在这个安装过程中把一些包提前安装好：
```bash
pacman -S vim dialog wpa_supplicant networkmanager
```
当时我没有安装dialog结果连不上网，然后又借助自己U盘arch-chroot在那个环境下装好然后才行。

桌面安装完成后配置下pacman.conf:
```
[archlinuxcn]
SigLevel = Optional TrustAll
Server = https://mirrors.tuna.tsinghua.edu.cn/archlinuxcn/$arch
```
输入法选择安装fcitx-sogoupinyin，所以pacman -S fcitx-im fcitx-configtool fcitx-sogoupinyin
在/etc/environment中添加如下内容：
```
GTK_IM_MODULE=fcitx
QT_IM_MODULE=fcitx
XMODIFIERS=@im=fcitx
```
要使用sougou还需要在图形界面时打开fcitx-configuration把Sougou Pinyin添加进去。
包管理AUR我选择yay，因为名字短好记：
```
git clone https://aur.archlinux.org/yay.git
cd yay
makepkg -si
```
用yay -S google-chrome visual-studio-code-bin把我喜欢的两个软件装上。

后续美化推荐dash-to-dock，no-title-bar等插件。



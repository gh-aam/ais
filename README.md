# `mAIS`

### `Part 1 @ {Installation}`
root@archiso ~ # iwctl   
[iwd]# station wlan0 connect "**?**"   
Passphrase: **?**   
[iwd]# exit   
root@archiso ~ # ping archlinux.org   
root@archiso ~ # fdisk /dev/sda   
root@archiso ~ # mkfs.btrfs /dev/sda3   
root@archiso ~ # mkswap /dev/sda4   
root@archiso ~ # mount /dev/sda3 /mnt   
root@archiso ~ # btrfs su cr /mnt/@   
root@archiso ~ # btrfs su cr /mnt/@home   
root@archiso ~ # umount -R /mnt   
root@archiso ~ # mount -o defaults,noatime,compress=zstd,commit=120,subvol=@ /dev/sda3 /mnt   
root@archiso ~ # mkdir -p /mnt/{boot,home}   
root@archiso ~ # mount -o defaults,noatime,compress=zstd,commit=120,subvol=@home /dev/sda3 /mnt/home   
root@archiso ~ # mount /dev/sda3 /mnt/boot   
root@archiso ~ # swapon /dev/sda4   
root@archiso ~ # pacstrap -K /mnt base linux linux-headers linux-firmware btrfs-progs intel-ucode grub nano xorg-server plasma konsole git base-devel vivaldi vivaldi-ffmpeg-codecs   
root@archiso ~ # genfstab -U /mnt >> /mnt/etc/fstab   
root@archiso ~ # arch-chroot /mnt   
[root@archiso /]# ln -sf /usr/share/zoneinfo/Asia/Dhaka /etc/localtime   
[root@archiso /]# hwclock --systohc   
[root@archiso /]# nano /etc/locale.gen   
en_US.UTF-8 UTF-8   
[root@archiso /]# locale-gen   
[root@archiso /]# echo LANG=en_US.UTF-8 >> /etc/locale.conf   
[root@archiso /]# echo archlinux >> /etc/hostname   
[root@archiso /]# nano /etc/hosts   
```
127.0.0.1        localhost
::1              localhost
127.0.1.1        archlinux
```
[root@archiso /]# systemctl enable NetworkManager.service   
[root@archiso /]# systemctl enable wpa_supplicant.service   
[root@archiso /]# systemctl enable sddm.service   
[root@archiso /]# passwd   
[root@archiso /]# grub-install /dev/sda   
[root@archiso /]# grub-mkconfig -o /boot/grub/grub.cfg   
[root@archiso /]# useradd -mG wheel aam   
[root@archiso /]# passwd aam   
[root@archiso /]# EDITOR=nano visudo   
%wheel ALL=(ALL:ALL) ALL   
[root@archiso /]# nano /etc/pacman.conf   
UseSyslog   
Color   
CheckSpace   
VerbosePkgLists   
[multilib]   
Include = /etc/pacman.d/mirrorlist   
[root@archiso /]# pacman -Syyuu   
[root@archiso /]# pacman -Scc   
[root@archiso /]# exit   
root@archiso ~ # umount -R /mnt   
root@archiso ~ # reboot   
...........................................................................................



>>> Part 2: Minimal Selected Packages

a) Arch Linux with KDE Plasma:
yay -S exfatprogs ntfs-3g os-prober grub-btrfs dolphin sweeper ksysguard yakuake noto-fonts-emoji khelpcenter appmenu-gtk-module ufw packagekit-qt5 packagekit-qt6 timeshift

b) Arch Linux with KDE Plasma and Chaotic-AUR:
yay -S exfatprogs ntfs-3g os-prober grub-btrfs dolphin sweeper ksysguard yakuake noto-fonts-emoji khelpcenter appmenu-gtk-module ufw packagekit-qt5 packagekit-qt6 timeshift
...........................................................................................

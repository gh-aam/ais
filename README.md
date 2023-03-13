### `OS Installation @ {Part 1}`
```
iwctl
```
```
station wlan0 connect "Wireless Network Name"
```
```
exit
```
```
ping archlinux.org
```
```
fdisk /dev/sda
```
```
mkfs.btrfs /dev/sda3
```
```
mkswap /dev/sda4
```
```
mount /dev/sda3 /mnt
```
```
btrfs su cr /mnt/@
```
```
btrfs su cr /mnt/@home
```
```
umount -R /mnt
```
```
mount -o defaults,noatime,compress=zstd,commit=120,subvol=@ /dev/sda3 /mnt
```
```
mkdir -p /mnt/{boot,home}
```
```
mount -o defaults,noatime,compress=zstd,commit=120,subvol=@home /dev/sda3 /mnt/home
```
```
mount /dev/sda3 /mnt/boot
```
```
swapon /dev/sda4
```
```
pacstrap -K /mnt base linux linux-headers linux-firmware btrfs-progs intel-ucode grub nano xorg-server plasma konsole git base-devel vivaldi vivaldi-ffmpeg-codecs
```
```
genfstab -U /mnt >> /mnt/etc/fstab
```
```
arch-chroot /mnt
```
```
ln -sf /usr/share/zoneinfo/Asia/Dhaka /etc/localtime
```
```
hwclock --systohc
```
```
nano /etc/locale.gen
```
```
en_US.UTF-8 UTF-8
```
```
locale-gen
```
```
echo LANG=en_US.UTF-8 >> /etc/locale.conf
```
```
echo myHostname >> /etc/hostname
```
```
nano /etc/hosts
```
```
127.0.0.1        localhost
::1              localhost
127.0.1.1        myHostname
```
```
systemctl enable NetworkManager.service
```
```
systemctl enable wpa_supplicant.service
```
```
systemctl enable sddm.service
```
```
passwd
```
```
grub-install /dev/sda
```
```
grub-mkconfig -o /boot/grub/grub.cfg
```
```
useradd -mG wheel myUsername
```
```
passwd myUsername
```
```
EDITOR=nano visudo
```
<pre>
%wheel ALL=(ALL:ALL) ALL   
</pre>
```
nano /etc/pacman.conf
```
<pre>
UseSyslog   
Color   
CheckSpace   
VerbosePkgLists   
[multilib]   
Include = /etc/pacman.d/mirrorlist   
</pre>
```
pacman -Syyuu
```
```
pacman -Scc
```
```
exit
```
```
umount -R /mnt
```
```
reboot
```

### `Packages Installation @ {Part 2}`
**a) Arch Linux with KDE Plasma:**
```
yay -S exfatprogs ntfs-3g os-prober grub-btrfs dolphin sweeper ksysguard yakuake noto-fonts-emoji khelpcenter appmenu-gtk-module ufw packagekit-qt5 packagekit-qt6 timeshift safeeyes python-croniter
```
**b) Arch Linux with KDE Plasma and Chaotic-AUR:**
```
yay -S exfatprogs ntfs-3g os-prober grub-btrfs dolphin sweeper ksysguard yakuake noto-fonts-emoji khelpcenter appmenu-gtk-module ufw packagekit-qt5 packagekit-qt6 timeshift safeeyes python-croniter
```

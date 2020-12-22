# linux-image-oem-5.6.0-1020-kernel-ubuntu-x86_64-deb-package
linux-image-oem-5.6.0-1020 , kernel , ubuntu , x86_64 , deb , dual gpu , eGPU , nvidia dlss 3.0 , superior image quality , super high color , package ( build original module nvidia-440.100 , nvidia-uvm.ko , nvidia-modeset.ko , nvidia-drm.ko , nvidia.ko ) , ( build original module zfs-dkms-0.8.3 , icp.ko , spl.ko , zavl.ko , zcommon.ko , zfs.ko , zlua.ko , znvpair.ko , zunicode.ko , support anbox snap , support openafs , support fs zfs rpool , bpool)

kernel linux-image-oem-5.6.0-1020 deb all download: https://github.com/Griggorii/linux-image-oem-5.6.0-1020-kernel-ubuntu-x86_64-deb-package/releases/tag/5.6.0

New kernel 5.9.2 low memory https://github.com/Griggorii/linux-image-5.9.2_amd64.deb_light_zstd_ultra_fast_kernel_memory_super_low

Download fix securetty command | sudo cp -r securetty /etc

Download anacrontab default command | sudo cp -r anacrontab /etc

Mesa graphics https://github.com/Griggorii/mesa-20.1.2_V15-libdrm_ubuntu-19.04-20.04-20.10_X86_64_full_stack_graphics

Данное ядро linux-image-oem-5.6.0-1020 поддерживает драйвера от nvidia , snapd и много других вещей , но для его компиляции я использовал dev от своего предыдущего ядра который это не поддерживает linux-libc-dev_5.8.8 от https://github.com/Griggorii/linux-image-kernel-5.8.8-zstd-dkms-support-light-kernel-x86_64

Original build video driver core + zfs module nvidia-440.100-zfs-my-build-driver.tar.xz nvidia-440.100 , nvidia-uvm.ko , nvidia-modeset.ko , nvidia-drm.ko , nvidia.ko 

hmm variant nvidia-drm: 

inpack nvidia-440.100-zfs-my-build-driver.tar.xz run in terminal folder nvidia/440.100/5.6.0-1020-oem/x86_64/module

$$ sudo mkdir /lib/modules/5.6.0-1020-oem/updates

$$ sudo mkdir /lib/modules/5.6.0-1020-oem/updates/dkms

$$ sudo cp -r  nvidia-uvm.ko nvidia-modeset.ko nvidia-drm.ko nvidia.ko /lib/modules/5.6.0-1020-oem/updates/dkms

$$ sudo apt update && sudo apt --reinstall install xserver-xorg-video-nouveau nvidia-prime bumblebee-nvidia bbswitch-dkms bumblebee primus-libs -y && sudo apt purge xserver-xorg-video-nouveau -y && sudo apt --reinstall install xserver-xorg-video-nvidia-440 libnvidia-cfg1-440 nvidia-settings -y

$$ cat  << EOF > nvidia-kms.conf
options nvidia-drm modeset=1
EOF

$$ sudo mv nvidia-kms.conf /lib/modprobe.d

install nvidia-kernel-source-440_440.100-0ubuntu0.20.04.1_amd64.deb nvidia-kernel-common-440_440.100-0ubuntu0.20.04.1_amd64.deb  nvidia-dkms-440_440.100-0ubuntu0.20.04.1_amd64.deb

Edit grub

/etc/default/grub edit string | GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 crashkernel=false rhgb quiet splash nvidia-drm.modeset=1"

$$ sudo update-initramfs -u -v && sudo update-grub

Reboot command

$$ ubuntu-drivers devices

$$ dmesg |grep nvidia

$$ inxi -G

$$ lspci -vnn | grep -A12 '\''[030[02]\]' | grep -Ei "vga|3d|display|kernel"

Run /var/log/gpu-manager.log

Tutorial redirect display driver https://askubuntu.com/questions/264247/proprietary-nvidia-drivers-with-efi-on-mac-to-prevent-overheating/613573#613573

Looking for nvidia modules in /lib/modules/5.6.0-1020-oem/updates/dkms
Found nvidia module: nvidia-drm.ko

https://github.com/Griggorii/linux-image-oem-5.6.0-1020-kernel-ubuntu-x86_64-deb-package/blob/master/Nvidia-Optimus.png

Далее не на чем просто работать по скольку нету ноутбука или пк в котором есть карта нвидиа за место optimus технологии , на оптимусе может и не показать что nvidia-drm работает по скольку это огрызок видео чипа.

Test kernel+moodule original nvidia-drm perfomance tester s youtuber s send rezultate benchmark link youtube video griggoriigmail.com and send alternative notify https://www.youtube.com/channel/UC6WtVfU5gi2CQ4ionzbz1CQ?view_as=subscriber

Recommended OS https://github.com/Griggorii/Linux_OS20.04_V2_X64_By_Griggorii.iso_ubuntu_focal_fossa-linux-image-5.4.0-29 

Not recommended ubuntu groovy very poor memory handling and swap partitions when building groovy hangs 



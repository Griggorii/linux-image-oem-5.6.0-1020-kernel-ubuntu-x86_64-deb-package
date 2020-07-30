# linux-image-oem-5.6.0-1020-kernel-ubuntu-x86_64-deb-package
linux-image-oem-5.6.0-1020 , kernel , ubuntu , x86_64 , deb , package ( build original module nvidia-440.100 , nvidia-uvm.ko , nvidia-modeset.ko , nvidia-drm.ko , nvidia.ko ) , ( build original module zfs-dkms-0.8.3 , icp.ko , spl.ko , zavl.ko , zcommon.ko , zfs.ko , zlua.ko , znvpair.ko , zunicode.ko)

kernel linux-image-oem-5.6.0-1020 download: https://yadi.sk/d/f8YrUOtvdnD6gA

Download fix securetty command | sudo cp -r securetty /etc

Download anacrontab default command | sudo cp -r anacrontab /etc

Mesa graphics https://github.com/Griggorii/mesa-20.1.2_V15-libdrm_ubuntu-19.04-20.04-20.10_X86_64_full_stack_graphics

Данное ядро linux-image-oem-5.6.0-1020 поддерживает драйвера от nvidia , snapd и много других вещей , но для его компиляции я использовал dev от своего предыдущего ядра который это не поддерживает linux-libc-dev_5.8.8 от https://github.com/Griggorii/linux-image-kernel-5.8.8-zstd-dkms-support-light-kernel-x86_64

Original build video driver core + zfs module nvidia-440.100-zfs-my-build-driver.tar.xz nvidia-440.100 , nvidia-uvm.ko , nvidia-modeset.ko , nvidia-drm.ko , nvidia.ko 

hmm variant: 

$$ sudo mkdir /lib/modules/5.6.0-1020-oem/updates

$$ sudo mkdir /lib/modules/5.6.0-1020-oem/updates/dkms

$$ sudo cp -r  nvidia-uvm.ko nvidia-modeset.ko nvidia-drm.ko nvidia.ko /lib/modules/5.6.0-1020-oem/updates/dkms

$$ cat  << EOF > nvidia-kms.conf
options nvidia-drm modeset=1
EOF

$$ sudo mv nvidia-kms.conf /lib/modprobe.d

Edit grub

/etc/default/grub edit string | GRUB_CMDLINE_LINUX_DEFAULT="ipv6.disable=1 crashkernel=false rhgb quiet splash nvidia-drm.modeset=1"

$$ sudo update-initramfs -u -v && sudo update-grub

Reboot command

$$ ubuntu-drivers devices

$$ inxi -G

$$ lspci -vnn | grep -A12 '\''[030[02]\]' | grep -Ei "vga|3d|display|kernel"

Run /var/log/gpu-manager.log

Looking for nvidia modules in /lib/modules/5.6.0-1020-oem/updates/dkms
Found nvidia module: nvidia-drm.ko

Далее не на чем просто работать по скольку нету ноутбука или пк в котором есть карта нвидиа за место optimus технологии , на оптимусе может и не показать что nvidia-drm работает по скольку это огрызок видео чипа.



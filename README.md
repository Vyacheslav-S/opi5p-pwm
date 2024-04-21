# OrangePi 5 plus PWM fan control
Controller for controlling the fan speed (4 pin PWM) depending on the SOC temperature for OrangePi 5 Plus.

Tested and works on Arch Linux Arm.

### 1. It is necessary to add rk3588-pwm14-m2.dtbo for PWM control on the 7 pin board

extlinux.conf:

```
DEFAULT linux-aarch64-rockchip-bsp6.1-joshua-git
LABEL	linux-aarch64-rockchip-bsp6.1-joshua-git
	LINUX	/vmlinuz-linux-aarch64-rockchip-bsp6.1-joshua-git
	INITRD	/initramfs-linux-aarch64-rockchip-bsp6.1-joshua-git-fallback.img
	FDT	/dtbs/linux-aarch64-rockchip-bsp6.1-joshua-git/rockchip/rk3588-orangepi-5-plus.dtb
	FDTOVERLAYS	/dtbs/linux-aarch64-rockchip-bsp6.1-joshua-git/rockchip/overlay/rk3588-pwm14-m2.dtbo
	APPEND	root=UUID=00e17a68-27a5-49e7-a3cd-23a0a6bd440d rw
```
### 2. Make an opi5p-pwm executable file
``# chmod +x opi5p-pwm``

and copy it to /usr/local/bin/
### 3. Create and launch a service
Copy the pwm-fan.service file to /usr/lib/systemd/system

And execute to run this service:

``# systemctl enable --now pwm-fan.service``

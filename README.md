Rockchip Walle SDK
======
It's an ubuntu base SDK, now it support RK3188 chip.

### Download source code
```
$ repo init -u https://github.com/rockchip-linux/rk3188-manifests
$ repo sync -j3
```

### Environment configuration
You need install some packages before building.  
Ubuntu 14.04:
```
$ sudo apt-get install git-core gnupg flex bison gperf build-essential \
				zip curl zlib1g-dev gcc-multilib g++-multilib libc6-dev-i386 \
				lib32ncurses5-dev x11proto-core-dev libx11-dev lib32z-dev ccache \
				libgl1-mesa-dev libxml2-utils xsltproc unzip qemu-user-static \
				qemu qemu-system
```

### BUild
* $ make all  
    use for first build
* $ make base  
    build kernel/demo/hardware
* $ make kernel  
    just build kernel
* $ make ubuntu-base  
    just build ubuntu-base image
* $ make lubuntu-core  
    just build lubuntu-core image

### Flash Image
```
$ sudo ./tools/DFU/linux/upgrade_tool ul output/image/RK3188Loader(L)_V2.19.bin
$ sudo ./tools/DFU/linux/upgrade_tool di -p output/image/parameter
$ sudo ./tools/DFU/linux/upgrade_tool di -k output/image/kernel.img
$ sudo ./tools/DFU/linux/upgrade_tool di -b output/image/boot.img
$ sudo ./tools/DFU/linux/upgrade_tool di -s output/image/lubuntu-core.img
$ sudo ./tools/DFU/linux/upgrade_tool rd
```
If you use eMMC storage, you need flash parameter.emmc:
```
$ sudo ./tools/DFU/linux/upgrade_tool di -p output/image/parameter.emmc
```

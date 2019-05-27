# VirtioFS QEMU for Proxmox

This repository contains the patches to enable virtiofs Qemu to work in Promox. These are the port of the patches that you find in the repo **pve-qemu** (see https://git.proxmox.com/?p=pve-qemu.git;a=summary). To know more about virtiofs Qemu, please visit https://virtio-fs.gitlab.io.

# How to Use these Patches

You need to follow the instructions in https://virtio-fs.gitlab.io/howto-qemu.html at section **Building QEMU**. Before to compile, you need to apply the patches by using **git am**. The configure should look like:

`../configure --prefix=$PWD --target-list=x86_64-softmmu --disable-xen --enable-gnutls \`

`--enable-linux-aio --enable-sdl --enable-rbd --enable-libiscsi \`

`--disable-smartcard --audio-drv-list="alsa" \`

`--enable-usb-redir --enable-glusterfs --enable-libusb --disable-gtk \`

`--enable-xfsctl --enable-numa --disable-strip --enable-jemalloc \`

`--disable-libnfs \`

`--disable-capstone \`

`--disable-guest-agent --disable-guest-agent-msi`

Note that the compilation may requiere the installation of additional dependencies. The resulting binary can be used in a Proxmox host by replacing the binary at **/usr/bin**. I think it may be another way to install it but I did not find it.

# Note

The patch **0003-PVE-Config-use-kvm-by-default.patch** should be removed. 

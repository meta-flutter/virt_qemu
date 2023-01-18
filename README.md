# Running GUI Linux in a virtual machine on a arm64 Mac

## Create runtime folder

    mkdir -p ~/VirtQemu

## Download artifacts and extract rootfs

    cd ~/VirtQemu
    curl -o Image https://download.automotivelinux.org/AGL/release/octopus/latest/qemuarm64/deploy/images/qemuarm64/Image
    curl -o agl-demo-platform-crosssdk-qemuarm64.ext4.xz https://download.automotivelinux.org/AGL/release/octopus/latest/qemuarm64/deploy/images/qemuarm64/agl-demo-platform-crosssdk-qemuarm64.ext4.xz
    unxz agl-demo-platform-crosssdk-qemuarm64.ext4.xz

## Create Disk Image

    dd if=/dev/zero of=Disk.img bs=1M count=7000
    hdiutil attach -nomount Disk.img

Use the name of the disk returned in following

    sudo dd if=agl-demo-platform-crosssdk-qemuarm64.ext4 of=/dev/<disk name> bs=1M
    hdiutil detach <disk name>

## Run image

    Execute VirtQemu

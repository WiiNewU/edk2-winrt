This is a UEFI Firmware that supports the Windows RT emulation. \
Sourced/Forked from: https://github.com/driver1998/edk2-winrt \
\
Reason for this fork is so that Windows RT 8.1 Boots at a higher 1360 x 768 rather then the default 800 x 600 that will look much better for viewing but still be small enough as a desktop window. \ 
I want to latter look at a custom UEFI Boot logo as well. \
It is used by this fork of qemu to boot Windows RT: https://github.com/AirDog46/qemu-winrt.git \
\
When booting qemu make sure in the boot comands to use "```-device VGA -device usb-kbd,id=kbd -device usb-tablet,id=mice```" for your vga output and flag "```-bios /path/to/QEMU_EFI_WinRT_768p.fd```" to have the right bios file to boot. \
\
Build:\
You will need Debian 11 and GCC 10.\
With Debian 11 setup (and its apt mirror pointing to https://archive.debian.org/debian) Get these packages with this command: "```sudo apt-get install uuid-dev python gcc-10-arm-linux-gnueabihf bison flex libgmp3-dev libmpc-dev libmpfr-dev texinfo gdc gcc build-essential cmake ninja-build autoconf automake git iasl```" \
You might have to update Debian first but due to age of Debian 11 you might have to do a un-secure update by: "```sudo apt -o Acquire::Check-Valid-Until=false update```" . \
\
\
Run these in order upon rebuild: 
```
git clone https://github.com/WiiNewU/edk2-winrt --recursive 
cd edk2-winrt 
make -C BaseTools 
source edksetup.sh 
export GCC49_ARM_PREFIX=arm-linux-gnueabihf- 
build -a ARM -t GCC49 -b RELEASE -p ArmVirtPkg/ArmVirtQemuWinRt.dsc
```
\
If successful output UEFI Floppy file should be at: ```edk2-winrt/Build/ArmVirtQemuWinRt-ARM/RELEASE_GCC49/FV/QEMU_EFI.fd``` \
If Build failes delete the ```edk2-winrt\Build``` directory to start over. 


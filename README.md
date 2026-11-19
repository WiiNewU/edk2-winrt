This is a UEFI Firmware that supports the Windows RT emulation.\
Sourced/Forked from: https://github.com/driver1998/edk2-winrt\
Reason for this fork is so that Windows RT 8.1 Boots at a higher 1360 x 600 rather then the default 800 x 600 that will look much better for viewing but still be small enough as a desktop window.\
\
Build:\
You will need Debian 11 and GCC 10.\
With Debian 11 setup (and its apt mirror pointing to https;//archive.debian.org/debian) Get these packages with this command: "#sudo apt-get install uuid-dev python gcc-10-arm-linux-gnueabihf"\
Run these in order upon rebuild:\
#git clone https://github.com/WiiNewU/edk2-winrt\
#cd edk2-winrt\
#make -C BaseTools\
#source edksetup.sh\
#export GCC49_ARM_PREFIX=arm-linux-gnueabihf-\
#build -a ARM -t GCC49 -b RELEASE -p ArmVirtPkg/ArmVirtQemuWinRt.dsc\
\
If successful output UEFI Floppy file should be at: edk2-winrt/Build/ArmVirtQemuWinRt-ARM/RELEASE_GCC49/FV/QEMU_EFI.fd\


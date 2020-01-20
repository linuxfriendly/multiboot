# multiboot

This project is about creating a multi-boot EFI usb stick.

Please note : It only works with EFI-enabled hardware and/or EFI-enabled virtual machines.

Setting up a KVM EFI virtual machine is easy, instructions on that will be added later.

# Usage instructions

## The USB Stick

The USB stick will have to be 16GB in size (minimum) with preferribly an USB3 chipset for performance reasons.

First create a partition table on the USB stick with parted

create a GPT partition table with 2 partitions:

- /EFI (FAT32, flags bios_boot set) 512MB space (exfat is not supported)
- / The rest of the Stick.

Please note that the filesystem used for / , has to be supported by Grub2.

My own stick uses xfs for / , so the grub files in /EFI contain the grub_xfs module which is inserted in the bootloader.

## Contents

/EFI contains just grub.efi which loads grub , 
     grub creates the files in this directory when mounted properly before running grub-mkconfig from a fedora workstation.

/boot -> The setup structure
/boot/grub2 -> Grub's configuration
/boot/iso -> The actual iso's


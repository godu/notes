---
date: 2021-05-22T14:42
tags:
  - linux
  - windows
---

# Grub2 menuentry for Windows 10 UEFI

- Install `os-prober`
- Mount your windows partitions
- Run `grub2-mkconfig -o /boot/grub2/grub.cfg`

- Put this in your `/etc/grub.d/40_custom` file

```
menuentry 'Windows 10' {
    search --fs-uuid --no-floppy --set=root 23C5-F86E
    chainloader (${root})/EFI/Microsoft/Boot/bootmgfw.efi
}
```

Where `23C5-F86E` is the UUID of your windows UEFI partition.

## How to get UUID

```
$ os-prober
/dev/sdb1@/EFI/Microsoft/Boot/bootmgfw.efi:Windows Boot Manager:Windows:efi
$ blkid /dev/sdb1
/dev/sdb1: UUID="23C5-F86E" BLOCK_SIZE="512" TYPE="vfat" PARTLABEL="EFI System Partition" PARTUUID="2d530bb2-55db-4e8a-9b94-afdf08afe071"
```

## References

- [Grub2 menuentry for Windows 10 UEFI](https://ihaveabackup.net/2016/12/18/grub2-entry-for-windows-10-uefi/)

# linux-bootloader

This is a minimal bootloader for vorteil.io.

It's a slightly modified version of an existing bootloader which can be found here:

http://sebastian-plotz.blogspot.com/

The important change is setting _current_lba_ to LBA 67 where the Linux kernel is stored on disk.

```asm
mov eax, 67
mov [current_lba], eax
```

The offset of 67 is based on:

- 33 LBAs for GUID partition table
- 32 LBAs for 16384 bytes of vorteil.io configuration space
- 1 LBA for the tar header of the bundle

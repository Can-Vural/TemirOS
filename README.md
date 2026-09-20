### Note : 
This project is currently in `active development`. At this stage, it is a 16-bit real mode bootloader capable of booting on a real physical machine.

---

- Install Dependencies:
```Bash
sudo pacman -S nasm qemu-ui-gtk
```

- Assemble the Boot Sector:
```Bash
nasm -f bin ./boot.asm -o ./boot.bin
```

- Emulate via QEMU:
```Bash
qemu-system-x86_64 -hda ./boot.bin
```

- Flash to Bare-Metal USB:
  Ensure /dev/sdX matches your intended drive
  
```Bash
sudo dd if=./boot.bin of=/dev/sdX bs=512 count=1 conv=notrunc status=progress && sync
```


To boot on a physical machine, Secure Boot must be **disabled** in the BIOS, and Compatibility Support Module **(Legacy Mode) must be enabled**.

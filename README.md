# Custom Operating System Kernel

this repository cotains the source code for a basic custom operating system kernel.
This version of the kernel is desined to handle basic keyboard input and output to the screen, utilizing both C and assembly code.

#Features
- Basic keyboard input handling
- Screen output to the console
- Interrupt Descriptor Table (IDT) setup
- Programmable Interrupt Controllers (PIC) initialisation

## Prerequesities
Before you start, make sure you have the following tools installed:
- **Assembler**: nasm (Netwide assembler)
- **C compielr**: GCC (GNU Compiler Collection)
- **Linker**: LD (GNU Linker)
- **Bootloader**: GRUB (Grand Unified Bootloader)

## Building the Kernel

To compile and buid the kernel, follow these steps:
  
 1. **Assemeble the Assembly code**
     Assemble the `kernel.asm` file using NASM:
     ```sh
     nasm -f elf32 kernel.asm -o kernel.o
     ```
 2. **Compile the C Code**
    Compile the kernel.c file using GCC:
    ```sh
    gcc -m32 -c kernel.c -o kc.o
     ```
 3. **Link the Object Files**
    Link the object files to create a kernel binary:
    ```sh
    ld -m elf_i386 -T link.ld -o kernel kasm.o kc.o
    ```
 4. **Test the kernel**
   Test your kernel using an emulator like QEMU:
   ```sh
   qemu-system-i386 -kernel kernel
   ```
## How It works
- **Assembly Code** (`Kernel.asm`): this file contains the low level kernel entry point, stack setup, and keyboard interrupt handling. It also includes the Multiboot header required by GRUB to load the kernel.managing screen output, and basic kernel operations.

- **C Codde**(`Lernel.asm`): Implements the Kernel's main functionality, including IDT and PIC initialization, handling keyboard input, managing screen output, and basic kernel operations.

- **Keyboard Handlig**: The kenel processes Keyboard interupts, updates the screen based on user input , and handles special keys like Enter. the other special keys will be added in the upcoming commits.

- **Screen output**: Uses direct video memory access to display text on the screen.
  
##Contributing

Contributions are welcome if you have suggestions, issues, or would like to contribute code, please submit issues or pull requests.







      

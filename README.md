# Embedded Linux Demo  
## Overview  
This project demonstrates building a minimal embedded Linux system on an STM32MP1 or Raspberry Pi platform. It covers building a root filesystem using Yocto or Buildroot, customizing the device tree, cross-compiling applications, and booting the target. This showcases your ability to bring up embedded Linux, configure peripherals, and run user-space applications.  
## Hardware Requirements  
- STM32MP1 development board (e.g., NUCLEO ‑STM32MP157C) or Raspberry Pi 3/4.  
- SD card for booting the Linux image.  
- USB ‑to ‑UART cable for serial console access.  
- Optional: external LEDs or sensors for demo applications.  
## Software Requirements  
- Yocto Project (Poky) or Buildroot.  
- ARM cross-compilation toolchain (e.g., `arm-none-linux-gnueabihf`).  
- U ‑Boot and Linux kernel sources.  
- Linux host PC with required packages (`git`, `gcc`, `repo`, etc.).  
## Build & Setup Instructions  
1. Install build prerequisites on your host machine.  
2. Clone this repository and initialize the build environment.  
3. Choose Yocto or Buildroot:  
   - **Yocto:** Initialize a `repo` manifest for your board, adjust `local.conf` and `bblayers.conf`, then run `bitbake core-image-minimal`.  
   - **Buildroot:** Run `make stm32mp1_defconfig` (or the appropriate board defconfig) and `make` to build the root filesystem and kernel.  
4. Write the generated SD card image to your SD card.  
5. Insert the SD card into the board and connect the serial console.  
6. Boot the board and log in via the console.  
7. Modify the device tree to enable custom peripherals; rebuild the image if necessary.  
8. Cross-compile a simple GPIO application using the provided Makefile and run it on the target.  
## Features  
- Minimal embedded Linux distribution for STM32MP1/Raspberry Pi.  
- Custom device tree enabling GPIO, UART, and I²C peripherals.  
- Example user-space application toggling an LED via sysfs or `libgpiod`.  
- Documentation on cross-compiling, SD card preparation, and bootloader configuration.  
## Demo  
After building and booting the image, run the provided LED ‑toggle application and observe the LED blinking on your board. Use `dmesg` to verify device ‑tree changes and peripheral initialisation.  
## Future Work  
- Integrate an initramfs and BusyBox for smaller footprints.  
- Add package management (e.g., `opkg`).  
- Enable networking and remote update capabilities. 

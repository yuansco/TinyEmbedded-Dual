
# TinyEmbedded-Dual
Low-cost Embedded Linux development board compatible with RISC-V D1s/F133 and ARM Cortex-A7 T113-S3 SoC.

<img src="https://github.com/yuansco/TinyEmbedded-Dual/blob/main/Demo/pcb_top_view.PNG" style="width:450px;"/>

## About the SoC
D1s/F133: Single-Core RISC-V 64 @ 1.0G with in package 64MB DDR2\
T113-S3: Dual-Core ARM Cortex-A7 @ 1.2 GHz with in package 128MB DDR3

## Feature
TinyEmbedded-Dual is a low-cost embedded Linux development board compatible with ARM Cortex-A7 T113-S3 and RISC-V D1s/F133 SoC. Here are some highlights of this board:

 * On-board USB-to-UART serial debug console.

 * On-board LIS3DH acceleration sensor.

 * On-board Realtek RTL8188FTV Wi-Fi Module.

 * One USB Type-C port support USB2.0.

 * Three indicator LEDs for power status, UART data transmission, and user-defined purposes.

 * Two buttons for reset and user-defined purposes.

 * One MicroSD slot for storing the boot image.

 * One Serial NOR Flash connected to SPI0.

 * One 3.5mm headphone jack for audio output.

## Hardware Design

#### Block Diagram

<img src="https://github.com/yuansco/TinyEmbedded-Dual/blob/main/Document/block_diagram.PNG" style="width:450px;"/>

#### Power Tree

<img src="https://github.com/yuansco/TinyEmbedded-Dual/blob/main/Document/power_tree.PNG" style="width:450px;"/>

#### 3D Simulation

<img src="https://github.com/yuansco/TinyEmbedded-Dual/blob/main/Demo/3d_top_view.PNG" style="width:450px;"/>
<img src="https://github.com/yuansco/TinyEmbedded-Dual/blob/main/Demo/3d_bottom_view.PNG" style="width:450px;"/>

#### Top View

<img src="https://github.com/yuansco/TinyEmbedded-Dual/blob/main/Document/top_view.PNG" style="width:450px;"/>

#### Download

Schematic: [PDF](https://github.com/yuansco/TinyEmbedded-Dual/blob/main/Document/TinyEmbedded_Dual_A.pdf)

BOM: [CSV](https://github.com/yuansco/TinyEmbedded-Dual/blob/main/Document/BOM.csv)

Image: [IMG](https://github.com/yuansco/TinyEmbedded-Dual/blob/main/Images/sdcard.img)

## Build an SD card image for booting TinyEmbedded-Dual

BSP is placed at [Buildroot-TinyEmbedded-Dual](https://github.com/yuansco/Buildroot-TinyEmbedded-Dual)

``` shell
# Install development tools
sudo apt install -y libssl-dev swig ncurses-dev flex bison

# Download TinyEmbedded-Dual BSP from Buildroot-TinyEmbedded-Dual
git clone https://github.com/yuansco/Buildroot-TinyEmbedded-Dual.git

# Apply defconfig
cd Buildroot-TinyEmbedded-Dual/buildroot
make tinyembedded_dual_t113_defconfig

# Build image
make 

# Flash image into your SD card. You need to replace /dev/sdx with the actual drive letter.
sudo dd if=./output/image/sdcard.img of=/dev/sdx bs=512 status=progress && sync
```

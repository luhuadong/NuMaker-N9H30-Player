# NuMaker-N9H30-Player

## 软件包

| 软件包 | 版本 | 功能 |
| :--   | :-- | :--  |
| LVGL  | 8.2.0 | GUI 图形库 |
| helix | 1.0.0 | MP3 Decoder |
| webclient | 2.2.0 | HTTP 客户端 |
| mbedtls | 2.7.10.1 | TLS 加密库 |
| ezXML | 0.8.6.1 | XML 解释器 |
| fastlz | 1.0.1 | 解压缩 |
| EasyFlash | 4.1.0 |  |
| littlefs  | 2.0.5 |  |
| ft6236 | 1.0.0 |  |


## 1. Introduction
Nuvoton offers HMI platforms which are embedded with Nuvoton N9H MPU.  The N9H series with ARM926EJ-S core can operate at up to 300 MHz and can drive up to 1024x768 pixels in parallel port. It integrated TFT LCD controller and 2D graphics accelerator, up to 16 million colors (24-bit) LCD screen output, and provides high resolution and high chroma to deliver gorgeous display effects. It embedded up to 64 MB DDR memory, along with ample hardware storage and computing space for excellent design flexibility.


### 1.1 MPU specification
|  | Features |
| -- | -- |
| Part NO. | N9H30F61IEC(or N9H30F63IEC) (LQFP216 pin MCP package with DDR (64 MB) |
| CPU ARCH. | 32-bit ARM926EJ-S |
| Operation frequency | 300 MHz |
| Embedded SDRAM size | Built-in 64MB |
| Crypto engine |  AES, DES,HMAC and SHA crypto accelerator |
| RMII interface |  10/100 Mbps x2 |
| USB 2.0 |  High Speed Host/Device x1 |
| Audio |  Mono microphone / Stereo headphone |
| Extern storage |  32MB SPI-NOR Flash |
| SD card slot |  SD |

**Notice: Please remember to select corresponding Part NO in NuWriter.**

### 1.2 Interface
| Interface |
| -- |
| Two RJ45 Ethernet |
| An USB 2.0 HS Dual role(Host/Device) port |
| A microSD slot |
| A 3.5mm Audio connector |
| An ICE connector |

### 1.3 On-board devices
| Device | Description | Driver supporting status |
| -- | -- | -- |
|Ethernet PHY | IP101GR | Supported |
|Keypad | K[1, 6] | Supported |
|LEDs |  | Supported |
|TFT-LCD panel | 7" inch 24b RGB  | Supported |
|Touch panel | 7" inch resistive | Supported |
|Audio Codec | NAU8822, Supports MIC and earphone | Supported |
|USB Device | VCOM + MStorage | Supported |
|USB Host | MStorage | Supported |
|SPI NOR flash | W25Q256JVEQ (32 MB) | Supported |

## 2. Supported compiler
Support GCC and MDK IDE/compilers. More information of these compiler version as following:
| IDE/Compiler  | Tested version            |
| ---------- | ---------------------------- |
| MDK        | uVision 5.25.2               |
| GCC        | 6-2017-q1-update             |

Notice: Please install ICE driver for development and [NuMicro_ARM9_Device_Database_Keil](https://www.nuvoton.com/resource-download.jsp?tp_GUID=SW1820201207155701).

## 3. Program firmware
### 3.1 SDRAM Downloading using NuWriter
You can use NuWriter to download rtthread.bin into SDRAM, then run it.

```bash
$ ./install/bin/nuwriter -m sdram -d N9H30F61IEC.ini -a 0x0 -w ../../firmwares/Studio/rtthread.bin -n
```

<br>
Choose type: DDR/SRAM<br>
<< Press Re-Connect >><br>
Choose file: Specify your rtthread.bin file.<br>
Execute Address: 0x0<br>
Option: Download and run<br>
<< Press Download >><br>
Enjoy!! <br>
<br>

### 3.2 SPI NOR flash using NuWriter
You can use NuWriter to program rtthread.bin into SPI NOR flash.

```bash
$ ./install/bin/nuwriter -m spi -d N9H30F61IEC.ini -t uboot -a 0x0 -w ../../firmwares/Studio/rtthread.bin -v
```

<br>
Choose type: SPI<br>
<< Press Re-Connect >><br>
Choose file: Specify your rtthread.bin file.<br>
Image Type: Loader<br>
Execute Address: 0x0<br>
<< Press Program >><br>
<< Press OK & Wait it down >><br>
<< Set Power-on setting to SPI NOR booting >><br>
<< Press Reset button on board >><br>
Enjoy!! <br>
<br>

## 4. Test
You can use Tera Term terminate emulator (or other software) to type commands of RTT. All parameters of serial communication are shown in below image. Here, you can find out the corresponding port number of Nuvoton Virtual Com Port in window device manager.

```bash
$ sudo minicom -D /dev/ttyUSB0
```

## 5. Resources
* [Board Schematic](https://www.nuvoton.com/resource-download.jsp?tp_GUID=HL1020201117191514)
* [Download NK-N9H30 Quick Start Guide](https://www.nuvoton.com/resource-download.jsp?tp_GUID=UG1320210329155300)
* [Download NuWriter](https://github.com/OpenNuvoton/NUC970_NuWriter)
* [Download Windows 32-bit 6-2017-q1-update ARM GCC](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads/6-2017-q1-update)


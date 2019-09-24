# stm32f1-template-project

stm32f1-template-project is a Makefile based template for bare metal
stm32f1 projects.

Currently it's configured to support stm32f103c8t6 MCU found on
the "Blue Pill" boards. Switching to another MCU requires to change
the linker script and possibly startup code.

## Prerequisites

Install the following software:

- [arm-none-eabi toolchain](
    https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads)
- [open source stlink](<https://github.com/texane/stlink>)
- [STM32CubeF1](
    <https://www.st.com/en/embedded-software/stm32cubef1.html>)

ARM toolchain, stlink, and must be added to PATH (use ~/.bash_profile).
Assuming everything is installed in ~/stm32/:

```bash
# add ARM toolchain path
export PATH=~/stm32/gcc-arm-none-eabi/bin:$PATH
# add stlink path
export PATH=~/stm32/stlink-install/bin:$PATH
```

Path to STM32CubeF1 should be also exported (use ~/.bash_profile):

```bash
# export STM32Cube
export STM32CUBE_PATH=~/stm32/stm32cube
```

## Building Project

Run

```bash
make
```

to build the project and create the firmware hex file.

Run

```bash
make flash
```

to flash MCU using st-link.

Run

```bash
make clean
```

To remove object and dependency files.

Run

```bash
make distclean
```

to remove object, dependency, and firmware files.

## Note on Linker Script

Currently the Makefile uses STM32F103XB_FLASH.ld, which defines 128K flash size.
However, stm32f103c8t6 has 64K flash. Make sure firmware fits MCU memory.

## Documentation

- [STM32F103C8T6 Datasheet](
    https://www.st.com/resource/en/datasheet/stm32f103c8.pdf)
- [STM32F103C8T6 Reference Manual](
    https://www.st.com/content/ccc/resource/technical/document/reference_manual/59/b9/ba/7f/11/af/43/d5/CD00171190.pdf/files/CD00171190.pdf/jcr:content/translations/en.CD00171190.pdf)
- [Nokia 5110 Display Controller Datasheet](
    https://www.sparkfun.com/datasheets/LCD/Monochrome/Nokia5110.pdf)
- [Cortex-M3 Devices Generic User Guide](
    http://infocenter.arm.com/help/topic/com.arm.doc.dui0552a/DUI0552A_cortex_m3_dgug.pdf)
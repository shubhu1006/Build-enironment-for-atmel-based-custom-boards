# Windows-build-flash-enironment-for-atmel-based-custom-boards
Windows Build environment for atmel based custom boards having on board programmer.

## Insall necessay softwares
User needs to install WinAVR (https://sourceforge.net/projects/winavr/files/) and add paths in environment variable:
- \WinAVR-<*version*>\bin
- \WinAVR-<*version*>\utils\bin

> replace **version** with installed version
## Build applicaion code:
To build user application made the following changes in the Makefile:
- Set **MCU**, user has to give name of the atmel controller. For example: **MCU=atmega8**
- Set **F_CPU** user has to set controller frequency. For example: **F_CPU = 12000000**
- Set **TARGET**, target file name without extension, For example: **TARGET = main**
- Set (optional) **SRC**, mention name of the source files with their respective folder path.
- Set (optional) **EXTRAINCDIRS**, user can mention paths to the other include files if any.
- Set (optional) **EXTRALIBDIRS**, user can mention other libraries with their respective path.

## Flash application code:

## References

## Contact
shubham.mittal.k@gmail.com


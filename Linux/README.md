# Linux-build-enironment-for-atmel-based-custom-boards
Build and flash environment for atmel based custom boards having on board programmer.

There are many custom boards using atmel series controllers having on board programmer, flashing the code from linux environment is bit tricky. So this will help you in flashing atmel controllers on linux development environment.
For linux, we are using BootloadHID utility, which needs to be build and using that atmel controllers can be flash.

## Insall necessay softwares
- sudo apt-get install gcc-avr avr-libc avrdude binutils 
- sudo apt-get install libusb-1.0-0-dev libusb-dev

## Build bootloadHID utility:
- Get the bootloadHID source from the following repo: https://github.com/robertgzr/bootloadHID
- Extract and cd bootloadHID/
- cd commandline/
- make VENDORID=0x16c0 PRODUCTID=0x05DF

> make requires VENDORID and PRODUCTID to identify the device. This information can be extract from the datasheet of the chip. Without this parameter, the compiler will produce wrong code that most likely not work on the chip. 
> In the above make command for our project got these values from somewhere (from a guy) not from the datasheet.

The make command will create the 'bootloadHID' app. This will be later used to flash.

## Build applicaion code:
- User can build app either using following commands or use Makefile provided with this project
	- avr-gcc -g -Os -DF_CPU=12000000 -mmcu=atmega8 -c demo.c
	- avr-gcc -g -mmcu=atmega8 -o demo.elf demo.o
	- avr-objcopy -j .text -j .data -O ihex demo.elf demo.hex

> Here, it is tested on atmel atmega8 mcu with frequency = 12Mhz. You can test it for other mcu's too.

## Flash application code:
Copy the bootloadHID bin created and paste it into your project folder.
	
If applicaion is build using above commands then use command:
- sudo ./bootloadHID <application_hex >demo.hex
> example: sudo ./bootloadHID demo.hex 

If application is build using Makefile provided with this project then use command:
- make program

## References
https://blog.akendo.eu/post/how_to_flash_an_atmega8

https://github.com/robertgzr/bootloadHID

## Contact
shubham.mittal.k@gmail.com


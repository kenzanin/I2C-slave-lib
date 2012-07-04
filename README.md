# I2C Slave library

## Table of contents

1. What is this library?
2. Contents of this library
3. Supported devices
4. Functions in this library

------------------------------------------------------------------------------------

### 1. What is this library? 
This library is an I2C slave library which uses the TWI peripheral inside the
AVR microcontroller to establish connections using the I2C protocol

------------------------------------------------------------------------------------

### 2. Contents of this library
	
The library contains the following files:

* main.c
* I2C_slave.c
* I2C_slave.h

##### main.c
This is a piece of example code which prints out the first index of the 
buffer to show that the slave device acts as an EEPROM.
		
##### I2C_slave.c
This file contains all the function declarations to setup and work with the
TWI hardware peripheral inside the AVR.
It takes care of the interrupt handling and receiving the bytes.

*Make sure you add this source file to your Makefile!*
		
##### I2C_slave.h 
This file contains the function prototypes
		
*This file has to be included in your source file*

------------------------------------------------------------------------------------
	
### 3. Supported devices
Though I have only tested this library on an ATmega328P it should be running
on all major ATmega AVRs like:
		
* ATmega644
* ATmega32
* ATmega16
* ATmega328/P
* ATmega168/P
* ATmega88/P
* ATmega44/P
* ATmega8
	
If your device is not supported you can probably adapt this library easily to your
needs by having a look at the your device's datasheet and changing the register names
appropriately

The ATtiny range of microcontrolles is not supported as they only provide a USI 
peripheral which is completely different from the TWI peripheral used on the
other controllers

------------------------------------------------------------------------------------

### 4. Functions in this library

* void I2C_init(uint8_t address)
* void I2C_stop(void)
	
##### void I2C_init(uint8_t address)
This function needs to be called only once to set up the TWI to respond to 
the address passed into the function

**Note that you have to include the avr/interrupt.h and you have to globally enable interrupts with sei() for this library to work**
		
##### void I2C_stop(void)
This function disables the TWI peripheral completely and therefore isolates the
device from the bus
		

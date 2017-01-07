# Bluetooth Dials

<IMG alt=overall src="pics/overall.png"><BR>

"Bluetooth Dials" is a wireless input device for manipulating multiple parameters, such as viewing directions, positions, image contrast, proceeding/reversing movie frames, zooming in/out, and so on. It has dials and buttons and sends your manipulation through its Bluetooth interface to the host PC or WS. In 1990's, dial/button boxes were commercially available from graphics WS manufacturers, but today we couldn't find such devices. The most similar one is Microsoft Surface Dial, but it has only one dial and does not meet our purpose. Bluetooth Dials is a wireless version of the historic dial/button box. It's compatible with our <a href="https://github.com/mizutanilab/RecView">RecView</a> and <a href="https://github.com/mizutanilab/MCTrace">MCTrace</a> softwares.<br>

Six knobs are used for manipulating parameters. Two buttons are used for toggling some functions. The upper black button is also used for turning on and off the device. The green LED is turned on when connected, and blinks when standby.  

The Bluetooth interface of this device is Microchip (Roving Networks) RN42. As the host-side Bluetooth interface, we use Bluetooth dongles MM-BTUD43 (Sanwa Supply) with Windows Vista, 7, and 10 PCs. This dongle seems to use CSR chips. Built-in Bluetooth interfaces of our laptop PCs also work well with the device. We have no information about what kind of chips are implemented in our laptops.   

# Firmware
The device firmware runs in two modes: serial mode and keyboard mode. The serial mode is the default boot. In this mode, dial/button manipulations are sent to a virtual COM port associated with the Bluetooth interface of this device. The keyboard mode can be selected by pressing the black button while setting batteries or connecting the power cable. In the keyboard mode, this device is recognized as a Bluetooth keyboard. Dial/button manipulations are treated as if they are keyboard inputs.  
In the serial mode, Bluetooth sniffing with a 500 ms interval is enabled (RN42 command: SW,0320) to reduce the battery consumption, but a certain laptop interface seems not compatible with this sniffing. In the keyboard mode, sniffing is disabled because it's frustrating.  

# Schematic
<IMG alt=schematic src="pics/schematic170107.png"><BR>
There's nothing special. The MCU (PIC16F1828) receives signals from rotary encoders (PEC11R, Bourns) and push buttons, and sends the information through the UART TX line to the Bluetooth module (RN42XV). The device operates with four AA batteries, or with an external DC supply (4 - 16 V, 50 mA). If you prefer wired connection to your PC, the UART output can be directly sent to a serial (RS232C) port. Or you can choose a MCU with a USB interface or use an external UART-USB interface chip, such as FT232 or CP210x, to connect the device to the USB port. <BR>

# Host side coding
The device decodes your dial/button manipulations into ASCII characters Z/X (CCW/CW of the lower left dial), A/S (middle left), Q/W (upper left), C/V (lower right), D/F (middle right), E/R (upper right), G (lower button), and T (upper button) and sends them through the Bluetooth interface. In the keyboard mode, these characters come through as keyboard inputs, so they can be used as accelerator keys. By associating target routines with these characters, those routines are invoked by the dial/button manipulations. <BR>
If you use this device in the serial mode, dedicated host side coding is necessary, but its response is faster, while the current consumption is rather low thanks to the Bluetooth sniffing. You can find a serial-mode example in the source code of <a href="https://github.com/mizutanilab/RecView">RecView</a>.

# Tips
Rubber bumpons on the device back are essential.
<IMG alt=overall src="pics/rubberBumpons.png"><BR>
Without these bumpons, the device itself rotates when you rotate knobs.

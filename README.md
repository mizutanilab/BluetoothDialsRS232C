# Bluetooth Dials

<IMG alt=overall src="pics/overall.png"><BR>

"Bluetooth Dials" is a wireless input device for manipulating multiple parameters, such as viewing directions, positions, image contrast, proceeding/reversing movie frames, zooming in/out, and so on. It has dials and buttons and sends your manipulation through a Bluetooth interface to the host PC or WS. In 1990's, dial/button boxes were commercially available from graphics WS manufacturers, but today we couldn't find such devices. This device is compatible with RecView and MCTrace softwares. It's very useful.<br>

Six knobs are used for manipulating parameters. Two buttons are used for toggling some functions. The green LED is turned on when connected, or blinks when standby.  

The device firmware runs in two modes: serial mode and keyboard mode. The serial mode is the default boot. In this mode, dial/button actions are sent to a virtual COM port associated with the Bluetooth interface of this device. The keyboard mode can be selected by pressing a button while setting batteries or connecting the power supply if no batteries. In the keyboard mode, this device is recognized as a Bluetooth keyboard. Dial/button actions are treated as if they are inputs from keyboard.  

The Bluetooth interface of this device is Microchip (Roving Networks) RN42. We use Bluetooth dongles MM-BTUD43 (Sanwa Supply) with workstations running Windows Vista, 7, and 10. This dongle seems to use CSR chips. Built-in Bluetooth interfaces of our laptop PCs also work well with the device. We have no information about what kind of chips are implemented in our laptops.  

# Schematic
<IMG alt=schematic src="pics/schematic170107.png"><BR>
There's nothing special. The MCU (PIC16F1828) receives signals from rotary encoders (PEC11R, Bourns) and push switches, and sends them through the UART TX line to the Bluetooth module (RN42XV). The device operates with four AA batteries, or with an external DC supply (4 = 16 V, 50 mA). If you prefer wired connection, the UART output can be directly sent to a serial (RS232C) port if your PC has it. Or you can use a UART-USB interface chip, such as FT232, to connect the device to the USB port. <BR>

# Host side coding
In the keyboard mode, character inputs caused by dial/button actions can be used as accelerator keys to manipulate the software. The device sends characters Z/X (CCW/CW of the left lower dial), A/S (left middle), Q/W (left upper), C/V (right lower), D/F (right middle), E/R (right upper), G (lower button), and T (upper button). You can associate these keys with your routines only by assigning these characters as accelerator keys. If you use this device in the serial mode, dedicated host side coding is necessary, but its response is rather fast. You can find an example in <a href="https://github.com/mizutanilab/RecView">RecView</a>.

# Tips
Rubber bumpons on the backside are essential.
<IMG alt=overall src="pics/rubberBumpons.png"><BR>
Without these bumpons, the device itself rotates when you rotate knobs.

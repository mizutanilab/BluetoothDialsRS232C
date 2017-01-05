# Bluetooth Dials
Dial input device with Bluetooth interface

[We took device picutures. It will be posted here soon]<br>

This is a wireless input device for manipulating multiple parameters, such as viewing directions, positions, contrast, frames, magnification, and so on. It has dials and buttons and communicate through a Bluetooth interface with the host PC or WS. In 1990's, dial/button boxes were commercially available from graphics WS manufacturers, but today we can't find such devices. So we made it by ourselves. This device is compatible with RecView and MCTrace softwares. It's very useful.<br>

The device firmware runs in two modes: serial mode and keyboard mode. The serial mode is the default boot. In this mode, dial/button actions are sent to a virtual COM port associated with the Bluetooth interface of this device. The keyboard mode can also be selected by pressing a button while setting batteries or connecting the power supply if no batteries. In the keyboard mode, this device is recognized as a Bluetooth keyboard. Dial/button actions are treated as if they are inputs from keyboard. 

The Bluetooth interafce of this device is Microchip (Roving Networks) RN42. We use Bluetooth dongles MM-BTUD43 (Sanwa Supply) with Windows Vista, 7, and 10 PCs. The Sanwa Supply site says they use CSR chips. Built-in Bluetooth interfaces of our laptop PCs also work well with the device. We have no information what kind of chips are implemented in our laptops. 

# Schematic
[in preparation]

# Host side coding
In the keyboard mode, character inputs caused by dial/button actions can be used as accelerator keys to manipulate the software. The device sends characeters Z/X (left lower dial CCW/CW), A/S (left middle), Q/W (left upper), and so on. You can associate these keys with your routines only by assigning these characters as accerelator keys. If you use this device in the serial mode, dedicated host side coding is necessary, but its response is rather fast. 
[coding will be posted soon.]

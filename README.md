# Bluetooth-dials
Dial input device with Bluetooth interface

[We took device picutures. It will be posted here soon]<br>

This is a wireless input device for manipulating multiple parameters, such as viewing directions, positions, contrast, frames, magnification, and so on. It has dials and buttons and communicate through a Bluetooth interface with the host PC or WS. Dial/button boxes were commercially available from graphics WS manufacturers in 1990's, but we couldn't find similar ones today. So we made it by ourselves. This device is compatible with RecView and MCTrace softwares. It's very useful.<br>

The device firmware runs in two modes: serial mode and keyboard mode. The serial mode is the default boot. In this mode, dial/button actions are sent to a virtual COM port associated with the Bluetooth interface of this device. The keyboard mode can also be selected by pressing a button while setting batteries or connecting the power supply if no batteries. In the keyboard mode, this device recognized as a Bluetooth keyboard and dial/button actions are treated as if they are inputs from keyboard. 

The Bluetooth interafce of this device is Microchip (Roving Networks) RN42. We use Sanwa Supply dongles MM-BTUD43 on Windows Vista, 7, and 10 PCs to communicate with this device. The Sanwa Supply site says they use CSR chips. Built-in Bluetooth interaces of our laptop PCs can also communiate. We have no information what kind of chips are implemented in our laptops. 

# Schematic
[in preparation]

# Host side coding
In the keyboard mode, dial/button actions can be processed as accelerator keys to manipulate the software. The device sends characeters Z/X (left lower dial CCW/CW), A/S (left moddle), Q/W (left upper), and so on. Software-side actions are invoked by accelerator keys, so you can associate your function by assigning these accelerator keys. If you use this device in the serial mode, the host side coding is complicated, but it's rather faster than keyboard mode. 
[coding will be posted soon.]

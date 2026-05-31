---
layout: default
---
## Transmission To/From Modules

### Hardware
Transmission between the main raspberry pi controller and each of the connected modules begins and ends with the SPI harness board. 

This board uses a 74HC595 shift register to handle the six CS lines currently used in the KICK Robot system. The lines are numbered 0-5 and are mapped to shift register output stage states as follows, with the bang (!) symbol indicating a bitwise logical not due to CS being active low:

| Line ID | Output |
|------|--------|
| 0 | !(0x80) |
| 1| !(0x40) |
| 2 | !(0x20) |
| 3 | !(0x10) |
| 4 | !(0x08) |
| 5 | !(0x04) |

Additionally, within the hardware_interfaces.py file that defines how the shift register toggles the CS lines, there is one additional case where all lines are pulled high. This is because the way SPI is configured in the code on both sides, the CS line needs to pulse high after each byte. This is toggled with the Line ID of 8, leaving line IDs 6 and 7 available for future use if a board were developed that used all 8 output stages of the shift register. 

### Protocol
Messages sent to and from the attached modules need to have integrity, and actions need to be coordinated between modules. For these reasons, the KICK Robot system uses an 8-byte message frame for communications and has a SYNC line available to pulse low once all lines have been polled. 

Since the way SPI works means that the module will always be one byte behind the controller, it is set up with some asymmetry. 

Pi Side Example (Discovery):

| Alignment | Header | Module ID | Data (4 bytes) | Checksum |
|-----------|--------|-----------|----------------|----------|
| 0xBF | 0xF0 \| (0x7 & path) | 0x00 | 0 | Header Value |

Module Side Example (EchoDevice Discovery):

| Header | Module ID | Data (4 bytes) | Checksum | Alignment |
|--------|-----------|----------------|----------|-----------|
| 0xF0 \| (0x7 & 0x00) | 0x01 | 0 | Header + ID | 0xBF |

Note that the Checksum in these examples do not always equal these values, it is simply the 8-bit sum over the header, module ID, and all 4 of the data bytes. These just represent the discovery case where zeros are being sent in the data stream. 

In the case of an internal error, the module side is actually intended to send a 0xFF Checksum as an indicator of internal fault. In practice, the pi also detects this when the module is disconnected. 

<br>
[Back to Overview]({% link pages/kick-robot/overview.md %}) <br>
[Back to Architecture]({% link pages/kick-robot/architecture.md %})

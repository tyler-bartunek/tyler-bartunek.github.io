---
layout: default
---
## Transmission To/From Modules

### Hardware
Transmission between the main raspberry pi controller and each of the connected modules begins and ends with the SPI harness board. 

This board uses a 74HC595 shift register to handle the six CS lines currently used in the KICK Robot system. 

### Protocol
Messages sent to and from the attached modules need to have integrity, and actions need to be coordinated between modules. For these reasons, the KICK Robot system uses an 8-byte message frame for communications. Since the way SPI works means that the module will always be one byte behind the controller, it is set up with some asymmetry. 

Pi Side Example:
| Alignment | Header | Module ID | Data (4 bytes) | Checksum |
| --------- | ------ | --------- | -------------- | -------- |
| 0xBF | 0xF0 \| (0x7 & path) | 0x00 | 0 | Header Value |

Module Side Example:
| Header | Module ID | Data (4 bytes) | Checksum | Alignment |
| ------ | --------- | -------------- | -------- | --------- |
| 0xF0 \| (0x7 & path) | 0x00 | 0 | Header Value | 0xBF |



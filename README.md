# IO-Box is made from stm32f4 that has 32 ports, of which 16 ports are output replays and 16 ports are inputs.
# IO-Box controls through RS485 bus and uses Modbus protocol
##Function code:
##01: Read the stat of relay
05: Write a single relay
06: Set baud rate and address
0F: Write all relay
Example:
Sending 01 05 00 00 FF 00 8C 3A to turn on relay at 00 00 address
01: device adress
05: command for writing a single relay
00 00: register address of controlled relay
FF 00: open relay (00 00: close relay)
8C 3A: CRC16 check sum ò the frist six bytes
Sending 01 01 00 00 00 08 3D CC to read states of relays
01: device address
01: command for reading states of relays
00 00 00 08: Initial address
3D CC: CRC16 check sum of the frist six bytes
Receiving 01 01 01 41 91 B8 to answer how many relay is on
01: device address
01: command for reading states of relays
01: number of bytes returned
41: relay 0 and relay 6 is on, close other relays (41: 0100 0001)
91 B8: CRC16 check sum of the frist six bytes

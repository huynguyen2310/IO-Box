# IO-Box is made from stm32f4 that has 32 ports, of which 16 ports are output replays and 16 ports are inputs. IO-Box controls through RS485 bus and uses Modbus protocol
  <p><strong>Function code:</strong><br>
  01: Read the state of relay<br>
  05: Write a single relay<br>
  06: Set baud rate and address<br>
  0F: Write all relay<br>
<strong>Example:</strong><br>
<strong>Sending 01 05 00 00 FF 00 8C 3A to turn on relay at 00 00 address</strong><br>
01: device adress<br>
05: command for writing a single relay<br>
00 00: register address of controlled relay<br>
FF 00: open relay (00 00: close relay)<br>
8C 3A: CRC16 check sum of the first six bytes<br>
<strong>Sending 01 01 00 00 00 08 3D CC to read states of relays</strong><br>
01: device address<br>
01: command for reading states of relays<br>
00 00 00 08: Initial address<br>
3D CC: CRC16 check sum of the first six bytes<br>
<strong>Receiving 01 01 01 41 91 B8 to answer how many relay is on</strong><br>
01: device address<br>
01: command for reading states of relays<br>
01: number of bytes returned<br>
41: relay 0 and relay 6 is on, close other relays (41: 0100 0001)<br>
91 B8: CRC16 check sum of the first six bytes</p>

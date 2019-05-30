# GP2D12_network
This repository contains code for 2 GP2D12 distance sensors network. Communication between slaves and a master rely on RS-485. Communication between master and receiver device implements RS-232. 

Components used in project:
1xAtmel ATmega2560 (master), 
2xAtmel Atmega328p (slaves), 
3xMax485, 
2xGP2D12

Example schematics can be found here - https://drive.google.com/open?id=1-M8pvuAhSaHILxNf2TCWzY5SSda2fbFE . 

# Communication protocol
To retrieve sensor values following bits have to be send to master: 
bit0 - slave address (0x01, 0x02), 
bit1 - get sensor value command (0xB1).
Slaves send data in following order: number of packets to send(1 byte), data packet(max. 5 bytes + '\n' character), CRC checksum(1 byte + '\n' character).
CRC8 EBU is used to prevent data corruption.

Example client program is provided (RecieverExampleProgram.exe).

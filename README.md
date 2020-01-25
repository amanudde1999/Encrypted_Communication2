# Encrypted_Communication2
# Description: 
This program allows two Arduino's to communicate using RSA encryption and decryption to have a secure communication path.
The Keys are now generated using arithmetic with randomly generated prime numbers, Euler's totient and the Extended Euclidean algorithm.
The keys are sent from server-side to client-side and vice-versa using the "hand-shaking" protocol. 
This handshaking protocol now allows communication only when both Arduino's have a connection, otherwise, no keys will be transmitted.

# Included files (besides README):
- encrypted_communication.cpp
- Makefile

# Required Components:
- 1 x 550 Ohm resistor
- 2 x Arduino MEGA Boards
- 1 x Breadboard

# Wiring Instructions: 
- Arduino 1 Pin 13 <--> Arduino 1 GND 
- Arduino 1 GND <--> Arduino 2 GND 
- Arduino 2 5V <--> Breadboard/550 ohm resistor <--> Arduino 2 Pin 13
- Arduino 1 Pin TX3 <--> Arduino 2 Pin RX3
- Arduino 2 Pin TX3 <--> Arduino 1 Pin RX3

# Running Instructions:

While in the directory that contains the MakeFile and the encrypted_communication_part2.cpp file, open two separate terminals and ensure that both the arduino's have been selected using "arduino-port-select" and appoint one of them as port 0 and the other as port 1 (different when testing on two separate machines). In one of the te`rminals use the command "make upload-0 && serial-mon-0" and in the other terminal use "make upload-1 && serial-mon-1". Please reset both the arduinos at the same time if establishing a connection takes too long or if the arduino continuously times out. The Arduinos start the key generation and inititate the handshake. The serial monitors show messages of progress with handshake. When both the serial moniters show "Connected Established! You may chat now!", you are able to type into one or the other serial monitor and it will appear on the other one.

# Assumptions:
- Will not hold down a key. Holding down a key will flood the input buffer and will give wrong output on the other serial-monitor
- Will not type extremely extremely fast. Doing this will also flood the input buffer, giving wrong output on the other end. 




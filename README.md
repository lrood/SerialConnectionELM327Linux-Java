# SerialConnectionELM327Linux-Java
This Class has a method that passes a command to the ELM327 interface and returns a string

The class is written in Java and needs the JSSC Class for the serial connections. Use this class
to pass an AT command used by the ELM327 interface to communicate with a vehicle's computer.
An unformatted String will be returned to the calling program for further processing.

The best features of the program are the autoport detection and the loops that make sure a value
is returned in the buffer.  The program will return a "Check your Connections" statement if an
exception is thrown.

The ELM327 is an inexpensive interface designed to communicate with a vehicle's OBD II system
(1996 - present).  

The best way to make a serial connection with the ELM327 is probably using the SerialPortEventListener
Class included in JSSC.  The algorithms from this class could be used in that build.

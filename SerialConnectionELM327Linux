import jssc.SerialPort;
import jssc.SerialPortException;

// This class will accept a command to an ELM327 interface device as an argument
// and return the contents of the buffer.  If an exception is thrown the 
// program will return a message prompting the user to check the connections
// and and the ignition
public class SerialConnection
{
    public String connect(String command) 
    {
		String line = "";
		String buffer = "";
        SerialPort serialPort = new SerialPort("/dev/ttyUSB0");
        try 
        {
            serialPort.openPort();//Open serial port
            serialPort.setParams(SerialPort.BAUDRATE_38400, 
                                 SerialPort.DATABITS_8,
                                 SerialPort.STOPBITS_1,
                                 SerialPort.PARITY_NONE);
            serialPort.writeString(command + "\r\n");  // command is passed to the interface
			
			// The buffer is checked every 50 ms 100 times 
			for (int i = 0; i < 100; i++)
			{
					// If information is available it will be read into the buffer variable.
					if (serialPort.getInputBufferBytesCount() > 0)
					{
							buffer = serialPort.readString();
							
							// If the buffer contains bytes it will be stored in the line variable.
							// This is important so that the data is not overwritten with null.
							if (buffer.contains("0") || buffer.contains("TO") || buffer.contains("NO"))
							{
									line = buffer;
							}
					}
					Thread.sleep(50);
			}
			serialPort.closePort();  // Port is closed
		 }	 
         catch (Exception ex) 
         {
            line = "Check your Connections. Turn Ignition On.";           
         }
        return line;  // data is returned to the calling function.  The data can be further parsed by another function.
    }
}

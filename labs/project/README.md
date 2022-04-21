# Introduction :
In our case we decided a trame for transmission of data:
UART data is organized into packets. Each packet contains 1 start bit, 8 data bits. In this project an optional parity bit is not necessary, and at the end of the packet we have 1 stop bits.
To understand you can see what the packet of data can look like :


![Full_Adder](images/TimingDiagram.png)

We need to use a clock in order to use signals, just as we did during laboratories, we use clock_enable process.
### This design includes 1 start bit, 8 data bits and 1 stop bits.We want to creat it with State Machine structure using VHDL.


# Description of how it should work :
## Baud rate definition :
Firstly, it is necessary to know what is this value.
In the UART communication data transmission speed is measured by Baud Rate. Baud rate describes the total number of bit sent through serial communication. It includes Start bit, 
Data byte, Parity bit and Stop bit. Transmitter and receiver need to be maintained in the baud rate.



## Transmission delay :
The transmission rate is measured by bits per second. Each bit has a fixed time duration while transmission. The transmission delay for each bit 104.16 μs which is constant till the end of communication.

### Example
The baud rate is 9600.
The transmission delay can be calculated by Transmission delay =1/9600 =104.16 μs.
That is to say, our solution needs to achieves the baud rate by generating clock enable pulses at those frequencies. 
It is derived from the system clock clk wich we used many time in laboratories, it must be specified in the generic parameter clk_freq.


## Transmit Circuit :
The data on tx data is latched into an internal shift register when the tx ena input is asserted.
Along with the start and stop bits. The baud pulse then allows the system clock to move the register contents to the tx line at the baud rate on a regular basis.
When the transmission is complete and the circuit is ready to take new data to send, the TX Done output informs the user logic.

![image](images/UARTTX.png)


## Receive Circuit :
The receive circuit monitors the rx input on each pulse. If it detects a rising edge to logic high, it recognizes an incoming start bit. 
At this point, it begins shifting the value of the rx line into a shift register at the baud rate.

Once the entire data word is shifted into the register, the receive circuitry verifies the data. 
It then outputs the received data on the rx_data port . A high-to-low transition on the rx_busy port signifies to the user logic that new receive data is now available.

![image](images/UARTRX.png)

































## ADVANTAGES AND DISADVANTAGES OF UARTS
There is no perfect communication protocol, although UARTs are pretty good at what they do. Here are some advantages and disadvantages to help you decide whether they are appropriate for your project:

### ADVANTAGES
    • Only two wires are used.
    • Has a parity bit that can be used to check for errors.
    • The data packet's structure can be modified as long as both sides are prepared.
    • This approach is well-documented and commonly used.
### DISADVANTAGES
    • The data frame size is restricted to a maximum of 9 bits.
    • Multiple slave or master systems are not supported.
    • Each UART's baud rates must be within ten percent of one another.

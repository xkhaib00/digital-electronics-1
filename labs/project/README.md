# Introduction :
In our case we decided a trame for transmission of data:
UART data is organized into packets. Each packet contains 1 start bit, 8 data bits. In this project an optional parity bit is not necessary, and at the end of the packet we have 1 stop bits.
To understand you can see what the packet of data can look like :
![Full_Adder](images/TimingDiagram.png)

We need to use a clock in order to use signals, just as we did during laboratories, we use clock_enable process.
### This design includes 1 start bit, 8 data bits and 1 stop bits.We want to creat it with State Machine structure using VHDL.

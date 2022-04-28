# UART - Universal asynchronous receiver / transmitter

### Team members

* Štěpán Večeřa 
* Romain Fresneau 
* Rishat Khaibullin 

### Table of contents

* [Project objectives](#objectives)
* [Hardware description](#hardware)
* [VHDL modules description and simulations](#modules)
* [TOP module description and simulations](#top)
* [Video](#video)
* [References](#references)

<a name="objectives"></a>

## Project objectives

The data for the UART that will transmit it comes from a data bus. Another device, such as a CPU, RAM, uses the data bus to deliver data to the UART. Data is sent in parallel from the data bus to the UART. After receiving parallel data from the data bus, the  UART creates the data packet by adding a start bit, a parity bit, and a stop bit. The data packet is then serially output at the Tx pin. The Rx pin on the receiving UART reads the data bit by bit. The data is subsequently converted back into parallel form by the receiving UART, which eliminates the start bit, parity bit, and stop bit. At the end, the second part of UART is transmitting the data in parallel way to the data bus on the receiving end.



In our case we decided a trame for transmission of data:
UART data is organized into packets. Each packet contains 1 start bit, 8 data bits. In this project an optional parity bit is not necessary, and at the end of the packet we have 1 stop bits.
To understand you can see what the packet of data can look like :


![Full_Adder](images/TimingDiagram.png)

We need to use a clock in order to use signals, just as we did during laboratories, we use clock_enable process.
#### This design includes 1 start bit, 8 data bits and 1 stop bits.We want to creat it with State Machine structure using VHDL.

### ADVANTAGES AND DISADVANTAGES OF UARTS
There is no perfect communication protocol, although UARTs are pretty good at what they do. Here are some advantages and disadvantages to help you decide whether they are appropriate for your project:

#### ADVANTAGES
    • Only two wires are used.
    • Has a parity bit that can be used to check for errors, but in our solution, we do not use it.
    • The data packet's structure can be modified as long as both sides are prepared.
    • This approach is well-documented and commonly used.
#### DISADVANTAGES
    • The data frame size is restricted to a maximum of 9 bits.
    • Multiple slave or master systems are not supported.
    • Each UART's baud rates must be within ten percent of one another.
    • Do not have full duplex mode
    
This UART is a programmable logic component with a simple asynchronous serial interface that allows for communication. The system clock, baud rate, data length, parity scheme, and oversampling rate can all be customized by the user.
    

<a name="hardware"></a>

## Hardware description

We performed the following steps to implement the UART design on the Nexys A7 board. In fact we used two of them, one is used to be the transmitting entity, the second one is the receiving entity.

For this design, we are only in half duplex, wich means only one of the board can transmit data. That is why we only use two wires, one for the ground and one for transmitting data in parrallel.

![image](images/20220428_140240(0).jpg)


The transmitting board use switches from 0 to 7 to transmit data, the receiving board use LED to let the user see that the data are correctly read.
Here you can see the block diagram of our complete solution :


<a name="modules"></a>

## VHDL modules description and simulations

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


<a name="top"></a>

## TOP module description and simulations

Write your text here.

<a name="video"></a>

## Video

Write your text here

<a name="references"></a>

## References

We used several websites to get informed on UART protocol, here are the links were we used some knowledge.

    • To understand UART transmission with some image of data bus :https://www.analog.com/en/analog-dialogue/articles/uart-a-hardware-communication-protocol.html
    
    • Knowledge to create block diagram : https://www.codrey.com/embedded-systems/uart-serial-communication-rs232/
    
    • Basics about this technologies, applications and adv/dis : https://microcontrollerslab.com/uart-communication-working-applications/
    
    • We really struggled on how to use baud rate, to understand, we used this : https://resources.altium.com/p/serial-communications-protocols-part-two-uart
    
    • Interpretations of simulations : https://forum.digikey.com/t/uart-vhdl/12670
    
    • Maual reference for Nexys board : https://digilent.com/reference/programmable-logic/nexys-a7/reference-manual?redirect=1
    
    • Github cheat sheet
    
    • We would also like to thanks our teacher Tomas Fryza to have the knowledge necessary for the successful completion of our project.
    

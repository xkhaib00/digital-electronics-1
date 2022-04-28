# UART - Universal asynchronous receiver / transmitter

### Team members

* Štěpán Večeřa (responsible for xxx)
* Romain Fresneau (responsible for xxx)
* Rishat Khaibullin (responsible for xxx)

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
### This design includes 1 start bit, 8 data bits and 1 stop bits.We want to creat it with State Machine structure using VHDL.


<a name="hardware"></a>

## Hardware description

Write your text here.

<a name="modules"></a>

## VHDL modules description and simulations

Write your text here.

<a name="top"></a>

## TOP module description and simulations

Write your text here.

<a name="video"></a>

## Video

Write your text here

<a name="references"></a>

## References

1. Write your text here.

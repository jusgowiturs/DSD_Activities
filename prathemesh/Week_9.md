# DSD Qestion Bank

## Week 9

---

1. In a synchronous bus system, a master device initiates a read cycle to a slow slave device. The slave asserts a WAIT signal for 3 clock cycles. If a standard bus cycle consists of 2 clock cycles, and data is sampled at the falling edge of the clock in the final state, how many total clock cycles does this transaction consume?
    - [ ] 3
    - [ ] 5
    - [ ] 6
    - [ ] 8


2. In a Daisy Chain priority interrupt system with 4 devices, where priority decreases from device 1 to device 4, devices 2 and 4 request interrupts simultaneously while the processor is executing the ISR of device 3. What is the correct sequence of events?
    - [ ] The ISR of device 3 finishes, then the ISR of device 4 executes, followed by the ISR of device 2.
    - [ ] The ISR of device 3 is suspended, the ISR of device 2 executes, then the ISR of device 4 executes, after which the ISR of device 3 resumes.
    - [ ] The ISR of device 3 is suspended, the ISR of device 4 executes, then the ISR of device 2 executes, after which the ISR of device 3 resumes.
    - [ ] The ISR of device 3 finishes, then the ISR of device 2 executes, followed by the ISR of device 4.


3. A DMA controller operates in Cycle Stealing mode. A program has two types of instructions: 20% are memory-intensive, each taking 4 cycles, and 80% are ALU-intensive, each taking 1 cycle. The DMA controller steals 1 cycle for every 10 CPU cycles elapsed. What is the approximate percentage slowdown experienced by the CPU program?
    - [ ] 1.0%
    - [ ] 7.5%
    - [ ] 10.0%
    - [ ] 6.25%


4. In a UART receiver, if the receiver's clock runs 2% faster than the transmitter's clock, after approximately how many bits will cumulative timing drift cause the receiver to sample outside the valid bit window? (assuming sampling occurs at the theoretical center of the bit)
    - [ ] 10
    - [ ] 25
    - [ ] 50
    - [ ] 100


5. Which of the following statements about Memory-Mapped I/O (MMIO) and Port-Mapped I/O (PMIO) are TRUE?
    - [ ]  In MMIO, the full general-purpose instruction set of the CPU can be applied directly to peripheral registers.
    - [ ]  PMIO requires the CPU to assert a dedicated I/O select signal to distinguish peripheral access from memory access.
    - [ ] Adopting MMIO reduces the address space available for physical memory.
    - [ ] PMIO typically offers lower access latency than MMIO due to its use of a dedicated address bus.


6. During the invocation of an Interrupt Service Routine (ISR), which of the following actions are performed automatically by the CPU hardware rather than explicitly by the programmer?
    - [ ] Preserving the Program Counter onto the stack before transferring control.
    - [ ] Saving general-purpose registers onto the stack for later restoration.
    - [ ] Loading the Program Counter with the address sourced from the interrupt vector.
    - [ ] Suppressing further interrupts by clearing the interrupt enable flag in the status register.


7. A GPIO pin is configured in Open-Drain output mode. Which of the following conditions are necessary for a logic High to appear on the external pin?
    - [ ] The internal pull-up transistor must be actively driven on.
    - [ ] The internal drain transistor must be in a non-conducting state.
    - [ ] An external pull-up resistor must be connected to the supply rail.
    - [ ] The data direction register must be configured for input mode.


8. In a 3-wire handshaking protocol, which of the following signal transitions guarantee that the receiver has successfully latched the data before the transmitter is permitted to change the data lines?
    - [ ] The data-valid signal transitioning high, followed by the strobe signal transitioning high.
    - [ ] The acknowledgement signal transitioning high, followed by the strobe signal transitioning low.
    - [ ] The acknowledgement signal transitioning low, followed by the data-valid signal transitioning low.
    - [ ] The strobe signal transitioning low, followed by the acknowledgement signal transitioning low.


9. A processor operating at 100 MHz uses polling to interface with an input device. The input device generates events at a rate of 10 events per second. To guarantee no event is missed, the CPU polls the device at 100 times per second. Each polling operation consumes 500 clock cycles, regardless of whether an event is pending.
Calculate the percentage of CPU time consumed by polling overhead.


10. A DMA controller transfers a block of 64 KB (where 1 KB=1024 bytes) from a source device to memory. The system bus has a width of 32 bits. Each 32-bit transfer occupies 4 bus cycles, and the bus clock runs at 50 MHz.
Calculate the total time required to complete the transfer, in milliseconds.


11. A 16-bit up-counting timer is driven by a 24 MHz clock and configured with a prescaler of 1:8. The timer triggers an interrupt on overflow, i.e., when the count rolls over from 0xFFFF to 0x0000.
Determine the decimal integer value that must be preloaded into the timer register so that an interrupt is generated exactly every 10 ms.


## Answers
1. B
2. B
3. D
4. B
5. A, B, C
6. A, C
7. B, C
8. B, D
9. 0.05%
10. 1.31 ms
11. 35536
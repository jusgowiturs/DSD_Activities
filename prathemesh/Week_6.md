# DSD Qestion Bank

## Week 6

---

1. In a 2-bit register implementation, the setup time is $1.5 \text{ ns}$ and the clock-to-Q delay is $2 \text{ ns}$. If the combinatorial logic for the write_en signal adds a delay of $1 \text{ ns}$, calculate the maximum operating frequency (in MHz) of the register bank.


2. Which of the following statements regarding the Verilog implementation of a register bank are TRUE?
    - [ ] Register files are often treated as pure storage rather than part of the system state, meaning it is acceptable to leave them uninitialized provided the software protocol ensures a "write-before-read" sequence.
    - [ ] In a standard synchronous write implementation, the data value present at the input is captured and stored exactly at the triggering clock edge..
    - [ ] An asynchronous read implementation implies that the output data is a combinational function of the read address, changing as soon as the address bits stabilize.
    - [ ] To ensure synthesizability on FPGA resources, all register bank arrays must include a reset branch within the sequential logic to clear every storage bit.


3. Consider the Special Case of Register 0 in a CPU register file. If $R0$ is hardwired to zero, how does this affect the decoder and MUX logic? 
    - [ ] The write decoder requires one fewer output line to function.
    - [ ] The write logic is removed but the read MUX remains the same.
    - [ ] The register still requires thirty-two flip-flops for timing.
    - [ ] The Address decoder must be replaced by a priority encoder.


4. A register bank has a DEPTH of 16 and a WIDTH of 64 bits. How many total D-Flip-Flops are required for storage, and what is the minimum bit-width of the addr signal?


5. In SRAM "Sense Amplifiers," which of the following functions do they perform?
    - [ ] They accelerate the read process by detecting small voltage differences on bit lines.
    - [ ] They reduce power consumption during the read cycle.
    - [ ] They act as the primary storage element for the bit.
    - [ ] They drive the bit lines to full rail-to-rail voltage during a write operation.


6. A system uses a 12-bit address bus to map four $1\text{K} \times 8$ SRAM blocks. The address decoder uses only bit $A[11]$ to select between two memory regions, effectively ignoring bit $A[10]$. A user performs the following sequence of operations:
    a. Write `8hFF` to logical address `0xC3A`. 
    b. Read from logical address `0x83A`.
    Calculate the decimal value of the data returned from the Read operation.



7. Why is Dynamic RAM (DRAM) technology not typically integrated directly into the internal logic fabric of an FPGA?
    - [ ] DRAM utilizes a high-speed multi-transistor cell that creates excessive heat and timing violations in standard logic. 
    - [ ] DRAM requires complex periodic refresh cycles and analog charge storage that are incompatible with digital FPGA gates. 
    - [ ] DRAM architectures only support read-only operations which prevents the dynamic reconfiguration required by FPGA users.
    - [ ] DRAM transistors are physically too large to be routed efficiently between the lookup tables and the routing matrix.


8. Calculate the bandwidth of a DDR4-1600 memory module with a 64-bit bus width. Provide the answer in GB/s.


9. When should a designer choose Distributed RAM over Block RAM in an FPGA?
    - [ ] When creating a very small buffer .
    - [ ] When low-latency is critical.
    - [ ] When implementing a large video frame buffer.
    - [ ] When the memory needs to be placed close to specific combinatorial logic.


10. Which of the following are valid methods for initializing a ROM in an FPGA?
    - [ ] Direct assignment in RTL using an `initial` block.
    - [ ] Loading from an external `.mem` file using `$readmemh`.
    - [ ] Using a JTAG interface during run-time.
    - [ ] Hard-wiring the Bit lines to Ground or VCC in the SRAM cell.


11. In a standard FIFO implementation using circular pointers, which of the following conditions accurately describes the generation of the Full status flag?
    - [ ] The write pointer and read pointer are exactly equal across all bit positions including the extra MSB.
    - [ ] The read pointer has incremented past the write pointer, causing a negative offset in the address logic.
    - [ ] The lower address bits of both pointers are identical, but the most significant bit is different.
    - [ ] The write clock frequency exceeds the read clock frequency by a factor greater than the depth of the array.


12. A FIFO has a depth of 16. The write pointer and read pointer are 5-bit counters. If `wptr = 5'b10010` and `rptr = 5'b00010`, is the FIFO empty, full, or neither?


13. Why do Asynchronous FIFOs require independent read/write clocks? 
    - [ ] To increase the total storage capacity.
    - [ ] To handle data transfer between different clock domains.
    - [ ] Because SRAM cells cannot support two clocks.
    - [ ] To prevent the pointers from ever being equal.


14. Which of the following signals and protocols are typically part of a standard Memory Controller bus interface for a complex system?
    - [ ] Request/Grant handshake signals to manage bus ownership and arbitration. 
    - [ ] Dedicated Address and Data buses for transferring location and payload information. 
    - [ ] Command lines (Read/Write) to specify the type of operation to be performed. 
    - [ ] Burst length and alignment parameters used to optimize high-bandwidth data transfers.

## Answers:
1. 222.22 MHz
2. A, B, C
3. B
4. 1024
5. A, B
6. 255
7. B
8. 12.8
9. A, B, C
10. A, B, C
11. C
12. Full
13. B
14. A, B, C, D
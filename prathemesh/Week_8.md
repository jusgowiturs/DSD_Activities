# DSD Qestion Bank

## Week 8

---

1. A processor uses a 16-bit register architecture but limits the immediate operand field in its instruction encoding to 5 bits. If the processor implements sign-extension to convert this 5-bit value into a 32-bit operand for the ALU, what is the decimal value of the most negative constant that can be represented in a single `ADDI` instruction?


2. Consider the Verilog implementation of sign-extension: `assign extended_imm = {{27{immediate[4]}}, immediate}`;. If the instruction being decoded is `ANDI r1, r2, 0x1F` (where `0x1F` is the 5-bit immediate), what will be the 32-bit hexadecimal value of extended_imm?
    - [ ] $0x0000001F$
    - [ ] $0xFFFFFFFF$
    - [ ] $0x0000000F$
    - [ ] $0x11111111$


3. Which of the following are valid reasons for including immediate operands in an instruction set architecture?
    - [ ] To reduce memory accesses when working with constant values in instructions.
    - [ ] To designate `r0` as a hardwired zero register for use in initialization operations.
    - [ ] To perform bit masking operations directly within instructions without occupying extra registers.
    - [ ] To allow instructions to operate on values stored in memory directly, bypassing the register file entirely.


4. To load the constant decimal value $1000$ into a register $r1$ using a processor with a 5-bit signed immediate limit, a programmer uses the following sequence:
    ADDI r1, r0, 15
    SLLI r1, r1, 6
    ADDI r1, r1, 8
    ADDI r1, r1, 8
What is the intermediate decimal value stored in register $r1$ immediately after the execution of the SLLI (Shift Left Logical Immediate) instruction? 


5. In a `program_counter` module, the PC normally increments by $8'h01$ per cycle. If the current `pc_out` is $8'h1A$ and the instruction at that address is a `JUMP` to a target address $8'h2F$ , what will be the value of `pc_out` in the next clock cycle, assuming `pc_load` is asserted? 


6. A processor implements `BEQ rs1, rs2, addr`. During the execution of this instruction, the control logic evaluates (rs1_data == rs2_data). If this condition is false, which of the following describes the behavior of the Program Counter?
    - [ ] The PC is updated with the computed branch target address.
    - [ ] The PC is updated with the address of the next sequential instruction.
    - [ ] The PC retains its current value until the pipeline flushes the instruction.
    - [ ] The PC is updated with the reset vector address 8'h00.


7. A basic CPU executes instructions in a fixed sequence without any branching or conditional behavior. Which of the following components must be added or modified to support program flow control?
    - [ ] A Program Counter that supports loading arbitrary target addresses.
    - [ ] An ALU that supports comparison operations such as equality checks.
    - [ ] A Register File that hardwires one register to a constant zero value.
    - [ ] Control logic that drives the pc_load signal based on ALU output flags.


8. In fixed-width instruction encoding, why is the branch or jump target address field typically restricted to a small number of bits?
    - [ ] Because control flow transfers in most programs stay within a short range of instructions.
    - [ ] Because the available bit width is shared among the opcode, register fields, and the target address.
    - [ ] Because wider address fields increase the time required to complete the instruction fetch stage.
    - [ ] Because restricting the field width ensures the target address stays aligned to a word boundary.


9. A CPU uses 8-bit addressing and each location stores 32 bits (4 bytes). What is the total storage capacity of this memory in bytes?


10. For a byte-addressable memory system, 32-bit words are stored at aligned addresses. If a 32-bit word is stored starting at address $0x0004$, what is the address of the next sequential 32-bit word?
    - [ ] $0x0005$
    - [ ] $0x0006$
    - [ ] $0x0008$
    - [ ] $0x000C$


11. A 32-bit value $0x12345678$ is stored in a Little-endian memory system starting at address $A$. What is the hexadecimal value of the byte stored at address $A+3$? 


12. What is the primary disadvantage of a Single-Cycle CPU design when interfacing with modern synchronous memory?
    - [ ] It requires the memory interface to operate on both clock edges, increasing power consumption significantly.
    - [ ] The clock period must accommodate the slowest instruction's datapath, which includes the full memory access latency.
    - [ ] It cannot support simultaneous read and write operations because the memory bus is shared across all instruction types.
    - [ ] It requires a dedicated memory controller to handle address translation for each instruction independently.


## Answers
1. -16
2. B
3. A, C
4. 960
5. $8'h2F$
6. B
7. A, B, D
8. B
9. 1024
10. C
11. `0x12`
12. B
# DSD Qestion Bank

## Week 7

---

1. A processor is designed to evaluate the expression $Y = (A \times B) + (C \times D) - (E \times F)$. The hardware consists of one multiplier and one adder/subtractor. If every operation takes exactly one clock cycle and requires its operands to be in registers, what is the minimum number of registers required to compute $Y$ without re-loading any initial values? Assume $A, B, C, D, E, F$ are initially stored in a register file.


2. A register bank uses decoders for write selection and multiplexers for read selection. A Register File has $2^n$ registers, each $W$ bits wide. It features two asynchronous read ports and one synchronous write port. Which of the following statements regarding its hardware implementation are CORRECT?
    - [ ] The total number of 2-to-1 multiplexers required for the read circuitry is $2 \times W \times (2^n - 1)$
    - [ ] A change in the read address will reflect at the output only after the next positive edge of the clock
    - [ ] The write decoder requires $n$ input lines to uniquely address each register
    - [ ] Increasing the number of registers from 8 to 16 requires one additional address bit for each port


3. Consider an 8-bit ALU where the "Multiply" operation is implemented as a combinational array multiplier. The propagation delay of a 1-bit Full Adder is $2ns$, and the delay of an AND gate is $1ns$. Ignoring wire delays and assuming the multiplier is the slowest component in the ALU, calculate the Critical Path Delay (in ns) for the multiplication of two 8-bit unsigned integers. (Use the standard formula for an $N \times N$ carry-save array multiplier: $t_{pd} = [1 + (N-1) + (N-2)] \times t_{gate\_delay}$).


4. A designer is creating a custom 16-bit instruction format for a 3-register operand architecture (rd, rs1, rs2). The processor supports 12 distinct ALU operations. If the designer maximizes the number of registers possible in the register file while keeping the instruction length fixed at 16 bits, how many total registers can the architecture support?
    - [ ] 8
    - [ ] 16
    - [ ] 32
    - [ ] 64


5. A Simple CPU has an 8-bit PC that increments by 1 every clock cycle. The instruction memory is byte-addressable. If the processor starts at pc = 8'h00 after a reset  and must execute a program that calculates the area of 50 different triangles sequentially, where each triangle's calculation requires 4 instructions, what will be the Hexadecimal value of the PC immediately after the last instruction of the 50th triangle is fetched?


6. Given the following timing parameters for a single-cycle processor:
   1. Instruction Fetch (Memory access): $10ns$
   2. Register File Read: $3ns$
   3. ALU Execution: $12ns$ 
   4. Register File Setup Time: $2ns$
   5. Clock-to-Q delay of PC: $1ns$
   What is the maximum clock frequency at which this processor can safely operate?
    - [ ] 33.33 MHz
    - [ ] 35.71 MHz
    - [ ] 40.00 MHz
    - [ ] 50.00 MHz


7. A Register File is designed with $N$ registers, where each register is $W$ bits wide. The architecture requires three asynchronous read ports and one synchronous write port. To implement the read circuitry, the designer uses $2$-to-$1$ multiplexers as the basic building block. If $N = 32$ and $W = 16$, calculate the total number of 2-to-1 multiplexers required solely for the read logic across all ports.


8. An ALU is designed to perform $2^k$ distinct operations using a $k$-bit operation select signal op. If the designer decides to implement a Fused Multiply-Add (FMA) unit—which computes $A \times B + C$ in a single combinational step—to replace separate MUL and ADD instructions, which of the following is the most significant hardware trade-off?
    - [ ] A decrease in the total number of registers required in the register bank.
    - [ ] An increase in the opcode bit-width required in the instruction encoding.
    - [ ] A significant increase in the propagation delay of the critical path.
    - [ ] Elimination of the need for a Decoder in the Register File.


9. A processor uses a fixed-length 12-bit instruction format. The designer is considering two different ISA schemes:
    - Scheme 1: 3-register operand format (rd, rs1, rs2) supporting 8 registers.
    - Scheme 2: 2-register operand format (rd, rs1) where rd acts as both a source and destination, supporting 16 registers.
  Which of the following statements are CORRECT regarding these schemes?
    - [ ] Scheme 1 allows for $2^3$ unique operation codes.
    - [ ] Scheme 2 provides more bits for the opcode than Scheme 1, allowing for a larger instruction set.
    - [ ] In Scheme 2, the instruction encoding would require 8 bits just for register addressing.
    - [ ] Scheme 1 is more efficient for evaluating the expression $R_d = R_{s1} - R_{s2}$ as it avoids overwriting source data.


10. In the `alu_regfile_top` module, the `reg_write_en` signal is critical for data integrity. If a No-Operation (NOP) instruction is introduced into the ISA, how must the Control Unit behave during its execution cycle? (Select all that apply)
    - [ ] It must set `alu_op` to `2'b00` or any don't-care value, since the ALU result will not be written back to the Register File.
    - [ ] It must drive `reg_write_en` to `1'b0` to prevent unintended modification of the Register File.
    - [ ] It must reset the Program Counter to `8'h00`.
    - [ ] It must set `rs1_addr` and `rs2_addr` to the same value to balance the ALU inputs.


## Answer
1. 6
2. A, C, D
3. 27 ns
4. B
5. 8'hC8
6. B
7. 1488
8. C
9. A, B, C, D
10. A, B
# DSD Qestion Bank

## Week 1

---

1. 2-input XOR gate using only 2-input NAND gates. Draw the circuit diagram. How many NAND gates are required at a minimum?

    ---

2. A 3-input digital circuit (Inputs: A, B, C; Output: F) has the following truth table:
    
    | A | B | C | F |
    |---|---|---|---|
    | 0 | 0 | 0 | 1 |
    | 0 | 0 | 1 | 0 |
    | 0 | 1 | 0 | 1 |
    | 0 | 1 | 1 | 1 |
    | 1 | 0 | 0 | 0 |
    | 1 | 0 | 1 | 0 |
    | 1 | 1 | 0 | 1 |
    | 1 | 1 | 1 | 0 |

    Derive the canonical Sum-of-Products (SOP) expression for F directly from the truth table. Then, simplify this expression to its minimal SOP form using Boolean algebra.

    ---

3. A 2-input Boolean function has $2^2 = 4$ possible input combinations. There are $2^4 = 16$ possible unique 2-input functions. A 3-input Boolean function has $2^3 = 8$ possible input combinations. How many unique 3-input Boolean functions exist? Explain your reasoning.

    ---

4. Using De Morgan's Laws and other Boolean identities, simplify the following expression: $Y = \overline{(A + \overline{B}) \cdot (\overline{A} + C)}$

    ---

5. Implement a 2-input XOR gate ($Y = A \oplus B$) using only a single 2-to-1 Multiplexer (MUX) and one NOT gate.

    ---

6. Draw a block diagram illustrating how to build a 4-to-1 MUX using only 2-to-1 MUXes.

    ---

7. A Full-Adder (FA)  adds three 1-bit inputs (A, B, Cin) and produces two outputs (Sum, Cout).
   1. Write the Boolean expression for the Sum output .
   2. Write the Boolean expression for the Cout output .

    ---

8. In a 32-bit Ripple Carry Adder (RCA), each bit's calculation depends on the carry from the previous bit. If a single Full-Adder has a delay of 1.2ns from $C_{in}$ to $C_{out}$, what is the minimum time required to guarantee that the final carry-out (from bit 31) is valid?

    ---

9. An Arithmetic Logic Unit (ALU) often combines the results of several independent operation units (like an adder, a subtractor, an AND unit, and an OR unit).
   1.  What combinational component is used to select one of these four results as the final ALU output?
   2.  If this ALU were expanded to include 8 different operations, how many select lines would this selection component require?

    ---

10. You are given a single positive-edge triggered D-flip-flop (D-FF). The inputs CLK and D are shown in the waveform below. Draw the output Q, assuming Q is initially 0.
    **Wavediagram required**

    ---

11. You are given a positive-edge triggered D-FF with a Clock Enable (CE) pin. The register only updates its value if CE is high at the positive edge of the clock. The inputs CLK, CE, and D are shown below. Draw the output Q, assuming Q is initially 0. **Wavediagram needed**

    ---

12. a CPU's Register File have 4 registers.
    1.  Explain how a multiplexer is used for the read operation . How many select lines would be needed for a 4-register file?
    2.  Explain how a decoder (implied by the write select logic) is used for the write operation . What other signal is necessary to prevent the register from changing on every clock cycle?

    ---

13. Explain the concept of concurrency  in Hardware Description Languages. How does the behavior of the following two Verilog `assign` statements fundamentally differ from the same statements written in a sequential programming language like C?
    ```
    assign t1 = a & b;  // Statement 1
    assign y  = t1 | c; // Statement 2
    ```

    ---

14. In the code from Q13, if the input `c` changes, which `assign` statement(s) are re-evaluated? If the input `a` changes, which `assign` statement(s) are re-evaluated?

    ---

15. Name and briefly describe the three Verilog modeling styles discussed in the lecture.

    ---

16. What is the "Rule of Thumb" for using blocking (=) versus non-blocking (<=) assignments? Which is preferred for modeling combinational logic , and which is preferred for modeling sequential logic?

    ---

17. What specific hardware components will a synthesis tool infer from the following Verilog constructs?
    1.  `assign y = (s == 0) ? a : b;`
    2.  `always @(posedge clk)`

    ---

18. Explain the difference between Simulation and Synthesis. Can all Verilog code that simulates correctly also be synthesized into hardware? Provide an example from the lecture slides of a Verilog construct that is used for simulation but is not synthesizable.

    ---

19. What is the purpose of a test bench? What does it mean for a test bench to be "self-checking"?

    ---

20. ASICs (Application-Specific Integrated Circuits) are custom-designed chips. What are two major advantages of using an FPGA for prototyping a design instead of manufacturing an ASIC?

    ---

21. What is the fundamental programmable logic component in an FPGA, abbreviated as LUT? How does this component's structure allow it to implement any Boolean function of its inputs?

    ---

22. Besides programmable logic (CLBs), FPGAs include dedicated, pre-built hardware blocks known as "hard IP macros"  for performance and efficiency. Name two examples of these blocks.

# DSD Qestion Bank

## Week 1

---

1. A 2-input XOR gate needs to be implemented using only 2-input NAND gates. What is the minimum number of 2-input NAND gates required to construct this circuit?
(Numeric Answer)


1. A 3-input digital circuit has the following truth table:
    
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

    Which of the following represents the simplified Sum-of-Products (SOP) expression for output F?
    - [ ]  $F = \bar{A}\bar{C} + \bar{A}B + B\bar{C}$
    - [ ]  $F = \bar{A}\bar{C} + B\bar{C} + \bar{A}B$
    - [ ]  $F = \bar{A}\bar{C} + \bar{A}B$
    - [ ]  $F = \bar{A}\bar{C} + BC$



3. A 2-input Boolean function has $2^2 = 4$ possible input combinations. There are $2^4 = 16$ possible unique 2-input functions. A 3-input Boolean function has $2^3 = 8$ possible input combinations. How many unique 3-input Boolean functions exist?



4. Using De Morgan's Laws, which of the following is the simplified equivalent of the expression $Y = \overline{(A + \overline{B}) \cdot (\overline{A} + C)}$
   - [ ]  $Y = (\bar{A} + B) \cdot (A + \bar{C})$
   - [ ]  $Y = \bar{A}B + A\bar{C}$
   - [ ]  $Y = A\bar{B} + \bar{A}C$
   - [ ]  $Y = \bar{A}\bar{B} + AC$



5. You want to implement a 2-input XOR gate ($Y = A \oplus B$) using a single 2-to-1 Multiplexer. If input A is connected to the Select line (S), what should be connected to input $I_0$ and input $I_1$?
   - [ ]  $I_0\ =\ B,\ I_1\ =\ B$
   - [ ]  $I_0\ =\ \overline{B},\ I_1\ =\ B$
   - [ ]  $I_0\ =\ B,\ I_1\ =\ \overline{B}$
   - [ ]  $I_0\ =\ 0,\ I_1\ =\ 1$



6. To design a 4-to-1 Multiplexer using only 2-to-1 Multiplexers, how many 2-to-1 MUXes are required?
   (Numeric Answer)



7. A Full-Adder adds three inputs. Which of the following expressions correctly represent the outputs Sum and Carry-out? (MSQ)
   - [ ]  $Sum = A \oplus B \oplus C_{in}$
   - [ ]  $Sum = AB + BC_{in} + AC_{in}$
   - [ ]  $C_{out} = AB + C_{in}(A \oplus B)$
   - [ ]  $C_{out} = A \oplus B \oplus C_{in}$



8. In a 32-bit Ripple Carry Adder (RCA), each bit's calculation depends on the carry from the previous bit. If a single Full-Adder has a delay of 1.2ns from $C_{in}$ to $C_{out}$, what is the minimum time required to guarantee that the final carry-out (from bit 31) is valid?



9. 
   1.  An Arithmetic Logic Unit contains several independent processing units (Adder, AND gate, OR gate, etc.) that calculate results simultaneously. Which combinational component is typically placed at the output stage to select exactly one of these results as the final ALU output?
    - [ ]  Decoder
    - [ ]  Encoder
    - [ ]  Multiplexer
    - [ ]  Register
   2.  If this ALU were expanded to include 8 different operations, how many select lines are required to choose the correct output?(Numerical Answer)



10. A D-Flip-Flop is positive-edge triggered.
    * Initial State: $Q = 0$.
    * At $T=10ns$ (Clock rising edge), $D=1$.
    * At $T=15ns$ (Clock falling edge), $D=0$.
    * At $T=20ns$ (Clock rising edge), $D=0$.
      
      What is the value of Q at T=18ns?

    - [ ]  0 
    - [ ]  1 
    - [ ]  High Impedance (Z) 
    - [ ]  Unknown (X)



11.  A D-Flip-Flop has a Clock Enable (CE) pin. The register updates only if CE is HIGH at the rising edge of the clock.
    * Initial Q = 0.
    * Clock Edge 1: $D=1, CE=0$
    * Clock Edge 2: $D=1, CE=1$
    * Clock Edge 3: $D=0, CE=0$
    <br> What is the value of Q after Clock Edge 3?

      - [ ]  0
      - [ ]  1
      - [ ]  Z
      - [ ]  X

    

12. Regarding the design of a CPU Register File with 4 registers ($R0 - R3$), which of the following statements are TRUE?(MSQ)
    - [ ]  A Multiplexer is used to select which register data to read onto the output bus.
    - [ ]  A Decoder is used to select which register to enable for writing.
    - [ ]  To address 4 registers, the Read Select line must be 2 bits wide.
    - [ ]  To address 4 registers, the Write Select line must be 4 bits wide.



13. Consider the following Verilog code:
    ```
    assign t1 = a & b;  // Statement 1
    assign y  = t1 | c; // Statement 2
    ```
    Unlike C programming, how does Verilog treat these lines?
    - [ ]  Line 1 is always executed before Line 2. 
    - [ ]  They execute concurrently; if c changes, Line 2 evaluates immediately, regardless of Line 1. 
    - [ ]  They execute sequentially; Line 2 only evaluates after Line 1 finishes. 
    - [ ]  Line 2 cannot evaluate until t1 is stable.



14. In the code above, which assign statements will be re-evaluated if the input `a` changes logic state?
    - [ ]  Only Statement 1 
    - [ ]  Only Statement 2 
    - [ ]  Statement 1, and subsequently Statement 2 (if t1 changes) 
    - [ ]  Neither statement



15. Which of the following are recognized modeling styles in Verilog?(MSQ)
    - [ ]  Dataflow Modeling  
    - [ ]  Behavioral Modeling  
    - [ ]  Structural Modeling  
    - [ ]  Physical Modeling 



16. According to the standard "Rule of Thumb" for synthesis, which assignment operator should be used for modeling Sequential Logic (e.g., Flip-Flops)?
    - [ ]  Blocking assignment (=) 
    - [ ]  Non-blocking assignment (<=) 
    - [ ]  Continuous assignment (assign) 
    - [ ]  Equality operator (==)



17. Match the Verilog construct to the hardware component a synthesis tool would typically infer.
    1.  `assign y = (s == 0) ? a : b;`
    2.  `always @(posedge clk)`
    - [ ]  1 $\rarr$ D-Flip-Flop, 2 $\rarr$ Multiplexer 
    - [ ]  1 $\rarr$ Multiplexer, 2 $\rarr$ D-Flip-Flop 
    - [ ]  1 $\rarr$ Latch, 2 $\rarr$ Register 
    - [ ]  1 $\rarr$ Decoder, 2 $\rarr$ Counter



18. Which of the following Verilog constructs are generally NOT synthesizable (used for simulation only)?(MSQ)
    - [ ]  `initial` blocks 
    - [ ]  `#10` (Delays) 
    - [ ]  `always @(posedge clk)` 
    - [ ]  `$display` statements



19. What does it mean for a test bench to be "Self-Checking"?
    - [ ]  It generates a waveform file for manual inspection. 
    - [ ]  It automatically computes expected outputs and compares them against the DUT (Design Under Test) outputs, printing errors if they mismatch. git 
    - [ ]  It synthesizes the design into gates to check for timing errors. 
    - [ ]  It fixes syntax errors in the Verilog code automatically.

    

20. What are the major advantages of using an FPGA for prototyping compared to manufacturing a custom ASIC?(MSQ)
    - [ ]  Lower Non-Recurring Engineering (NRE) costs. 
    - [ ]  Faster time-to-market. 
    - [ ]  Higher maximum clock frequency than ASIC. 
    - [ ]  Ability to fix logic bugs by updating the bitstream.



21. The fundamental programmable logic component in an FPGA is the LUT. How does a 4-input LUT implement a boolean function?
    - [ ]  It uses mechanical switches to rewire gates. 
    - [ ]  It acts as a small RAM (16x1 bits) storing the Truth Table of the function. 
    - [ ]  It uses a processor to calculate the boolean algebra equation. 
    - [ ]  It constructs the function using only NAND gates.



22. Modern FPGAs contain "Hard IP" (dedicated silicon blocks) to improve efficiency. Which of the following are examples of Hard IP commonly found in FPGAs?
    - [ ]  Block RAM (BRAM) 
    - [ ]  DSP Slices (Multipliers) 
    - [ ]  LUTs (Look Up Tables) 
    - [ ]  Clock Management Tiles (PLL/MMCM)


## Answers:
1. 4
2. A
3. 256
4. B
5. C
6. 3
7. A, C
8. 38.4 ns
9. C; 3
10. B
11. B
12. A, B, C
13. B
14. C
15. A, B, C
16. B
17. B
18. A, B, D
19. B
20. A, B, D
21. B
22. A, B, D
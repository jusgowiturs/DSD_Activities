# DSD Qestion Bank

## Week 2

---

1. Given the following Verilog module:
    ```
    module mux_analysis (
    input  logic sel, a, b,
    output logic y
    );
    assign y = (sel) ? a : b;
    endmodule
    ```
    What is the value of output `y` if `sel = 1'bx`, `a = 1'b1`, and `b = 1'b0`?
   - [ ]  `1'b1` 
   - [ ]  `1'b0` 
   - [ ]  `1'bx`
   - [ ]  `1'bz`

    

2. Consider the following Verilog code snippet intended to describe a combinational logic block:
    ```
    reg y;
    always @(a or b) begin
        if (sel)
            y = a ^ b;
    end
    ```
    Which of the following statements accurately describe the consequences of this coding style during Simulation and Synthesis?
   - [ ] Simulation: If `a` and `b` are held constant and `sel` changes value, the output `y` will not update immediately.
   - [ ] Synthesis: The synthesis tool will infer a D-Flip-Flop for `y` because the value must be preserved when `sel` is 0.
   - [ ] Synthesis: The synthesis tool will infer a Transparent Latch for `y` because the if statement is incomplete.
   - [ ] General: This code results in a Simulation-Synthesis Mismatch because the sensitivity list does not match the signals read in the procedural block.
  


3. For the module below, what is the value of `bus_data` if `en1 = 1'b1`, `en2 = 1'b1`, `data1 = 1'b1`, and `data2 = 1'b0`?
    ```
    module tristate_bus (
    input  logic en1, data1,
    input  logic en2, data2,
    output logic bus_data
    );
    assign bus_data = (en1) ? data1 : 1'bz;
    assign bus_data = (en2) ? data2 : 1'bz;
    endmodule
    ```
    - [ ] `1'b1`
    - [ ] `1'b0`
    - [ ] `1'bx`
    - [ ] `1'bz`

    

4. Which of the following statements are TRUE regarding the code snippet below?
    ```
    always_comb begin
        if (sel == 1'b1) begin
            y = a;
        end
    end
    ```
    - [ ] It infers a 2-to-1 Multiplexer. 
    - [ ] It infers a Latch for signal `y`. 
    - [ ] The output `y` retains its previous value when `sel` is `0`. 
    - [ ] This is considered a safe coding style for combinational logic.
    

5. Consider the following `always_comb` block. How many distinct 2-bit values of `op` will cause a latch to be inferred?
    ```
    always_comb begin
        case (op)
            2'b00: y = a + b;
            2'b01: y = a - b;
            2'b10: y = a & b;
        endcase
    end
    ```



6. In the module below, which modeling issue is present?
   ```
    module circuit (input a, output y);
        logic temp;
        assign temp = y | a;
        assign y    = temp & a;
    endmodule
    ```
    - [ ] Inferred Latch
    - [ ] Combinational Loop
    - [ ] Race Condition
    - [ ] Improper Timescale

    

7. Analyze the hardware inferred for outputs `y_A` and `y_B`.
    ```
    always_comb begin
        y_A = 1'b0; // Default
        if (enable) begin
            y_A = a;
            y_B = b;
        end
    end
    ```
    - [ ] `y_A` infers a latch.
    - [ ] `y_A` infers pure combinational logic.
    - [ ] `y_B` infers a latch.
    - [ ] `y_B` infers pure combinational logic.

    

8. Why is the following code style dangerous for combinational logic?
    ```
    always_comb begin
        temp <= a & b; 
        y    = temp | c; 
    end
    ```
    - [ ] It causes syntax errors in SystemVerilog.
    - [ ] It simulates differently than the synthesized hardware.
    - [ ] It creates a transport delay of 1 time unit.
    - [ ] It forces the synthesis tool to ignore `temp`.

    

9. You are given the following snippet of code from a testbench:
    ```
    assign #3 p1 = a & b;
    assign #5 p2 = b | c;
    assign #2 y  = p1 ^ p2;
    ```
    If input `b` changes, causing both `p1` and `p2` to change eventually, what is the maximum total propagation delay from `b` to `y`?

    

10. Which of the following statements correctly distinguishes a Verilog function from a task?
    - [ ] Functions must return exactly one value and cannot have delays; tasks can have delays and return value.
    - [ ] Functions must return exactly one value and cannot have delays; tasks can have delays and no return value.
    - [ ] Functions are purely for testbenches, task are synthesizable.
    - [ ] Functions can call tasks, but tasks cannot call functions.

    

11. Consider the "Inertial Delay" model: `assign #5 y = a`; If a pulse of width 3ns appears on input `a`, what happens at output `y`?
    - [ ] A 3ns pulse appears at `y` after a 5ns delay.
    - [ ] A 5ns pulse appears at `y`.
    - [ ] No change appears at `y`.
    - [ ] The simulator throws an error.

    

12. You are writing a self-checking testbench. Which of the following components are essential for it to function correctly?
    - [ ] An instantiation of the Design Under Test.
    - [ ] An `initial` block to generate stimulus.
    - [ ] A logic analyzer connected to the FPGA.
    - [ ] A mechanism to compare DUT outputs against expected values.


## Answer
1. C (  )
2. A, C, D
3. C
4. B, C
5. 1
6. B
7. B, C
8. B
9. 7
10. B 
11. C ( The input will vanish before the delay hence no change output )
12. A, B, D ( Testbech is only used in simulation, no use of FPGA )
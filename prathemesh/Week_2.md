# DSD Qestion Bank

## Week 2

---

1. Given the following Verilog module, analyze the value of the output `y` for each of the following input combinations. Explain your reasoning for each case, paying close attention to how Verilog's 4-valued logic propagates.
    ```
    module mux_analysis (
    input  logic sel, a, b,
    output logic y
    );
    assign y = (sel) ? a : b;
    endmodule
    ```
   1. `sel = 1'b1, a = 1'bz, b = 1'b0` 
   2. `sel = 1'b0, a = 1'bx, b = 1'b1`
   3. `sel = 1'bx, a = 1'b1, b = 1'b0`
   4. `sel = 1'bx, a = 1'b1, b = 1'b1`

    ---

2. Analyze the following module.
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
    What will be the value of `bus_data` if:
    1. `en1 = 1'b1, en2 = 1'b0, data1 = 1'b1, data2 = 1'b0`
    2. `en1 = 1'b0, en2 = 1'b0, data1 = 1'b1, data2 = 1'b0`
    3. `en1 = 1'b1, en2 = 1'b1, data1 = 1'b1, data2 = 1'b0`

    ---

3. Design a 4-to-1 multiplexer that operates on 8-bit data buses. The module should have four 8-bit data inputs (data_in_0 to data_in_3), a 2-bit select line (sel), and one 8-bit inout bus (shared_bus). The selected input should drive the shared_bus. All unselected inputs should be in a high-impedance state (z). This component is intended to be part of a larger bus system.

    ---

4. A junior designer wrote the following code to implement a 2-to-1 MUX. The synthesis tool issues a warning: "Inferred latch for signal `y`". 
    ```
    module bad_mux (
    input  logic sel, a, b,
    output logic y
    );
    always_comb begin
        if (sel == 1'b1) begin
        y = a;
        end
    end
    endmodule
    ```
    1. Explain exactly which part of this `always_comb` block causes a latch to be inferred.
    2. What is the behavioral difference between the intended MUX and the hardware this code produces?
    3. Rewrite the `always_comb` block using the "preferred coding style" (with default assignments) to eliminate the latch and correctly model a MUX.

    ---

5. Analyze the following `always_comb` block, which is intended to be a simple 2-bit-input ALU.
   ```
    module incomplete_case (
    input  logic [1:0] op,
    input  logic [3:0] a, b,
    output logic [3:0] y
    );
    always_comb begin
        case (op)
        2'b00: y = a + b;
        2'b01: y = a - b;
        2'b10: y = a & b;
        endcase
    end
    endmodule
    ```
    1. This code also infers a latch. Why?
    2. What specific input combination for `op` will trigger the latching behavior?
    3. Fix the code by adding one line to ensure it remains purely combinational.

    ---

6. Consider the following module.
    ```
    module comb_loop (
    input  logic a,
    output logic y
    );
    logic temp;
    assign temp = y | a;
    assign y    = temp & a;
    endmodule
    ```
    1. Identify the combinational loop.
    2. What error or warning do you expect the synthesis tool to report?
    3. How would you expect a simulator to behave when `a` changes from 0 to 1? (Assume zero gate delays).

    ---

7. This module is intended to set `y_A` based on `a` and `y_B` based on `b` when `enable` is high.
    ```
    module partial_assign (
    input  logic enable, a, b,
    output logic y_A, y_B
    );
    always_comb begin
        y_A = 1'b0; // Default assignment
        if (enable) begin
        y_A = a;
        y_B = b; // No default assignment for y_B
        end
    end
    endmodule
    ```
    1. What hardware is inferred for `y_A`?
    2. What hardware is inferred for `y_B`?
    3. Explain the difference in the synthesized hardware and why this discrepancy occurs, even though both assignments are inside the same if block.

    ---

8. A designer mixed blocking and non-blocking assignments inside an `always_comb` block, which is very poor practice.
    ```
    module mixed_assigns (
    input  logic a, b, c,
    output logic y
    );
    logic temp;
    always_comb begin
        temp <= a & b; // Non-blocking
        y    = temp | c;  // Blocking
    end
    endmodule
    ```
    1. Explain the semantic difference in simulation between `temp = a & b;` and `temp <= a & b;` inside a combinational block.
    2. While this might synthesize correctly, why is it a dangerous coding style?
    3. Rewrite the module to be functionally equivalent using only blocking assignments (=) as is standard for combinational logic.

    ---

9. explain the fundamental reason why an `always_comb` block infers a latch when an output is not assigned a value under all possible conditions (e.g., in every branch of an if-else or every case of a case statement). What "memory" aspect is being created?

    ---

10. Design a 4-bit priority encoder. It has a 4-bit input `req` and two outputs: a 2-bit binary number `grant` indicating the highest-priority request, and a 1-bit output `valid` that is high if any request is active. `req[3]` has the highest priority, and `req[0]` has the lowest.

    ---

11. Analyze the provided ALU module.
    ```
    module alu_flags(
    input  logic [7:0] a, b,
    input  logic [1:0] op,
    output logic [7:0] result,
    output logic       zero
    );
    always_comb begin
        result = 8'h00; // Default
        case (op)
        2'b00: result = a + b;
        2'b01: result = a - b;
        default: result = a & b;
        endcase
        
        zero = (result == 8'h00); // Dependent on 'result'
    end
    endmodule
    ```
    1. Is the `zero` flag a Moore or Mealy style output relative to the `op` input?
    2. Explain the data dependency that dictates the order of operations inside the `always_comb` block.
    3. What would happen if the line `zero = (result == 8'h00);` was placed before the `case` statement?

    ---

12. You need to implement a module with two 8-bit inputs (`a`, `b`) and two 8-bit outputs (`y1`, `y2`).
    * `y1` should be the bitwise `XOR` of `a` and `b`.
    * `y2` should be `a` if `a > b`, otherwise it should be `b`
    
    Implement this module using the most appropriate Verilog construct for each output and justify your choice for each.

    ---

13. **Diagram Required** Write the Verilog code for the circuit in the diagram using only `assign` statements and intermediate `wires` for the outputs of `u1` and `u2`.

    ---

14. **Wave diagram needed**
    You have an input signal a as shown in the waveform. You instantiate two different buffers: `assign #5 y_inertial = a;` `always @(a) y_transport <= #5 a;` 
    Draw the resulting waveforms for `y_inertial` and `y_transport` from `t=0` to `t=40ns`. Pay close attention to the `3ns` pulse at `t=20ns`. Explain the difference in behavior.

    ---

15. A designer includes the line `assign #2 temp = a & b;` in their synthesizable design, thinking it will guarantee a 2ns gate delay. 
    1.  Is this assign #2 delay synthesizable?
    2.  What is this type of delay used for?
    3.  What actually determines the delay of the AND gate in the final hardware?

    ---

16. Given the following module, what is the total delay from a change in input a to a change in output y? What is the total delay from c to y?
    ```
    module multi_path_delay (
    input  logic a, b, c,
    output logic y
    );
    logic p1, p2;
    assign #3 p1 = a & b;
    assign #5 p2 = b | c;
    assign #2 y  = p1 ^ p2;
    endmodule
    ```

    ---

17. You are given the 4-bit priority encoder from question 10. Write a self-checking testbench for it. The testbench must:
    1. Instantiate the DUT.
    2. Use an initial block to provide a sequence of at least 4 different test vectors for the `req` input.
    3. For each test vector, check if the `grant` and valid outputs match the expected values.
    4. Print a custom error message to the console using `$display` if a mismatch is found.
    5. Print "All tests passed!" and use `$finish` at the end.

    ---

18. Explain the three main differences between a Verilog `task` and a `function`. Based on these differences, which one must you use to model a complex bus-read protocol that requires waiting for a `ready` signal and takes multiple clock cycles? Why?

    ---

19. A designer wrote the following testbench. The compiler gives an error on the function definition.
    ```
    module tb;
    logic [3:0] a;
    
    // This function is intended to apply stimulus
    function void apply_stim (input [3:0] data);
        a = data;
        #10; // Wait 10 time units
    endfunction

    initial begin
        apply_stim(4'hA);
        apply_stim(4'h5);
        #10 $finish;
    end
    endmodule
    ```
    1. What is the error?
    2. Why is this rule in place for functions but not for tasks?
    3. How would you fix this by changing the `function` to a `task`?

    ---

20. Write a testbench initial block that fully tests a 4-to-1 MUX (inputs `data_in[3:0]`, `sel[1:0]`). Use a `for` loop (or nested loops) to iterate through all 4 possible values of `sel` and provide unique data for each selection to verify its operation. Include a 10-unit delay between each change.

    ---

21. You have a testbench module named `tb_top` which instantiates a DUT named `u_my_alu`. How would you modify the initial block in `tb_top` to:
    1.  Create a VCD file named `alu_waves.vcd`?
    2.  Dump all signals within the `tb_top` module and all signals within the `u_my_alu` instance?
# DSD Qestion Bank

## Week 3

---

1. Which of the following Verilog code snippets correctly model a D-flip-flop with a synchronous active-low reset?
   - [ ] 
    ```
    always_ff @(posedge clk) begin
        if (!rst_n) q <= 1'b0;
        else q <= d;
    end
    ```
   - [ ] 
    ```
    always_ff @(posedge clk or negedge rst_n) begin
        if (!rst_n) q <= 1'b0;
        else q <= d;
    end
    ```
   - [ ] 
    ```
    always @(posedge clk) begin
        q <= (!rst_n) ? 1'b0 : d;
    end
    ```
   - [ ] 
    ```
    always_ff @(posedge clk) begin
        if (rst_n) q <= d;
        else q <= 1'b0;
    end   
    ```


2. Consider the following Verilog code describing a 4-bit loadable shift register:
    ```
    module shifter (input clk, rst, load, shift_en, input [3:0] par_in, input ser_in, output reg [3:0] q);
    always_ff @(posedge clk) begin
        if (rst)       q <= 4'b0;
        else if (load) q <= par_in;
        else if (shift_en) q <= {q[2:0], ser_in}; 
    end
    endmodule
    ```
    If the inputs are `rst=0`, `load=1`, `shift_en=1`, `par_in=4'b1010`, `ser_in=1` at the rising edge of the clock, what will be the value of `q` after the clock edge?
    - [ ] 4'b0101
    - [ ] 4'b1010
    - [ ] 4'b0100
    - [ ] The result is indeterminate because `load` and `shift_en` conflict.


3. A digital circuit has a flip-flop with a clock-to-Q delay ($T_{cq}$) of 2 ns and a setup time requirement ($T_{setup}$) of 1 ns. The combinational logic placed between two such flip-flops has a minimum propagation delay of 3 ns and a maximum propagation delay of 7 ns. What is the maximum clock frequency (in MHz) at which this circuit can operate reliably? (Answer as an integer)


4. Which of the following statements regarding Blocking (`=`) and Non-Blocking (`<=`) assignments in Verilog synthesis are TRUE? 
   - [ ] Using blocking assignments in a sequential `always` block creates a race condition in simulation but synthesizes correctly to flip-flops.
   - [ ] Mixing blocking and non-blocking assignments to the same variable within the same `always` block is a recommended practice for creating complex pipelines.
   - [ ] In a combinational `always` block, using non-blocking assignments can lead to synthesis-simulation mismatches or unwanted latches.
   - [ ] A chain of non-blocking assignments (e.g., `a <= b; b <= c;`) inside a clocked block infers a shift register (pipeline), whereas a chain of blocking assignments (e.g., `a = b; b = c;`) infers a single flip-flop with combinational logic.


5. Analyze the following code snippet intended for synthesis:
    ```
    always @(posedge clk) begin
        a = b + c;
        d = a + 1;
    end
    ```
    What hardware structure will a synthesis tool most likely infer for signals `a` and `d`?
    - [ ] Two flip-flops in series, where `d` is registered one cycle after `a`.
    - [ ] Two parallel flip-flops where `a` gets `b+c` and `d` gets `(b+c) + 1` simultaneously.
    - [ ] A flip-flop for `d` only; `a` becomes a purely combinational wire.
    - [ ] This code will trigger a syntax error because blocking assignments cannot be used in sequential blocks.


6. In a design intended for synthesis, a developer writes the following code to implement a 3-stage shift register:
    ```
    always_ff @(posedge clk) begin
        q1 = in_data;
        q2 = q1;
        q3 = q2;
    end
    ```
    Based on Verilog synthesis semantics, what is the actual functional behavior of the resulting hardware?
    - [ ] It operates correctly as a 3-stage shift register with a latency of 3 clock cycles.
    - [ ] It creates a race condition during synthesis, leading to indeterminate hardware behavior.
    - [ ] It operates as a set of parallel registers where `q1`, `q2`, and `q3` all update to `in_data` on the same clock edge.
    - [ ] It infers a combinational loop because the outputs depend on variables updated in the same block.


7. Identify the scenarios that will likely result in the inference of an unintended transparent latch during synthesis. (Select all that apply)
    - [ ] An `always_comb` block with an `if` statement that lacks an `else` branch, where the output variable is not assigned a default value.
    - [ ] A `case` statement inside an `always_comb` block where not all possible cases are covered, and there is no `default` clause.
    - [ ] A sequential `always_ff` block with a synchronous reset where the `else` (reset inactive) condition is missing.
    - [ ] An `assign` statement with a self-referencing loop (e.g., `assign q = enable ? d : q;`).


8. In the context of static timing analysis, which of the following best describes the "Hold Time" violation?
    - [ ] The data signal arrives at the destination flip-flop too late, missing the capture edge.
    - [ ] The data signal changes too quickly after the clock edge, corrupting the data currently being captured.
    - [ ] The clock signal arrives at the destination flip-flop before the source flip-flop, causing a negative skew.
    - [ ] The combinational logic delay is longer than the clock period.


9. Regarding Verilog coding styles for Finite State Machines (FSMs) and general sequential logic, which of the following practices are recommended for clean synthesis?
    - [ ] Combining the next-state logic and the state register update into a single `always_ff` block to save lines of code.
    - [ ] Separating the design into three parts: `always_ff` for state registers, `always_comb` for next-state logic, and `always_comb` for outputs.
    - [ ] Using `#delay` statements inside `always_ff` blocks to fix hold time violations in the synthesized netlist.
    - [ ] Using `localparam` or `enum` to define state encodings rather than hard-coding magic numbers.


10. You are designing a counter using a T-flip-flop. The T-flip-flop toggles when T=1 and holds when T=0. The T input is driven by a logic gate with a propagation delay of 3 ns. The T-flip-flop has a setup time of 2 ns and a clock-to-Q delay of 4 ns. What is the minimum clock period (in ns) required for this counter to operate correctly? (Assume the output Q feeds back to the logic gate).



## Answers:
1. A, C, D
2. B ( `load` have higher priority )
3. 100 ( Hint: Critical Path Delay )
4. C, D ( [Check out](https://www.chipverify.com/verilog/verilog-blocking-non-blocking-statements#/) )
5. B ( Hint: Blocking vs Non-blocking assignment )
6. C
7. A, B, D ( Hint: latch vs flip-flop )
8. B
9. B, D ( Best practices )
10. 9
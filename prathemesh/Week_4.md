# DSD Qestion Bank

## Week 4

---

1. In high-speed FPGA designs where timing closure is a major concern, why might a Moore machine be preferred over a Mealy machine for critical control signals?
   - [ ] It uses fewer states to represent the same logic.
   - [ ] It has a faster response time to external inputs.
   - [ ] It eliminates combinational paths from input to output.
   - [ ] It requires less area by minimizing decoding logic.


2. Which state encoding method is specifically noted for its ability to reduce power consumption by minimizing switching activity?
    - [ ] Binary encoding
    - [ ] One-hot encoding
    - [ ] Gray code encoding
    - [ ] Sequential encoding


3. Which of the following are benefits of using a Mealy machine implementation in a digital system? (Select all that apply)
    - [ ] Faster response to inputs.
    - [ ] Lower latency for protocol implementation.
    - [ ] Often requires fewer states compared to a Moore machine.
    - [ ] Better for crossing clock domains safely.


4. When implementing the state register in SystemVerilog, which of the following practices is recommended to ensure a clean transition to a known state?
    - [ ] Using `always_comb` with a default assignment.
    - [ ] Using `always_ff` with a synchronous reset.
    - [ ] Using a `generate` block to instantiate the reset logic.
    - [ ] Mixing next-state logic and state registers in a single `always` block.


5. A Finite State Machine is designed using One-hot encoding. If the machine has 6 distinct states, how many bits will the state register contain?


6. According to the design best practices for FSMs in SystemVerilog, which of the following should be followed? (Select all that apply)
    - [ ] Use `always_comb` for the state register and `always_ff` for next-state logic.
    - [ ] Define default outputs and include a default next state.
    - [ ] Use enumerated types for state definitions.
    - [ ] Keep next-state logic, state registers, and output logic in one large `always` block for efficiency.


7. Consider a Lift Controller FSM where the `door_open_cmd` is implemented as a Mealy output dependent on the `at_target_floor` sensor. If the sensor signal experiences a brief 5ns "glitch" (noise pulse) while the elevator is in the `MOVING_UP` state, what is the most likely architectural consequence?
    - [ ] The FSM will immediately transition to the `STOPPED` state and stay there.
    - [ ] The `door_open_cmd` will momentarily pulse high, potentially attempting to open the doors while the lift is in motion.
    - [ ] The system will ignore the noise because Mealy outputs are filtered by the system clock.
    - [ ] The state register will enter a metastable state, requiring a hard reset.


8. Why is One-hot encoding often preferred over Binary encoding for FSMs in high-speed FPGA designs?
    - [ ] It uses the minimum number of registers.
    - [ ] It reduces the complexity of decode logic, increasing speed.
    - [ ] It ensures that only a single bit changes between any two states.
    - [ ] It is primarily used to save power by reducing switching activity.


9. Regarding Parameterized Designs, which statements are true? (Select all that apply)
    - [ ] `localparam` is used for compile-time constants that should not be overridden by the parent module.
    - [ ] `generate` blocks are only used for simulation and are not synthesizable.
    - [ ] `genvar` is a standard Verilog type used for loop variables in sequential logic.
    - [ ] Parameters can be used to configure the width and depth of hardware structures like shift registers.
    - [ ] Parameters can be overridden via named or positional mapping during instantiation.


10. Observe the following SystemVerilog snippet:
    ```
    typedef enum logic [1:0] {
        IDLE=2'b00,
        MOVING_UP=2'b01,
        MOVING_DOWN=2'b10,
        STOPPED=2'b11} state_t;
    ```
    How many total bits are allocated for the current_state signal?


11. In the Traffic Light Controller case study, which safety requirements must the FSM logic strictly enforce? (Select all that apply)
    - [ ] No conflicting green signals between North-South and East-West.
    - [ ] An All-red period during transitions between directions.
    - [ ] Pedestrian walk signals must start before the vehicle yellow light finishes.
    - [ ] The system must enter a safe state (all red) upon reset.
    - [ ] The yellow light timing must be variable based on traffic density.


12. A shift register is instantiated with `WIDTH = 16` and `DEPTH = 8`. How many total flip-flops are synthesized for the stages array?

## Answers:
1. C (Elimination of input to output reduces the path delay, hence increasing speed)
2. C (In gray code encoding only one bit flip happens in adjecent states)
3. A, B, C (Mealy outputs react immediately to input changes within the current clock cycle)
4. B (Using an `always_ff` block ensures that the next state will predictibally update at the clock edge and wont change asynchronously)
5. 6 (One register per state)
6. B, C (Standard structural guidelines for synthesizable and safe FSM design)
7. B (Moore outputs depend on the state and the input)
8. B (One hot encoding is simpler to decode)
9. A, D, E (Parameters enable modularity while `localparam` protects internal constants)
10.  2 (The `logic [1:0]` definition explicitly allocates 2 bits)
11.  A, B, D (Critical safety requirements to prevent intersection accidents)
12.  128 (Total flip-flops = Width (16) × Depth (8))
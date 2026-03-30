# DSD Qestion Bank

## Week 5

---

1. In a hierarchical design, why is "Interface Definition" considered the most critical phase for parallel development?
    - [ ] It dictates the specific gate-level technology mapping for all subsystems simultaneously to ensure timing closure across the entire SoC.
    - [ ] It allows different teams to develop internal module logic independently as long as the predefined input, output, and functional boundaries are maintained.
    - [ ] It provides a system-level specification that automatically generates the RTL code for the interconnects between the ALU, Cache, and Memory Controller.
    - [ ] It enables the top-down decomposition process to bypass the verification stage by ensuring that all modular components are inherently compatible at the hardware level.


2. A designer transitions from a combinational parallel multiplier to an FSM-based sequential multiplier using a single adder. What is the most likely result? 
    - [ ] Increase in Area, Increase in Latency. 
    - [ ] Decrease in Area, Decrease in Latency.
    - [ ] Decrease in Area, Increase in Latency.
    - [ ] Increase in Area, Decrease in Latency.


3. A $12 \times 12$ bit signed (2's complement) multiplier is implemented. What is the minimum number of bits required for the output product to ensure no overflow occurs?


4. Consider an 8-bit parallel multiplier using a balanced binary adder tree. If each 16-bit adder has a delay of $T_{add}$ and partial product generation takes $T_{gen}$, what is the total combinational delay in terms of $T_{add}$ and $T_{gen}$? 


5. To multiply two 8-bit signed numbers, how many partial products are generated before the summation stage?


6. When computing the partial products of an 8-bit signed multiplication between multiplicand $A$ and multiplier $B$, how should the $0^{th}$ partial product be sign-extended before being fed into the adder tree?
    - [ ] Zero-extend $A$ to 16 bits.
    - [ ] Sign-extend $A$ to 16 bits.
    - [ ] Sign-extend $A$ to 9 bits.
    - [ ] No extension is needed.


7. Which of the following registers are essential components of the datapath for a sequential "Shift and Add" multiplier? (MSQ)
    - [ ] A register to hold the multiplicand.
    - [ ] A shift register to hold the multiplier.
    - [ ] An accumulator register for the product result.
    - [ ] A Program Counter.


8. What is the primary benefit of "Separation of Concerns" between Control and Datapath?
    - [ ] It optimizes the logic depth of the arithmetic units to ensure that every operation in the datapath is completed within a single clock cycle.
    - [ ] It allows the FSM logic to be adapted for different algorithms while reusing the same arithmetic components and interface registers.
    - [ ] It eliminates the requirement for multiplexers (MUX) by hardwiring the control signals directly to the sequential storage elements.
    - [ ] It provides a deterministic method to guarantee Pareto dominance for both area and power consumption without requiring design space exploration.


9. Design A has (Area=20, Delay=30). Design B has (Area=15, Delay=35). Design C has (Area=25, Delay=25). Which statement is true regarding Pareto dominance?
    - [ ] Design A Pareto dominates Design B because it achieves a lower delay despite a moderate area overhead.
    - [ ] Design B Pareto dominates Design C because it achieves the smallest area across all three designs.
    - [ ] No single design Pareto dominates all others, as each design is strictly better in at least one metric.
    - [ ] Design C Pareto dominates both A and B due to its optimal timing performance


10. In a Design Space Exploration graph, what does the "Pareto Frontier" represent?
    - [ ] The set of all synthesized design points that satisfy basic linear inequality constraints.
    - [ ] The set of optimal designs where one metric cannot be improved without sacrificing another.
    - [ ] The subset of design solutions that achieve the absolute minimum power consumption regardless of area.
    - [ ] The collection of designs that failed to meet timing closure during the logic synthesis phase.


## Answers:
1. B ( [Check out](https://www.youtube.com/watch?v=qIHQ_DOFZZY&list=PLUQpHm_JtukLuPA_xJiEZWreKTD9jwgJl&index=26) )
2. C ( [Check out](https://www.geeksforgeeks.org/digital-logic/sequential-binary-multiplier/#:~:text=Advantages%20of%20Sequential%20Binary%20Multiplier) )
3. 24
4. $T_{gen} + 3 \times T_{add}$ ( [Check out](https://www.youtube.com/watch?v=m9UNPyGbeyI) )
5. 8 ( [Check out](https://www.youtube.com/watch?v=m9UNPyGbeyI) )
6. B ( [Check out](https://www.youtube.com/watch?v=m9UNPyGbeyI) )
7. A, B, C ( A Program Counter is not a datapath component)
8. B
9. C
10. B
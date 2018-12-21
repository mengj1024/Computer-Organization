### step 1: delete extra ports and variables 

### step 2: make you code synthesizable

- [ ] delete hi-lo unit.
- [ ] sequential logic ~ `<=` or `always @([clk])`, combinatorial logic ~ `=` or `always @(*)`.
- [ ] delete initial, fork, join, casex, casez and system tasks(`$display`, `$signed`?).
- [ ] make sure all registers are resettable. 
- [ ] no assignment conflicts
- [ ] no latch.
- [ ] ...

### step 3:

### step 4: 
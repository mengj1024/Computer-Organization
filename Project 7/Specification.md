#### CP0:
- Status
- Cause
- EPC
- PrID

#### Interrupts: (asynchronous)
- I/O request
  
#### Exceptions: (synchronous)
- AdEL (Address Exception Load)
- AdES (Address Exception Store)
- RI (undefined instruction)
- Ov (Overflow)
  
### priority
Hold exception flags in pipeline until commit point (M stage). 
Exceptions in earlier pipe stages override later exceptions for a given instruction.
Inject external interrupts at commit point (override others).
If exception at commit: update Cause and EPC registers, kill all stages, inject handler PC into fetch stage.
  
#### AdEL
- `lw`, `lh`, `lhu`: address unaligned on boundary, like `lw $t1, 2(3)`
- `lw`, `lh`, `lhu`, `lb`, `lbu`: cross limit(base) address, like `lh $t2, 2(0x3000)`.
- `lh`, `lhu`, `lb`, `lbu`: perform on Timer.
- `jr`, `jalr`: PC isn't aligned on word boundary or in [0x3000, 0x4ffc].
- `lw`, `lh`, `lhu`, `lb`, `lbu`: arithemtic overflow at Execute stage.

#### AdES
- `sw`, `sh`, `sb`: address unaligned on boundary.
- `sw`, `sh`, `sb`: cross limit(base) address.
- `sw`, `sh`, `sb`: Trying to write Timer.CNT register.
- `sh`, `sb`: perform on Timer.
- `sw`, `sh`, `sb`: arithemtic overflow at Execute stage.

#### RI
- `xxx`: invalid opcode or funct.

#### Ov
- `add`, `addi`, `sub`: arithmetic overflow in ALU.
  

### Precise Exception
- pipelining "contradicts" sequential model of execution.
- In a *precise exception* CPU, on any exception we are pointed at one instruction (the exception victim).
- When re-executed after the exception, those instructions will behave exactly as they would have done if the exception hadn't happened. Any side effect must be idempotent, doing it twice is the same as doing it once.
- The software that handles exceptions can ignore all the timing effects of the CPU's implementation.
  
#### Ingredients
- Unambiguous proof of guilt: `Cause[BD]`
- Exceptions appear in instruction sequence: detect exceptions at MEM stage.
- Subsequent instructions nullified

## Q&A

- `jr`'s victim should be aligned by hardware(EPC aligned on word bundary).
- Exception(Interrupt) in the branch delay slot of `jal`, `jalr`  should **double write**.
- `sw` overrides state transition in Timer.
- `IRQ`-> 1 when `count` -> 0.
- LOAD -> CNT: `count` <= `preset`. 
- mode1, INT -> IDLE -> LOAD.
- `RI` exception only detects opcode and func.
- `Preset` > 0.
- victim: mult, divu, etc; roll back `HI` and `LO`.
- No exceptions in Handler program (software only **read** EXL).
- 2 versions of submission provided on class.
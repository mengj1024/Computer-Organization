# Computer-Organization
From logic gates to MIPS micro system.

## Project 0
- ALU
- CRC check digit
- Finite State Machine, 
- General-Purpose Registers in Logisim.

## Project 1
- ALU, GPR, Splitter, etc.
- **finite state machine** in Verilog.

## Project 2
- MIPS assembly language practice using MARS.
- require basic knowledge about data structure.

## Project 3
- single-cycle MIPS 32-bit CPU in Logisim.
- support instruction set {`addu`, `subu`, `ori`, `lw`, `sw`, `beq`, `lui`, `nop`}.
  
## Project 4
- single-cycle MIPS 32-bit CPU in Verilog.
- support instruction set {`addu`, `subu`, `ori`, `lw`, `sw`, `beq`, `lui`, `j`, `jal`, `jr`, `nop`}.

## Project 5
- 5-stage pipeline MIPS 32-bit CPU in Verilog.
- support instruction set {`addu`, `subu`, `ori`, `lw`, `sw`, `beq`, `lui`, `j`, `jal`, `jr`, `nop`}.

## Project 6
- 5-stage pipeline MIPS 32-bit CPU based on Project 5 in Verilog.
- support MIPS-C3 = {`LB`, `LBU`, `LH`, `LHU`, `LW`, `SB`, `SH`, `SW`, `ADD`, `ADDU`, `SUB`, `SUBU`, `MULT`, `MULTU`, `DIV`, `DIVU`, `SLL`, `SRL`, `SRA`, `SLLV`, `SRLV`, `SRAV`, `AND`, `OR`, `XOR`, `NOR`, `ADDI`, `ADDIU`, `ANDI`, `ORI`, `XORI`, `LUI`, `SLT`, `SLTI`, `SLTIU`, `SLTU`, `BEQ`, `BNE`, `BLEZ`, `BGTZ`, `BLTZ`, `BGEZ`, `J`, `JAL`, `JALR`, `JR`, `MFHI`, `MFLO`, `MTHI`, `MTLO`}.

## Project 7
- 32-bit MIPS micro system based on Project 6 in Verilog.
- Exception, Interrupt, Memory Mapped I/O.
- support MIPS-C4 = {`LB`, `LBU`, `LH`, `LHU`, `LW`, `SB`, `SH`, `SW`, `ADD`, `ADDU`, `SUB`, `SUBU`, `MULT`, `MULTU`, `DIV`, `DIVU`, `SLL`, `SRL`, `SRA`, `SLLV`, `SRLV`, `SRAV`, `AND`, `OR`, `XOR`, `NOR`, `ADDI`, `ADDIU`, `ANDI`, `ORI`, `XORI`, `LUI`, `SLT`, `SLTI`, `SLTIU`, `SLTU`, `BEQ`, `BNE`, `BLEZ`, `BGTZ`, `BLTZ`, `BGEZ`, `J`, `JAL`, `JALR`, `JR`, `MFHI`, `MFLO`, `MTHI`, `MTLO`, `ERET`, `MFC0`, `MTC0`}.

## Project 8
- **real stuff!**
- 32-bit MIPS micro system based on Project 7 in Verilog.
- Exception, Interrupt, Memory Mapped I/O.
- test on FPGA board
- support MIPS-C4 = {`LB`, `LBU`, `LH`, `LHU`, `LW`, `SB`, `SH`, `SW`, `ADD`, `ADDU`, `SUB`, `SUBU`, `MULT`, `MULTU`, `DIV`, `DIVU`, `SLL`, `SRL`, `SRA`, `SLLV`, `SRLV`, `SRAV`, `AND`, `OR`, `XOR`, `NOR`, `ADDI`, `ADDIU`, `ANDI`, `ORI`, `XORI`, `LUI`, `SLT`, `SLTI`, `SLTIU`, `SLTU`, `BEQ`, `BNE`, `BLEZ`, `BGTZ`, `BLTZ`, `BGEZ`, `J`, `JAL`, `JALR`, `JR`, `MFHI`, `MFLO`, `MTHI`, `MTLO`, `ERET`, `MFC0`, `MTC0`}.
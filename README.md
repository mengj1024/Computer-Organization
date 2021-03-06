# Computer-Organization
From logic gates to MIPS micro system.
## Problems
This repo include most of the on-class and off-class test problems recorded.

1 pre-exam and 9 Projects in total.

Here's an outline of each project.

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
- 32-bit single-cycle MIPS CPU in Logisim.
- support instruction set {`addu`, `subu`, `ori`, `lw`, `sw`, `beq`, `lui`, `nop`}.
  
## Project 4
- 32-bit single-cycle MIPS CPU in Verilog.
- support instruction set {`addu`, `subu`, `ori`, `lw`, `sw`, `beq`, `lui`, `j`, `jal`, `jr`, `nop`}.

## Project 5
- 32-bit 5-stage pipeline MIPS CPU in Verilog.
- support instruction set {`addu`, `subu`, `ori`, `lw`, `sw`, `beq`, `lui`, `j`, `jal`, `jr`, `nop`}.

## Project 6
- 32-bit 5-stage pipeline MIPS CPU based on Project 5 in Verilog.
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
- support MIPS-C5 = {`LB`, `LBU`, `LH`, `LHU`, `LW`, `SB`, `SH`, `SW`, `ADD`, `ADDU`, `SUB`, `SUBU`, `SLL`, `SRL`, `SRA`, `SLLV`, `SRLV`, `SRAV`, `AND`, `OR`, `XOR`, `NOR`, `ADDI`, `ADDIU`, `ANDI`, `ORI`, `XORI`, `LUI`, `SLT`, `SLTI`, `SLTIU`, `SLTU`, `BEQ`, `BNE`, `BLEZ`, `BGTZ`, `BLTZ`, `BGEZ`, `J`, `JAL`, `JALR`, `JR`, `ERET`, `MFC0`, `MTC0`}. **(No hi-lo relevant instructions)**

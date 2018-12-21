## 32-bit MIPS 5-stage pipelining microsystem
- support MIPS-C5 = {`LB`, `LBU`, `LH`, `LHU`, `LW`, `SB`, `SH`, `SW`, `ADD`, `ADDU`, `SUB`, `SUBU`, `SLL`, `SRL`, `SRA`, `SLLV`, `SRLV`, `SRAV`, `AND`, `OR`, `XOR`, `NOR`, `ADDI`, `ADDIU`, `ANDI`, `ORI`, `XORI`, `LUI`, `SLT`, `SLTI`, `SLTIU`, `SLTU`, `BEQ`, `BNE`, `BLEZ`, `BGTZ`, `BLTZ`, `BGEZ`, `J`, `JAL`, `JALR`, `JR`, `ERET`, `MFC0`, `MTC0`}. **(No hi-lo relevant instructions)**
- IM: 8KB IP core
- DM: 8KB IP core
- CLOCK: IP core
- bridge
- timer
- 9-bit 8-seg display
- 64-bit switch
- 8-bit button
- 32-bit LED
- UART
  - 我们会提供大部分代码，但你需要对其进行补全，并使之符合你的设计
  - 注：UART 的接口规范与前个 project 的 bridge 的接口规范不同。你或者调整 UART 接口规范使之符合前个 bridge，或者修改 bridge 使之匹配 UART端口设置及功能符合PIN定义文件。

### Memory Mapping
| Address | Device |
| :-: | :-: |
| 0x7f00~0x7f0b | Timer |
| 0x7f10~0x7f2b | MiniUART |
| 0x7f2c~0x7f33 | 64-bit Switch |
| 0x7f34~0x7f37 | 32-bit LED |
| 0x7f38~0x7f3f | SSD |
| 0x7f40~0x7f43 | 8-bit Button |
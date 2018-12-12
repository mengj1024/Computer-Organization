# 2018.12.6

## bgtz
(Branch on Greater Than Zero)

| opcode | rs | 000000 | offset | 
| :-: | :-: | :-: | :-: |

**Format:** `bgtz rs, offset`

**Operation:**
```verilog
if (GPR[rs] > 0)
    PC = PC + 4 + sign_extend(offset||00)
```

#### Solution by Demard
> Compare GPR[rs] with 0 in ALU, produce a signal `gtz` represents Greater Than Zero, and connect it to **npc** or **IFU** module, then do the same thing as `beq` inside.

#### Potential Bugs
  - waiting for you to fill this one..


## srlv
(Shift Right Logical Variable)

| opcode | rs | rt | rd | - | funct | 
| :-: | :-: | :-: | :-: | :-: | :-: |

**Format:** `srlv rd, rs, rt`

**Operation:**
```verilog
sa <- GPR[rs][4:0]
GPR[rd] = {sa{0}, GPR[rt][31:sa]}
```

#### Solution by Demard
> I'd like to add a `shamt` port to ALU, and ask **ctrl** module for a `ShamtSrc` to distinguish shift variable type and shift *sa* field type instructions.

#### Potential Bugs
  - waiting for you to fill this one..

## lbu
(Load Byte Unsigned)

| opcode | base | rt | offset | 
| :-: | :-: | :-: | :-: |

**Format:** `lbu rt, offset(base)`

**Operation:**
```verilog
addr <- GPR[base] + sign_extend(offset)
GPR[rt] = {24{0}, Memory[addr][7:0]}
```

#### Solution by Demard
> Load the word which the desired byte was in from data memory, select it on the way to RegFile by `addr[1:0]`.

#### Potential Bugs
  - waiting for you to fill this one..
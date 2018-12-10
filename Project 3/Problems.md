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
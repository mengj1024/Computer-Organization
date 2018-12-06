# 2018.11.22

## bnez
(Branch on Not Equal to Zero)

| opcode | rs | 000000 | offset | 
| :-: | :-: | :-: | :-: |

**Format:** `bnez rs, offset`

**Operation:**
```erl
if (GPR[rs] != 0)
    PC = PC + 4 + sign_extend(offset||00)
```

## msbv
(Move special byte variable ?)

| opcode | rs | rt | rd | - | funct | 
| :-: | :-: | :-: | :-: | :-: | :-: |

**Format:** `msbv rd, rs, rt`

**Operation:**
```erl
start <- GPR[rs]4..0
count <- GPR[rs]9..5
if (start + count – 1 <= 31) then
	temp <- GPR[rt]start+count-1..start
else if (start + count – 1 > 31)  then
	temp <- GPR[rt]start+count-33..0|| GPR[rt]31..start
endif
GPR[rd] <- sign_ext(temp)
```

## lbu
(Load Byte Unsigned)

| opcode | base | rt | offset | 
| :-: | :-: | :-: | :-: |

**Format:** `lbu rt, offset(base)`

**Operation:**
```erl
addr <- GPR[base] + sign_extend(offset)
GPR[rt] = {24{0}, Memory[addr][7:0]}
```

# 2018.11.29

## bptal
(Branch on Power of Two And Link)

| opcode | rs | 000000 | offset | 
| :-: | :-: | :-: | :-: |

**Format:** `bptal rs, offset`

**Operation:**
```erl
if (GPR[rs] is power of 2)
    GPR[31] <- PC + 4
    PC <- sign_extend(offset || 00)
else
    PC <- PC + 4
```

## rotrv
(Rotate Word Right Variable)

| opcode | rs | rt | rd | - | funct | 
| :-: | :-: | :-: | :-: | :-: | :-: |

**Format:** `rotr rd, rt, rd`

**Operation:**
```erl
sa <- GPR[rs][4:0]
GPR[rd] <- GPR[rt][sa-1:0] || GPR[rt][31:sa]
```

## lhs
(Load Halfword Special)

| opcode | base | rt | offset | 
| :-: | :-: | :-: | :-: |

**Format:** `shs rt, offset(base)`

**Operation:**
```erl
addr <- GPR[base] + sign_extend(offset)
Memword0 <- Memory[addr]
Memword1 <- Memory[addr-4] // ? I forgot it...
if (addr == 3)


```

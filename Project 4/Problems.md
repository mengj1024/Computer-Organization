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

#### Solution by Demard
> No difference from `beq` other than Not Equal to Zero.

#### Potential Bugs
  None

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
GPR[rt] <- {24{0}, Memory[addr][7:0]}
```

#### Solution by Demard
> Load the word out of data memory first, then select the byte correspondingly by `addr[1:0]`
> zero extend the byte and connect it to the Write Back MUX.

#### Potential Bugs
  None

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

#### Solution by Demard
> To see if it's power of 2, you can mod 2, find the only one 1 bit, etc.

#### Potential Bugs
- If the condi is not true, NO link(PC + 4 shouldn't be assigned to `GPR[31]`)!
- `GPR[rs]` is interpreted as **signed number**.

## rotrv
(Rotate Word Right Variable)

| opcode | rs | rt | rd | - | funct | 
| :-: | :-: | :-: | :-: | :-: | :-: |

**Format:** `rotr rd, rt, rs`

**Operation:**
```erl
sa <- GPR[rs][4:0]
GPR[rd] <- GPR[rt][sa-1:0] || GPR[rt][31:sa]
```

#### Solution by Demard
> {GPR[rt], GPR[rt]} >> GPR[rs][4:0]
> Jackpot!
> Another solution is to assign each bit to alu.res by a loop.

#### Potential Bugs
  None

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
    GPR[rt] <- Memword0 blabla..
else 
    blabla
```

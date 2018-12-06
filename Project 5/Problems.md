# 2018.12.6

## blezalr
(Branch on Less than or Equal to Zero And Link Register)

| opcode | rs | rt | rd | - | funct | 
| :-: | :-: | :-: | :-: | :-: | :-: |

**Format:** `blezalr rd, rs, rt`

**Operation:**
```erl
I:
condi <- GPR[rs] <= 0
GPR[rd] <- PC + 8

I+1:
if (condi) then
    PC <- GPR[rt]
endif
```

## rotr
(Rotate Word Right)

| opcode | rs | rt | - | sa | funct | 
| :-: | :-: | :-: | :-: | :-: | :-: |

**Format:** `rotr rd, rt, sa`

**Operation:**
```erl
GPR[rd] <- GPR[rt][sa-1:0] || GPR[rt][31:sa]
```

## lhs
(Load Halfword Special)

| opcode | base | rt | offset | 
| :-: | :-: | :-: | :-: |

**Format:** `lhs rt, offset(base)`

**Operation:**
```erl
addr <- GPR[base] + sign_extend(offset)
NewAddr <- {addr[31:2], 00}
Memword <- Memory[NewAddr]
if (addr[1:0] == 2)
    GPR[rt] <- sign_ext(Memword[15:0])
else if (addr[1:0] == 0)
    GPR[rt] <- sign_ext(Memword[31:16])
endif
```

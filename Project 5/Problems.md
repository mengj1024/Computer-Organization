# 2018.12.6

## blezalr
(Branch on Less than or Equal to Zero And Link Register)

| opcode | rs | rt | rd | - | funct | 
| :-: | :-: | :-: | :-: | :-: | :-: |

**Format:** `blezalr rd, rs, rt`

**Operation:**
```verilog
I:
condi <- GPR[rs] <= 0
GPR[rd] <- PC + 8

I+1:
if (condi) then
    PC <- GPR[rt]
endif
```
#### Solution by Demard
> Classic mixed instruction of `blez` and `jalr`!
> The `condi` signal is needed where PC is updated and **no where else**. So the easy way is to produce `condi` using `GPR[rs]`, and connect it to npc module or IF stage to update PC conditionally. 
> Note that the `Tuse` of both `rs` and `rt` are **0**.

#### Potential Bugs
  - `blezalr`'s *link* part is slightly different from `bgezal`, `GPR[rd] <- PC + 8` always gets executed no matter the `condi` is asserted or not.


## rotr
(Rotate Word Right)

| opcode | rs | rt | - | sa | funct | 
| :-: | :-: | :-: | :-: | :-: | :-: |

**Format:** `rotr rd, rt, sa`

**Operation:**
```verilog
GPR[rd] <- GPR[rt][sa-1:0] || GPR[rt][31:sa]
```

#### Solution by Demard
> Jackpot!
> `{GPR[rt], GPR[rt]} >> sa`
> Another solution is to assign each bit to alu.res by a loop.

#### Potential Bugs
  None


## lhs
(Load Halfword Special)

| opcode | base | rt | offset | 
| :-: | :-: | :-: | :-: |

**Format:** `lhs rt, offset(base)`

**Operation:**
```verilog
addr <- GPR[base] + sign_extend(offset)
NewAddr <- {addr[31:2], 00}
Memword <- Memory[NewAddr]
if (addr[1:0] == 2)
    GPR[rt] <- sign_ext(Memword[15:0])
else if (addr[1:0] == 0)
    GPR[rt] <- sign_ext(Memword[31:16])
endif
```

#### Solution by Demard
> seems pretty common, read a word just like `lw`, load conditionally, and make sure the `RegWrite` is also conditional.
> Jackpot...huh? but I didn't pass the penultimate case...wysl
> The report message shows that I was writing the right register at the right time(PC) but the wrong value, 0xffff4371 particularly which expected 0xffffa406. I'd checked sign extension part a million times...It must have gone wrong AFTER the sign extension part, the WB stage specifically, or it didn't go sign extension part at all.
> jeeeeeeeh, disgusting...

#### Potential Bugs
  - I didn't find it. :| 
  - waiting for you to fill this one..


# 2018.11.29

## blezals
(Branch on Less than or Equal to Zero And Link Special)
| opcode | rs | - | offset | 
| :-: | :-: | :-: | :-: |

**Format:** `blezals rs, offset`

**Operation:**
```verilog
I:
condi <- GPR[rs] <= 0
GPR[rd] <- PC + 8

I+1:
if (condi) then
    PC <- PC + sign_extend(offset||00)
endif
```

## rev
(Reverse)

| opcode | rs | rt | - | - | funct | 
| :-: | :-: | :-: | :-: | :-: | :-: |

**Format:** `rev rt, rs`

**Operation:**
```verilog
GPR[rt] <- {GPR[rs][0], GPR[rs][1], ..., GPR[rs][31]}
```

#### Solution by Demard
> perform this instruction mainly in ALU.
> for i in [0, 31], `GPR[rt][i] = GPR[rs][31-i]`

#### Potential Bugs
  None

## shs
(Store Halfword Special)

| opcode | base | rt | offset | 
| :-: | :-: | :-: | :-: |

**Format:** `shs rt, offset(base)`

**Operation:**
```verilog
addr <- GPR[base] + sign_extend(offset)

```
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

## msub
(Multiply and Subtract Word to Hi, Lo)

| opcode | rs | rt | - | - | funct |
| :-: | :-: | :-: | :-: | :-: | :-: |
| 011100 | rs | rt | 00000 | 00000 | 000100 |

**Format:** `msub rs, rt`

**Operation:**
```verilog
(HI,LO) <- (HI,LO) - (GPR[rs] x GPR[rt])
```
#### Solution by Demard
> similar instrcutions like `madd`, `mul`, etc can be performed without changing the datapath.
> Don't know if it's permissible that changing in md_unit directly...
> Note that the `Tuse` of both `rs` and `rt` are the same as cal_r type.
#### Potential Bugs
  - waiting for you to fill this one..

## lhs
(Load Halfword Special)

| opcode | base | rt | offset |
| :-: | :-: | :-: | :-: |

**Format:** `lhs rt, offset(base)`

**Operation:**
```verilog
addr <- GPR[base] + sign_extend(offset)
NewAddr <- addr[31:2] || 00
Memword <- Memory[NewAddr]
if (addr[1:0] == 2)
    GPR[rt] <- sign_ext(Memword[15:0])
else if (addr[1:0] == 0)
    GPR[rt] <- sign_ext(Memword[31:16])
endif
```
#### Solution by Demard
> same as Project 5.lhs

#### Potential Bugs
  - waiting for you to fill this one..
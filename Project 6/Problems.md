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
#### Solution by Demard
> Classic mixed instruction of `blez` and `jalr`!
> The `condi` signal is needed where PC is updated and **no where else**. So the easy way is to produce `condi` using `GPR[rs]` from each pipeline register, and connect it to npc module or IF stage to update PC conditionally. 
> Note that the `Tuse` of both `rs` and `rt` are **0**.
##### Potential Bugs
  - `blezalr`'s *link* part is slightly different from `bgezal`, GPR[rd] <- PC + 8 always gets executed no matter the `condi` is true or not.

## msub
(Multiply and Subtract Word to Hi, Lo)

| opcode | rs | rt | - | - | funct |
| :-: | :-: | :-: | :-: | :-: | :-: |
| 011100 | rs | rt | 00000 | 00000 | 000100 |

**Format:** `msub rt, rt`

**Operation:**
```erl
(HI,LO) <- (HI,LO) - (GPR[rs] x GPR[rt])
```
#### Solution by Demard
> similar instrcutions like `madd`, `mul`, etc can be performed without changing the datapath.
> Don't know if it's permissible that changing in md_unit directly...
> Note that the `Tuse` of both `rs` and `rt` are the same as cal_r type.
##### Potential Bugs
  - waiting for you to fill this one..

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
#### Solution by Demard
> seems pretty common, read a word just like `lw`, load conditionally, and make sure the `RegWrite` is also conditional.
> Jackpot...huh? but I didn't pass the penultimate case...wysl
> The report message shows that I was writing the right register at the right time(PC) but the wrong value, 0xffff4371 particularly which expected 0xffffa406. I'd checked sign extension part a million times...It must have gone wrong AFTER the sign extension part, the WB stage specifically, or it didn't go sign extension part at all.
> jeeeeeeeh 恶心死我了

##### Potential Bugs
  - I didn't find it. :| 
  - waiting for you to fill this one..
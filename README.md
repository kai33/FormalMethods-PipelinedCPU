# Pipelined Microcontroller
Use formal methods to verify the hazards have been correctly handled in the 5-stage pipelined microcontroller.

## Instruction Set

**NOOP**
* Performs no operation.
* Do nothing for all stages.
* op: (none)
* syntax: noop
* encode: 10 00 00 00

**ADD**
* Adds two registers and stores the result in a register.
* Ignore the MEM stage.
* op: $d = $s + $t
* syntax: add $d, $s, $t
* encode: 11 dd ss tt

**SUB**
* Subtracts two registers and stores the result in a register.
* Ignore the MEM stage.
* op: $d = $s - $t
* syntax: sub $d, $s, $t
* encode: 12 dd ss tt

**MULT**
* Multiplies register $s by register $t and stores the result in register $d.
* Ignore the MEM stage.
* op: $d = $s * $t
* syntax: mult $d, $s, $t
* encode: 13 dd ss tt

**DIV**
* Divides register $s by register $t and stores the quotient in register $d.
* Ignore the MEM stage.
* op: $d = $s / $t
* syntax: div $d, $s, $t
* encode: 14 dd ss tt

**BEQ**
* Branches if the two registers are equal.
* Ignore the EXE, MEM, WB stages.
* op: if $s == $t goto line #d
* syntax: beq #d, $s, $t
* encode: 15 dd ss tt

**BNE**
* Branches if the two registers are not equal.
* Ignore the EXE, MEM, WB stage.
* op: if $s != $t goto line #d
* syntax: beq #d, $s, $t
* encode: 16 dd ss tt

**JUMP**
* Jumps to the line.
* Ignore the EXE, MEM, WB stage.
* op: goto line #d
* syntax: j #d
* encode: 17 dd 00 00

**MOVE**
* Move immediate value into a register.
* Ignore the MEM stage.
* op: $d = #s
* syntax: move $d, #s
* encode: 18 dd ss 00

**LOAD**
* Load value into a register from the specified address in memory.
* Ignore the EXE stage.
* op: $d = memory[#s]
* syntax: load $d, #s
* encode: 19 dd ss 00

**SAVE**
* Save value into a memory address from the specified register.
* Ignore the EXE, WB stage.
* op: memory[#d] = $s
* syntax: save #d, $s
* encode: 20 dd ss 00

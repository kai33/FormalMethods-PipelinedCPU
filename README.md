# Formal Methods - Pipelined Microcontroller
use formal methods to verify the hazards have been correctly handled in the 5-stage pipelined microcontroller.

## Instruction Set

**NOOP**
* Performs no operation.
* Do nothing for all stages.
* op: (none)
* syntax: noop
* encode: 00 000 000 000

**ADD**
* Adds two registers and stores the result in a register.
* Ignore the MEM stage.
* op: $d = $s + $t
* syntax: add $d, $s, $t
* encode: 01 ddd sss ttt

**SUB**
* Subtracts two registers and stores the result in a register.
* Ignore the MEM stage.
* op: $d = $s - $t
* syntax: sub $d, $s, $t
* encode: 02 ddd sss ttt

**MULT**
* Multiplies register $s by register $t and stores the result in register $d.
* Ignore the MEM stage.
* op: $d = $s * $t
* syntax: multu $d, $s, $t
* encode: 03 ddd sss ttt

**DIV**
* Divides register $s by register $t and stores the quotient in register $d.
* Ignore the MEM stage.
* op: $d = $s / $t
* syntax: div $d, $s, $t
* encode: 04 ddd sss ttt

**BEQ**
* Branches if the two registers are equal.
* Ignore the EXE, MEM, WB stages.
* op: if $s == $t goto line #d
* syntax: beq #d, $s, $t
* encode: 05 ddd sss ttt

**BNE**
* Branches if the two registers are not equal.
* Ignore the EXE, MEM, WB stage.
* op: if $s != $t goto line #d
* syntax: beq #d, $s, $t
* encode: 06 ddd sss ttt

**JUMP**
* Jumps to the line.
* Ignore the EXE, MEM, WB stage.
* op: goto line #d
* syntax: j #d
* encode: 07 ddd 000 000

**MOVE**
* Move immediate value into a register.
* Ignore the MEM stage.
* op: $d = #s
* syntax: move $d, #s
* encode: 08 ddd sss 000

**LOAD**
* Load value into a register from the specified address in memory.
* Ignore the EXE stage.
* op: $d = memory[#s]
* syntax: load $d, #s
* encode: 09 ddd sss 000

**SAVE**
* Save value into a memory address from the specified register.
* Ignore the WB stage.
* op: memory[#d] = $s
* syntax: save #d, $s
* encode: 10 ddd sss 000

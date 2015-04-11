COMPASS-1: "Computer Onboard Mathematical Processing and Storage System"
========================================================================

Note: WIP

Introduction
============
COMPASS-1 is a 8-bit RISC processor architecture with 16-bit addressing.

User-visible Registers
======================
All registers are 8 bits wide except the program counter, which is 16 bits wide.

A0-A7: address registers
 - Address registers are 8 bits, but consecutive pairs (including A7:A0) may be
   treated as 16-bit. A 16-bit address is referred to by the register from which
   the high 8 bits are taken. The low 8 bits are taken from the next register.
D0-D7: data registers

There is no fixed stack pointer, any of the address registers may be used as a
stack pointer.

The program counter is 16 bits wide and referred to as 'PC'.
 - The high and low halfs are called P and C, respectively.

Assembly Language
=================
Destination comes AFTER the operands.
Immediate values are denoted with a $.
Address registers are prefixed with a lowercase 'a' when treated as 8-bit.
Address registers are prefixed with an uppercase 'A' when used as 16-bit.
Data registers are prefixed with a lowercase 'd'.

Instruction Set
===============
All instructions are 16 bits wide.

=================================================================================
|        Opcode        |     Mnemonic    |         Operation Performed          |
|===============================================================================|
| 0000 000 ddd bbb ooo | LD [AB+dO], dD  | Loads from memory to data register   |
| 0000 001 ddd bbb ooo | LD dD, [AB+dO]  | Stores from data register to memory  |
| 0000 010 000 aaa ddd | LD aA, dD       | Copies address to data register      |
| 0000 011 001 ddd aaa | LD dD, aA       | Copies data to address register      |
|===============================================================================|
| 0000 1aa aii iii iii | LD $imm, aA     | Loads immediate to address register  |
| 0001 0dd dii iii iii | LD $imm, dD     | Loads immediate to data register     |
|===============================================================================|
| 0010 000 aaa bbb ddd | ADD dA, dB, dD  | dA + dB -> dD                        |
| 0010 001 aaa bbb ddd | SUB dA, dB, dD  | dA - dB -> dD                        |
|===============================================================================|
| 0011 000 aaa bbb ddd | OR dA, dB, dD   | dA OR dB -> dD                       |
| 0011 001 aaa bbb ddd | AND dA, dB, dD  | dA AND dB -> dD                      |
| 0011 010 aaa bbb ddd | XOR dA, dB, dD  | dA XOR dB -> dD                      |
| 0011 011 aaa bbb ddd | NAND dA, dB, dD | dA NAND dB -> dD                     |
| 0011 100 aaa bbb ddd | XNOR dA, dB, dD | dA XNOR dB -> dD                     |
| 0011 101 000 aaa ddd | NOT dA, dD      | NOT dA -> dD                         |
|===============================================================================|
| 0011 110 aaa bbb ddd | LSH dA, dB, dD  | dA << dB -> dD                       |
| 0011 111 aaa bbb ddd | RSH dA, dB, dD  | dA >> dB -> dD                       |
|===============================================================================|
| 0100 000 000 000 aaa | JMP AA          | AA -> PC                             |
| 0100 001 aaa bbb ddd | JB dA, dB, AD   | if dA is below dB then AD->PC        |
| 0100 010 aaa bbb ddd | JE dA, dB, AD   | if dA equals dB then AD->PC          |
|===============================================================================|
| 0100 011 000 aaa ppp | CALL AA, AP     | Pushes C then P on AP; AA -> PC      |
| 0100 011 001 000 ppp | RET AP          | (AP) -> PC; AP + 2 -> AP             |
|===============================================================================|
| 0101 000 000 ppp aaa | PUSH aA, AP     | AP - 1 -> AP; aA -> (AP)             |
| 0101 000 001 ppp aaa | PUSH dA, AP     | AP - 1 -> AP; dA -> (AP)             |
| 0101 000 010 ppp aaa | POP AP, aA      | (AP) -> aA; AP + 1 -> AP             |
| 0101 000 011 ppp aaa | POP AP, dA      | (AP) -> dA; AP + 1 -> AP             |
|===============================================================================|
| 1111 000 000 ddd ppp | OUTB dD, aP     | Outputs dD to port aP                |
| 1111 000 001 ppp ddd | INB  dD, aP     | Reads from port aP to dD             |
=================================================================================
| 1111 111 111 111 111 | NOP             | No operation                         |
=================================================================================

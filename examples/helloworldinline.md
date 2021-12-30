# Hello World Inline!

Print `HELLO WORLD!` after running `SYS 49152`. A clever way of manipulating the return address on the stack to have data stored along with the code that uses it.

Adapted from *Assembler Routines for the 6502* by David Barrow (ISBN: 9780712605076), page 73.

## Code

    10 pointer=$fb
    20 chrout=$ffd2
    30 !
    100 *=$c000
    110 jsr output
    120 txt "hello "
    130 byt 0
    140 jsr output
    150 txt "world!"
    160 byt 0
    170 rts
    180 !
    1000 output pla
    1010 sta pointer
    1020 pla
    1030 sta pointer+1
    1040 ldy #0
    1050 loop inc pointer
    1060 bne skip
    1070 inc pointer+1
    1080 skip lda (pointer),y
    1090 beq finish
    1100 jsr chrout
    1110 jmp loop
    1120 finish lda pointer+1
    1130 pha
    1140 lda pointer
    1150 pha
    1160 rts

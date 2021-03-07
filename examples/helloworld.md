# Hello World!

Print `HELLO WORLD!` after running `SYS 828`.

## Code

    100 *=$033c
    110 ldx #$00
    120 loop lda msg,x
    130 jsr $ffd2
    140 inx
    150 cpx #$0c
    160 bne loop
    170 rts
    180 msg txt "hello world!"


## Modification

Add an `END` label to mark the end of the message and calculate the message size during assembly. Then change the message to display whatever you want.

    ...
    150 cpx #end-msg
    ...
    190 end=*


## Alternative version

Print all bytes from the `MSG` address until it encounters a zero byte.

    100 *=$033c
    110 ldx #$0
    120 loop lda msg,x
    130 beq stop
    140 jsr $ffd2
    150 inx
    160 jmp loop
    170 stop rts
    180 msg txt "hello other world!",$0

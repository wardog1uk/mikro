


# Hello World!

Print `HELLO WORLD!` after running `SYS 828`.

## Code

    100 *=$033C
    110 LDX #$00
    120 LOOP LDA MSG,X
    130 JSR $FFD2
    140 INX
    150 CPX #$0C
    160 BNE LOOP
    170 RTS
    180 MSG TXT "HELLO WORLD!"


## Modification

Add an `END` label to mark the end of the message and calculate the message size during assembly.

    ...
    150 CPX #END-MSG
    ...
    190 END=*


## Alternative version

Print all bytes from the `MSG` address until it encounters a #$00 (the `BRK` instruction).

    100 *=$033C
    110 LDX #$0
    120 LOOP LDA MSG,X
    130 BEQ STOP
    140 JSR $FFD2
    150 INX
    160 JMP LOOP
    170 STOP RTS
    180 MSG TXT "HELLO ALTERNATIVE WORLD!"
    190 BRK

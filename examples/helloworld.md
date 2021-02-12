# Hello World!

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

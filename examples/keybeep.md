# Key Beep

After running `SYS 828` this will beep on every key press. Return to normal by running `SYS 911`.

## Code

    10 ! SYS 828
    100 *=$033C
    110 !
    120 ! REDIRECT KEY PRESS TO HANDLER
    130 LDA #<HANDLER
    140 STA $028F
    150 LDA #>HANDLER
    160 STA $0290
    170 RTS
    180 !
    200 ! HANDLE KEY PRESS
    210 HANDLER PHA
    220 JSR BEEP
    230 PLA
    240 JMP $EB48
    250 !
    300 ! START SOUND
    310 BEEP LDA #15
    320 STA 54296
    330 LDA #0
    340 STA 54277
    350 LDA #248
    360 STA 54278
    370 LDA #17
    380 STA 54273
    390 LDA #37
    400 STA 54272
    410 LDA #17
    420 STA 54276
    430 !
    500 ! WAIT
    510 LDA #100
    520 STA 251
    530 LOOP1 STA 252
    540 LOOP2 DEC 252
    550 BNE LOOP2
    560 DEC 251
    570 BNE LOOP1
    580 !
    600 ! STOP SOUND
    610 LDA #16
    620 STA 54276
    630 LDA #0
    640 STA 54277
    650 STA 54278
    660 JMP $EB48
    670 !
    700 ! RESET = SYS 911
    710 *=$038F
    720 LDA #$48
    730 STA $028F
    740 LDA #$EB
    750 STA $0290
    760 RTS


## Credits

The original Mikro assembler code is from the book *Introducing Commodore 64 Machine Code* by *Ian Sinclair*. This version is slightly refactored and commented for clarity.

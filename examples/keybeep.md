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
    330 LDA #190
    340 STA 54273
    350 LDA #248
    360 STA 54278
    370 LDA #17
    380 STA 54273
    390 LDA #37
    400 STA 54272
    410 LDA #17
    420 STA 54276
    430 !
    440 ! WAIT
    450 LDA #100
    460 STA 251
    470 LOOP1 STA 252
    480 LOOP2 DEC 252
    490 BNE LOOP2
    500 DEC 251
    510 BNE LOOP1
    520 !
    530 ! STOP SOUND
    540 LDA #0
    550 STA 54276
    560 STA 54277
    570 STA 54278
    580 JMP $EB48
    590 !
    600 ! RESET = SYS 911
    610 *=$038F
    620 LDA #$48
    630 STA $028F
    640 LDA #$EB
    650 STA $0290
    660 RTS


## Credits

The original Mikro assembler code is from the book *Introducing Commodore 64 Machine Code* by *Ian Sinclair*. This version is slightly refactored and commented for clarity.

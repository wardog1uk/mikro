# Key Beep

After running `SYS 828` this will beep on every key press. Return to normal by running `SYS 911`.


## Credits

The original Mikro assembler code is from the book *Introducing Commodore 64 Machine Code* by *Ian Sinclair*. This version is slightly refactored and commented for clarity, plus some corrections were made to the SID settings.


## Code

    10 ! sys 828
    100 *=$033c
    110 !
    120 ! redirect key press to handler
    130 lda #<handler
    140 sta $028f
    150 lda #>handler
    160 sta $0290
    170 rts
    180 !
    200 ! handle key press
    210 handler pha
    220 jsr beep
    230 pla
    240 jmp $eb48
    250 !
    300 ! start sound
    310 beep lda #15
    320 sta 54296
    330 lda #0
    340 sta 54277
    350 lda #248
    360 sta 54278
    370 lda #17
    380 sta 54273
    390 lda #37
    400 sta 54272
    410 lda #17
    420 sta 54276
    430 !
    500 ! wait
    510 lda #100
    520 sta 251
    530 loop1 sta 252
    540 loop2 dec 252
    550 bne loop2
    560 dec 251
    570 bne loop1
    580 !
    600 ! stop sound
    610 lda #16
    620 sta 54276
    630 lda #0
    640 sta 54277
    650 sta 54278
    660 rts
    670 !
    700 ! reset = sys 911
    710 *=$038f
    720 lda #$48
    730 sta $028f
    740 lda #$eb
    750 sta $0290
    760 rts

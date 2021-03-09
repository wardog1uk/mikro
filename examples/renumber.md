# Renumber

Renumber code from 10 in increments of 10. Load in memory, then load or type in the other code and run `sys 50176`.


## Credits

Mikro code taken directly from *Advanced machine code programming for the Commodore 64* by *A.P. and D.J. Stephenson* page 69.


## Code

    10 ! fixed renumber routine
    20 ! for mikro 64 assembler
    30 ! start line 10 increment 10
    40 link=$fb
    50 line=$fd
    60 *=$c400
    70 lda #10
    80 sta line
    90 lda #0
    100 sta line+1
    110 lda $2b
    120 sta link
    130 lda $2c
    140 sta link+1
    150 loop ldy #0
    160 lda (link),y
    170 pha
    180 iny
    190 lda (link),y
    200 tax
    210 lda line
    220 iny
    230 sta (link),y
    240 lda line+1
    250 iny
    260 sta (link),y
    270 clc
    280 lda line
    290 adc #10
    300 sta line
    310 bcc skip
    320 inc line+1
    330 skip stx link+1
    340 pla
    350 sta link
    360 bne loop
    370 txa
    380 bne loop
    390 rts
    400 end

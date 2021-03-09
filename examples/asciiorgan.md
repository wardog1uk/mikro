# ASCII Organ

Start with `sys 49152`. Press a key to play a note and press F1 to exit.

|1|2|3|4|5|6|7|8|9|0|+|-|
|--|--|--|--|--|--|--|--|--|--|--|--|
|C|C#|D|D#|E|F|F#|G|G#|A|A#|B


## Credits

Taken from *The Visible Computer: 6502* by *Charles Anderson* and formatted for the Mikro assembler.
Code is copyright *Jim Blackshear* and *Brian Bouldin*.


## Code

    10 *=$c000
    19 !
    20 note=$fc
    30 bgcolor=$d021
    40 sid=$d400
    50 volume=$d418
    60 settim=$ffdb
    70 rdtim=$ffde
    80 getin=$ffe4
    99 !
    100 jsr initscrn
    110 jsr initsid
    120 top jsr getin
    130 cmp #$00
    140 beq top
    150 cmp #$85
    160 beq quit
    170 jsr chkkey
    180 lda note
    190 beq top
    200 jsr beep
    210 jmp top
    220 quit rts
    299 !
    300 initscrn lda #$00
    310 sta bgcolor
    320 lda #$04
    330 ldx #$d8
    340 ldy #$00
    350 sty $fb
    360 sta $fc
    370 sty $fd
    380 stx $fe
    390 ldx #$04
    400 loop1 lda #$00
    410 sta ($fd),y
    420 lda #$a0
    430 sta ($fb),y
    440 iny
    450 bne loop1
    460 inc $fc
    470 inc $fe
    480 dex
    490 bne loop1
    500 rts
    599 !
    600 initsid lda #$00
    610 ldx #$1c
    620 loop2 sta sid,x
    630 dex
    640 bne loop2
    650 lda #$20
    660 sta sid+4
    670 lda #$f0
    680 sta sid+6
    690 lda #$0f
    700 sta volume
    710 rts
    799 !
    800 chkkey ldx #$00
    810 stx note
    820 cmp #$2d
    830 bne plus
    840 lda #$0c
    850 sta note
    860 rts
    870 plus cmp #$2b
    880 bne zero
    890 lda #$0b
    900 sta note
    910 rts
    920 zero cmp #$30
    930 bne cnvt
    940 lda #$0a
    950 sta note
    960 rts
    970 cnvt sec
    980 sbc #$30
    990 cmp #$0a
    1000 bcs exit
    1010 sta note
    1020 exit rts
    1199 !
    1200 beep ldx note
    1210 lda pitchl,x
    1220 ldy pitchh,x
    1230 sta sid
    1240 sty sid+1
    1250 ldy #$21
    1260 sty sid+4
    1270 jsr dbar
    1280 ldy #$00
    1290 sty sid+4
    1300 rts
    1999 !
    2000 dbar lda #$00
    2010 tax
    2020 tay
    2030 jsr settim
    2040 ldx note
    2050 lda bsl,x
    2060 ldy bsh,x
    2070 sta $fd
    2080 sty $fe
    2090 txa
    2100 jsr bar
    2110 wait jsr rdtim
    2120 cmp #$1e
    2130 bne wait
    2140 lda #$00
    2150 jmp bar
    2160 bar ldy #$00
    2170 bar1 sta ($fd),y
    2180 iny
    2190 cpy #$50
    2200 bne bar1
    2210 rts
    2999 !
    3000 pitchl byt $00,$61,$e1,$68,$f7,$8f,$30,$da
    3010 byt $8f,$4e,$18,$ef,$d2,$00,$00,$00
    3020 pitchh byt $00,$08,$08,$09,$09,$0a,$0b,$0b
    3030 byt $0c,$0d,$0e,$0e,$0f,$00,$00,$00
    3040 bsl byt $00,$70,$20,$d0,$80,$30,$e0,$90
    3050 byt $40,$f0,$a0,$50,$00,$00,$00,$00
    3060 bsh byt $00,$db,$db,$da,$da,$da,$d9,$d9
    3070 byt $d9,$d8,$d8,$d8,$d8

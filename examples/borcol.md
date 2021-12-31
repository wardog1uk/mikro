# Border Colour

Checks the raster position to flash the border with a solid colour.

## Code

    10 borcol=$d020
    20 raster=$d012
    30 getin=$ffe4
    99 !
    100 *=$c000
    110 loop lda raster
    120 bne loop
    130 lda raster-1
    140 and #%10000000
    150 bne loop
    160 inc borcol
    170 jsr getin
    180 beq loop
    190 rts

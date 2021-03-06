
# 10 PRINT

Display a randomly generated maze pattern. Run `sys 4096` to start and press `Run Stop+Restore` to break (`Escape+Page-up` in Vice).

## Code

    10 *=$1000
    100 lda #$80
    110 sta $d40f
    120 sta $d412
    130 loop lda $d41b
    140 and #$01
    150 adc #$6d
    160 jsr $ffd2
    170 bne loop

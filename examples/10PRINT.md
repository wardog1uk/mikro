# 10 PRINT

Display a randomly generated maze pattern. Run `sys 4096` to start and press `Run Stop+Restore` to break back to basic (`Escape+Page-up` in Vice).


## Credits

Taken from the book *10 PRINT CHR$(205.5+RND(1)); : GOTO 10*, page 234. [(Website)](https://10print.org/)


## Code

    10 *=$1000
    100 lda #$80
    110 sta $d40f
    120 sta $d412
    200 loop lda $d41b
    210 and #$01
    220 adc #$6d
    230 jsr $ffd2
    240 bne loop

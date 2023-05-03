# Mikro Assembler Pseudo Opcodes

Here are the pseudo opcodes that can be used in Mikro Assembler:

 - [BYT](#byt)
 - [END](#end)
 - [LNK](#lnk)
 - [OFF](#off)
 - [OUT](#out)
 - [TXT](#txt)
 - [WOR](#wor)
 - [\*](#asterisk)


## BYT

The `BYT` opcode is used to store a byte value in memory. It takes one or more comma-separated values as its argument, each representing a byte to be stored in memory.

Example:
```
100 BYT $01,2,'A,"BCD"
```

This will store the values $01, $02, $41, $42, $43 and $44 in memory at the current location.


## END

The `END` opcode marks the end of the assembly file. Any code afterwards will not be assembled.

Example:
```
100 END
```


## LNK

The `LNK` opcode is used to link multiple Mikro Assembler source files together. This allows the assembler to handle longer programs by breaking them up into smaller, more manageable files. The syntax is similar to the `LOAD` command in BASIC.

Example:
```
500 LNK "PART TWO",8
```

You must use the `END` command in the last file to link the assembler back to the first one. The `END` command should include the name of the first file and its device number.
```
; PART ONE
...
500 LNK "PART TWO",8


; PART TWO
...
900 END "PART ONE",8
```


## OFF

The `OFF` opcode is used to stop the output from the `OUT` opcode.

Example:
```
10 OUT
...
200 OFF
```

This will stop assembly output from being displayed.


## OUT

The `OUT` pseudo-opcode is used to output the subsequent code with its assembled code to a specified device during assembly. If no device number is specified, the output will be displayed on the screen.

To specify the device number, use the value associated with the device according to the [C64-Wiki](https://www.c64-wiki.com/wiki/Device_number).

If the device is a printer that does not automatically perform a line feed, add 128 to the device number.

Example:
```
100 OUT 4
```

This will output the assembled code to device number 4, which is typically the first printer.


## TXT

The `TXT` opcode is used to store a string of characters in memory.

Example:
```
100 TXT "HELLO, WORLD!"
```

This will store the ASCII values of the string "HELLO, WORLD!" in memory.


## WOR

The `WOR` opcode is used to store a 16-bit word in memory, low byte first. It takes one or more comma-separated values as its argument, each representing a word to be stored in memory.

Example:
```
100 WOR $1234, $5678
```

This will store the values `$1234` and `$5678` in memory as `$34 $12 $78 $56`.


## \*\(asterisk\)

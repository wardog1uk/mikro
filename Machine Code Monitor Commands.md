# Mikro Assembler Machine Code Monitor

To enter the machine code monitor type `TIM` at the basic prompt.

![TIM](images/basic/tim.png)


## D (Disassemble)

### Command
* `D <start address> <end address>`

### Description
The `D` command is used to disassemble machine code instructions. It allows you to view the assembly instructions corresponding to a range of memory addresses.

To use this command, provide the start and end addresses of the memory range you want to disassemble. For example, `D C000 C100` would disassemble the machine code instructions between memory addresses C000 and C100.


## G (Go execute)


## H (Hunt)

### Command
* `H <start address> <end address> <byte> [<byte>]...`

### Description
The `H` command is used to search for specific bytes in memory. It lists all addresses in the given range that contain the specified byte pattern.

To use this command, provide the start and end addresses of the memory range to search within, followed by the byte or bytes you want to find. For example, `H C000 D000 BB` would search for occurrences of the byte `BB` in the memory range between addresses `C000` and `D000`.

You can also search for multiple bytes by providing additional bytes separated by spaces. For example, `H C000 D000 12 34 AB` would search for occurrences of the byte pattern `12 34 AB` in the specified memory range.


## L (Load)


## M (Memory display)

### Command
* `M <start address> <end address>`

### Description
The M command displays the contents of memory, allowing you to view and edit the values stored at specific addresses. You can overwrite values and press return on the line to save the changes.

To use this command, provide the start and end addresses of the memory range you want to display. For example, `M C000 C100` would display the memory contents between addresses C000 and C100.


## R (Register display)

### Command
* `R`

### Description
The `R` command displays the values of the CPU registers, allowing you to view and edit their current state

To use this command, simply enter `R` and the register values will be displayed on the screen. You can overwrite a value and press return to save the changes.


## S (Save)

## T (Transfer)


## X (Exit to Basic)

### Command
* `X`

### Description
The `X` command is used to exit the machine code monitor and return to the BASIC prompt.

To use this command, simply enter `X`.
